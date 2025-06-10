# Project Report: Real-Time Data Ingestion Pipeline with Apache NiFi

## Abstract
This report outlines the implementation of a real-time data ingestion pipeline using Apache NiFi. It details the setup process, the flow design, and the performance metrics observed during testing. Additionally, a comparison with Apache Kafka is provided to highlight the strengths of NiFi in handling transformation-heavy workloads.

## 1. Group Name
Rakai-Ken-Abhin

## 2. Overview
The project aims to create a robust real-time data ingestion pipeline that fetches weather data from the OpenWeatherMap API, processes it, and stores it in a CSV format. Apache NiFi is chosen for its ease of use, powerful data flow capabilities, and support for various data formats.

## 3. Flow Description
The NiFi flow consists of several processors that work together to achieve the desired data ingestion and transformation. The key processors include:

- **InvokeHTTP**: Fetches data from the OpenWeatherMap API.
- **EvaluateJsonPath**: Extracts relevant fields from the JSON response.
- **UpdateAttribute**: Converts timestamps and formats data.
- **ReplaceText**: Prepares the data for CSV output.
- **MergeContent**: Combines multiple records into a single CSV file.
- **PutFile**: Writes the final output to the specified directory.

## 4. Kafka Comparison
| Feature                | Apache NiFi                     | Apache Kafka                  |
|------------------------|----------------------------------|-------------------------------|
| Latency                | ~100–500 ms                     | ~10 ms                        |
| Throughput             | 10k–100k events/sec             | ≥1M events/sec                |
| Processing Model       | GUI-driven, ETL-focused         | Code-centric, streaming-centric|
| Learning Curve         | Low                              | High                          |
| Security               | TLS, RBAC                       | SSL/SASL, ACLs               |

## 5. Usage Instructions
To run the pipeline using Docker, follow these steps:

1. Pull the NiFi Docker image:
   ```
   docker pull apache/nifi:latest
   ```

2. Run the NiFi container with the following command:
   ```
   docker run --name nifi -p 8443:8443 \
   -e SINGLE_USER_CREDENTIALS_USERNAME=admin \
   -e SINGLE_USER_CREDENTIALS_PASSWORD=SecurePass123! \
   -d apache/nifi:latest
   ```

3. Access the NiFi UI by navigating to `https://localhost:8443/nifi` in your web browser. Accept any security warnings and log in with the provided credentials.

4. Import the NiFi flow from `nifi/flows/bigdataweather.xml` and start the processors to begin data ingestion.

5. Monitor the output in the `output` directory for generated CSV files.

## 6. Conclusion
This project successfully demonstrates the capabilities of Apache NiFi in building a real-time data ingestion pipeline. The ease of use and flexibility of NiFi make it an excellent choice for handling complex data transformations and integrations.

## Appendix
- Flow XML: [bigdataweather.xml](../nifi/flows/bigdataweather.xml)
- Screenshots: Refer to the `docs/screenshots` directory for visual documentation of the flow logic and data transformations.

## References
[Include any references or citations here]
