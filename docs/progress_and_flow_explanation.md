# NiFi Weather Pipeline: Flow Explanation & Progress

## Flow Explanation

This NiFi flow implements a real-time weather data ingestion pipeline using the OpenWeatherMap API. The main steps are:

1. **InvokeHTTP (Fetch Weather):**  
   Periodically calls the OpenWeatherMap API to retrieve current weather data for a specified city (e.g., London).

2. **EvaluateJsonPath:**  
   Extracts relevant fields from the JSON response, such as temperature (`temp`), wind speed (`wind_speed`), and timestamp (`dt`).

3. **UpdateAttribute:**  
   Converts the UNIX timestamp to a human-readable date format using NiFi Expression Language.

4. **ReplaceText:**  
   Formats the extracted data as a CSV row.

5. **MergeContent:**  
   Batches multiple rows into a single CSV file.

6. **PutFile:**  
   Writes the resulting CSV file to the output directory.

## Project Progress

- **Repository Structure:**  
  - Docker Compose and environment files are set up.
  - NiFi flow XML (`bigdataweather.xml`) is created and placed in the correct directory.
  - Documentation and report templates are prepared.

- **Dockerized NiFi:**  
  - NiFi runs in a Docker container with persistent storage and mapped flow directory.
  - Access to NiFi UI is available at [https://localhost:8443/nifi](https://localhost:8443/nifi).

- **Flow Upload & Configuration:**  
  - The flow template can be uploaded via the NiFi UI.
  - Processors are configured for the OpenWeatherMap API and CSV output.

- **Documentation:**  
  - Setup instructions and report templates are available in the `docs` folder.
  - Screenshots and output samples can be added as progress continues.

---

**Next Steps:**  
- Test the pipeline end-to-end.
- Collect output files and screenshots.
- Complete the final report and performance analysis.