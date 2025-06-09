# Setup Instructions for NiFi Weather Pipeline

## Prerequisites
- Ensure you have Docker and Docker Compose installed on your machine.
- Familiarity with command line interface.

## Step 1: Clone the Repository
Clone the project repository to your local machine:
```bash
git clone <repository-url>
cd nifi-weather-pipeline
```

## Step 2: Configure Environment Variables
Create a `.env` file in the root directory if it doesn't exist. Add the following environment variables:
```
NIFI_USERNAME=admin
NIFI_PASSWORD=SecurePass123!
```

## Step 3: Start NiFi using Docker Compose
Navigate to the `docker` directory and run the following command to start the NiFi instance:
```bash
cd docker
docker-compose up -d
```

## Step 4: Access the NiFi UI
Once the NiFi container is running, access the NiFi UI by opening your web browser and navigating to:
```
https://localhost:8443/nifi
```
You may need to accept a security warning. Log in using the credentials specified in the `.env` file.

## Step 5: Import the NiFi Flow
1. In the NiFi UI, click on the "Operate" palette.
2. Click on the "Template" icon and select "Upload Template".
3. Choose the `bigdataweather.xml` file located in the `nifi/flows` directory.
4. Drag the imported template onto the canvas to visualize the flow.

## Step 6: Configure Processors
- Double-click on each processor to configure them according to your requirements.
- Ensure the `InvokeHTTP` processor is set with the correct OpenWeatherMap API URL.

## Step 7: Start the Flow
- Start each processor by right-clicking on it and selecting "Start".
- Monitor the flow and check the output directory for generated CSV files.

## Step 8: Stop the NiFi Instance
To stop the NiFi instance, run the following command in the `docker` directory:
```bash
docker-compose down
```

## Additional Notes
- For troubleshooting, check the logs of the NiFi container using:
```bash
docker logs nifi
```
- Ensure that your API key for OpenWeatherMap is valid and has the necessary permissions.

## Conclusion
You have successfully set up the NiFi Weather Pipeline. Follow the above steps to run the pipeline and monitor the data ingestion process.