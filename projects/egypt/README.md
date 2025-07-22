# Egypt Geocoding Project

This project provides geocoding services for Egypt using Pelias.

## Data Sources

- **OpenStreetMap**: Complete Egypt data from Geofabrik
- **GeoNames**: Egypt-specific place names and administrative divisions
- **Who's on First**: Administrative boundaries and place hierarchies for Egypt

## Configuration

The project is configured with:
- Focus point: Cairo (30.0444°N, 31.2357°E)
- Country code: EG (Egypt)
- Elasticsearch with optimized settings for Egypt data

## Usage

To run the Egypt geocoding service:

1. Navigate to this directory: `cd docker/projects/egypt`
2. Create a data directory: `mkdir ./data`
3. Set up the environment: 
   ```bash
   sed -i '/DATA_DIR/d' .env
   echo 'DATA_DIR=./data' >> .env
   ```
4. Run the complete setup:
   ```bash
   pelias compose pull
   pelias elastic start
   pelias elastic wait
   pelias elastic create
   pelias download all
   pelias prepare all
   pelias import all
   pelias compose up
   ```
5. Optionally run tests: `pelias test run`

## API Endpoints

Once running, the API will be available at:
- Main API: http://localhost:4000/v1/
- Placeholder service: http://localhost:4100/
- PIP service: http://localhost:4200/
- Interpolation service: http://localhost:4300/

## Data Import

The system will automatically download and import:
- Egypt OpenStreetMap data (164MB) - **Already downloaded**
- Egypt GeoNames data
- Egypt Who's on First administrative boundaries

Import time: Approximately 30-60 minutes depending on your system.

**Note**: The Egypt OSM data file (egypt-latest.osm.pbf) has already been downloaded to `data/openstreetmap/` directory. 