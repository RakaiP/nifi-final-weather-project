# NiFi Weather Pipeline

## Overview
This project implements a real-time weather data pipeline using Apache NiFi. It ingests weather data from both live API streams and local file simulations, cleans and deduplicates the data, and outputs well-formatted CSV/JSON files ready for analysis or dashboarding.

---

## Project Structure

```
nifi-weather-pipeline/
├── docker/
│   ├── docker-compose.yml         # Docker Compose config for NiFi
│   └── nifi/
│       ├── data/
│       │   └── input/             # Place your input CSV files here (e.g., meteo1.csv)
│       └── flows/
│           ├── Flow_Final.json    # NiFi flow definition (import this in NiFi UI)
│           ├── Data.json          # (Optional) Other flow configs
│           └── duplicaterWORK.json# (Optional) Other flow configs
├── output/                        # Output directory for cleaned CSV/JSON files
├── docs/
│   ├── setup_instructions.md      # Step-by-step setup guide
│   ├── progress_and_flow_explanation.md # Flow and progress explanation
│   └── report_template.md         # Template for your project report
├── bigdataweather.xml             # NiFi flow template (XML, can be imported in NiFi)
├── .env                           # Environment variables for Docker/NiFi
└── README.md                      # This file
```

### Directory Explanations

- **docker/nifi/flows/**  
  Contains NiFi flow definitions (`Flow_Final.json`, etc.).  
  **Import these files into the NiFi UI** to set up your pipeline.

- **docker/nifi/data/input/**  
  Place your **input weather data files** (CSV) here.  
  Example: `meteo1.csv`, `meteo2.csv`, `meteo3.csv`.

- **output/**  
  The pipeline writes **cleaned, deduplicated output files** here (CSV or JSON).

- **docs/**  
  Documentation, setup instructions, and report templates.

---

## How to Build and Run

### 1. Prerequisites

- [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed.
- (Optional) [Git](https://git-scm.com/) for cloning the repository.

### 2. Clone the Repository

```bash
git clone <repository-url>
cd nifi-weather-pipeline
```

### 3. Prepare Input Data

- Place your weather CSV files in `docker/nifi/data/input/`.
- Example files: `meteo1.csv`, `meteo2.csv`, `meteo3.csv`.

### 4. Configure Environment Variables

- Check the `.env` file in the project root.  
  Default credentials are set for NiFi admin access.

### 5. Start NiFi with Docker Compose

```bash
cd docker
docker-compose up -d
```

- This will start NiFi and mount the necessary directories for flows, input data, and output.

### 6. Access the NiFi UI

- Open your browser and go to:  
  [https://localhost:8443/nifi](https://localhost:8443/nifi)
- Login with the credentials from `.env` (default: admin / SecurePass123!)

### 7. Import the NiFi Flow

- In the NiFi UI, go to the Operate palette.
- Click the **Upload Template** button.
- Import `bigdataweather.xml` (or use the JSON flow in `docker/nifi/flows/Flow_Final.json`).
- Drag the template onto the canvas.

### 8. Configure and Start the Flow

- Double-click processors to check or adjust settings (e.g., file paths, API keys).
- Start all processors.
- Monitor the flow and check the `output/` directory for results.

---

## How the Pipeline Works

- **Ingests** weather data from both local files and live API.
- **Splits** and **streams** data for real-time simulation.
- **Cleans** and **formats** timestamps and fields.
- **Deduplicates** records using a cache (MapCacheClientService).
- **Merges** records and writes output as CSV/JSON to the `output/` directory.

---

## Supporting Documentation

- **Flow_Final.json**: Complete NiFi pipeline setup (import in NiFi UI).
- **Sample Output Files**: See `output/` for cleaned CSV/JSON files.
- **Controller Services Used**:
  - JsonTreeReader and JsonRecordSetWriter for schema-based processing.
  - MapCacheClientService for real-time duplicate detection.

---

## Highlights

- Supports multiple data sources (real and simulated).
- Real-time processing, cleaning, and deduplication.
- Outputs are well-formatted and analysis-ready.
- Built using low-code, scalable architecture with Apache NiFi.

---

## Troubleshooting

- Check NiFi logs with:  
  `docker logs nifi`
- Ensure your input files are in the correct directory.
- For more help, see `docs/setup_instructions.md`.

---

## References

- [docs/setup_instructions.md](docs/setup_instructions.md)
- [docs/progress_and_flow_explanation.md](docs/progress_and_flow_explanation.md)
- [docs/report_template.md](docs/report_template.md)

---

**For further questions, see the documentation or contact the project maintainers.**
