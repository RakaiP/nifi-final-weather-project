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

## NiFi vs Kafka: Real-Time Data Ingestion Comparison

### Flow Explanation

- **NiFi Flow:**  
  Our NiFi pipeline fetches weather data from the OpenWeatherMap API at a configurable interval (e.g., every 2 minutes), processes the JSON, and writes the results to CSV files. NiFi provides a visual interface for building ETL pipelines, making it easy to monitor and adjust the flow.

- **Kafka Flow (Conceptual):**  
  In a Kafka-based pipeline, a producer application fetches weather data and publishes it to a Kafka topic in real time. Consumers (e.g., Spark Streaming, Flink, or custom apps) subscribe to the topic and process the data, possibly writing to a database or file system. Kafka is optimized for high-throughput, low-latency streaming and supports message replay and strong ordering.

### Real-Time Comparison

- **NiFi** is suitable for near real-time ETL and integration tasks, with easy setup and strong transformation capabilities. However, its latency is typically higher than Kafka, and it is not designed for ultra-low-latency streaming.
- **Kafka** is designed for high-throughput, low-latency, distributed streaming. It excels at handling massive data streams with minimal delay and supports message replay and partitioned ordering.

### When to Use Each

- **Use NiFi** when you need easy integration, transformation, and routing of data from many sources, and when sub-second latency is not critical.
- **Use Kafka** when you need to handle very high data rates, require strong ordering, replay, and ultra-low latency.

### Project Progress

- [x] NiFi pipeline implemented and tested for weather data ingestion.
- [ ] Kafka pipeline (conceptual or implemented) for comparison.
- [x] Documentation updated with flow diagrams and screenshots.
- [ ] Performance metrics collected for both approaches.

---

**Conclusion:**  
For most weather data use cases, NiFi provides sufficient real-time capabilities with much easier setup and management. Kafka is better suited for scenarios requiring massive scale and ultra-low latency.