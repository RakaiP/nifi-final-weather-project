# NiFi Weather Pipeline: Flow Explanation & Progress

## Flow Explanation

This NiFi flow implements a real-time weather data ingestion pipeline using both simulated and live data. The main steps are:

1. **GetFile (Simulated Real-Time):**  
   Reads historical weather data CSV files from the input directory, simulating real-time ingestion by replaying the data as if it were arriving live.

2. **SplitText:**  
   Splits each CSV file into individual records (one line per FlowFile).

3. **ControlRate:**  
   Controls the rate at which records are released, allowing simulation of real-time streaming (e.g., 1 record per second).

4. **Process Group (InvokeHTTP):**  
   Sends each record to a downstream process group, which can include further transformation or an InvokeHTTP processor for integration/testing.

5. **ReplaceText / UpdateAttribute:**  
   Formats and enriches the data as needed (e.g., reformatting timestamps, extracting fields).

6. **PutFile:**  
   Writes the resulting CSV files to the output directory.

## Project Progress

- **Repository Structure:**  
  - Docker Compose and environment files are set up.
  - NiFi flow templates (`bigdataweather.xml`, `Data.json`) are created and placed in the correct directory.
  - Input data files (`meteo1.csv`, `meteo2.csv`, `d.csv`) are available in the input directory.
  - Output directory is mapped and working.

- **Dockerized NiFi:**  
  - NiFi runs in a Docker container with persistent storage and mapped flow/data/output directories.
  - Access to NiFi UI is available at [https://localhost:8443/nifi](https://localhost:8443/nifi).

- **Flow Upload & Configuration:**  
  - The flow template can be uploaded via the NiFi UI.
  - Processors are configured for both simulated real-time (historical CSV) and live API data.
  - Data is successfully ingested, processed, and written to the output directory.

- **Documentation:**  
  - Setup instructions and report templates are available in the `docs` folder.
  - Screenshots and output samples can be added as progress continues.

---

## Next Steps

- [ ] **Enhance Data Transformation:**  
  Ensure all important columns are extracted and formatted in the output (e.g., using UpdateRecord or ExtractText for CSV fields).

- [ ] **Automate Output Validation:**  
  Add checks or sample scripts to validate the correctness of the output CSV files.

- [ ] **Integrate/Document InvokeHTTP Testing:**  
  If using InvokeHTTP for integration or testing, document the endpoint and results, and ensure local endpoints are accessible from the NiFi container.

- [ ] **Add More Data Sources (Optional):**  
  Simulate multiple data streams by adding more input files or increasing the ControlRate.

- [ ] **Collect Screenshots and Output Samples:**  
  For the final report, capture screenshots of the NiFi flow and sample output files.

- [ ] **Complete Final Report:**  
  Fill in the report template with flow diagrams, explanations, and performance notes.

---

**Summary:**  
You have successfully set up a simulated real-time weather data pipeline using historical CSV data in NiFi. The next steps focus on refining data transformation, validating outputs, documenting integration, and preparing final deliverables.