# Voiture App Backend (Spring Boot) with monitoring using Actuator-prometheus-grafana

This is the back-end part of the **Voiture App**, built with **Spring Boot** and **Java 21**, and Dockerized for easy deployment. The project is integrated with **Spring Boot Actuator**, **Prometheus**, and **Grafana** for application monitoring and performance visualization. This guide explains how to set up, build, push, run the back-end, and monitor it with these tools.

## Prerequisites

- **JDK 21** installed. You can download it from [here](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html).
- **Docker** installed. You can get Docker [here](https://www.docker.com/get-started).
- **Maven** installed. Find installation instructions [here](https://maven.apache.org/install.html).
- A **GitHub account** for cloning the repository and pushing updates.
  
## Setup and Build Instructions

### 1. Clone the Repository

   First, you need to clone this repository from GitHub and navigate into the project directory:
   
   - git clone https://github.com/ChakraHs/SpringDataRest-React.git
   - cd SpringDataRest-React

### 2. Build the Docker Image

The back-end image is built using **Maven** and the **Spring Boot** plugin. To create the Docker image, run the following command:

- mvn clean package -Pbuild-image

This command will generate a Docker image for the back-end.

### 3. Run Docker Compose

Run the following command to start the the project services using Docker Compose:

- docker compose up -d

This will start all services defined in your `docker-compose.yml`. including backend with db (postgres), frontend, Prometheus for metrics scraping and Grafana for visualizing these metrics

## Monitoring with Actuator, Prometheus, and Grafana

### 1. Spring Boot Actuator

Spring Boot Actuator provides several out-of-the-box endpoints that expose useful metrics about your application. These metrics are now accessible and scraped by Prometheus. Common endpoints include:

- `/actuator/health` – for health checks.
- `/actuator/prometheus` – Prometheus metrics.

### 2. Accessing Prometheus

Once Docker Compose is running, Prometheus will be available at the following URL:

- **Prometheus URL**: [http://localhost:9090](http://localhost:9090)

You can explore the metrics being scraped by Prometheus by visiting this URL and querying metrics such as:

- `http_server_requests_seconds_count`: HTTP request counts.
- `jvm_memory_used_bytes`: Memory usage.
- `process_cpu_usage`: CPU usage.

### 3. Accessing Grafana

Grafana will also be available via Docker Compose. To access Grafana, visit:

- **Grafana URL**: [http://localhost:3000](http://localhost:3001)

### 4. Setting Up Dashboards in Grafana

#### Login to Grafana

The default login credentials are:

- **Username**: `admin`
- **Password**: `admin` (you will be prompted to change it on first login).

#### Add Prometheus as a Data Source

1. Go to **Configuration** -> **Data Sources** -> **Add data source**.
2. Select **Prometheus** and set the URL to `http://prometheus:9090` (if running through Docker).

#### Import a Dashboard

1. Go to **Create** -> **Import**.
2. You can use pre-built Grafana dashboard templates, such as the **Spring Boot Actuator Metrics** dashboard available in the Grafana library, or create custom ones.

#### Visualize Metrics

Create panels in Grafana to visualize metrics like CPU usage, memory consumption, HTTP request performance, etc. Common metrics for Spring Boot include:

- `jvm_memory_used_bytes`: Memory usage.
- `http_server_requests_seconds_count`: HTTP request counts.
- `process_cpu_usage`: CPU usage.

### 5. Customize Monitoring

You can extend monitoring by adding custom metrics using the `@Timed`, `@Gauge`, or `@Counted` annotations in your Spring Boot application. These custom metrics will automatically be available in Prometheus and visualized in Grafana.

## Accessing the Application

Once the services are running, you can access the App at:

- **Application URL**: [http://localhost:3000](http://localhost:3000)
- **Prometheus URL**: [http://localhost:9090](http://localhost:9090)
- **Grafana URL**: [http://localhost:3001](http://localhost:3001)





