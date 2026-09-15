# Architecture

## System Architecture

The Mission Readiness & Predictive Maintenance Copilot combines device knowledge, source-code understanding, sensor data, machine-learning-based health prediction, and maintenance intelligence.

```mermaid
graph TD
    A[Engineer / Browser] -->|HTTP| B[Frontend - HTML5 CSS3]
    B -->|REST API| C[Backend - FastAPI]

    C --> D[Device Files & Source Code]
    D -->|Understanding| E[IBM Bob AI]

    C --> F[Sensor Data]
    F --> G[ML Health Prediction]

    E --> H[Health & Maintenance Analysis]
    G --> H

    H --> I[Maintenance Alerts]
    I --> J[Engineer Decision]

    C --> K[PostgreSQL]

    L[Arduino / Physical Asset] -->|Sensor Data| F

    C --> M[Docker Container]
    M --> C
````

## Components

| Component           | Technology          | Responsibility                                                                    |
| ------------------- | ------------------- | --------------------------------------------------------------------------------- |
| Frontend            | HTML5, CSS3         | Dashboard UI, asset information, health results and maintenance alerts            |
| Application Runtime | Node.js             | Supports the application/frontend environment                                     |
| Backend API         | Python, FastAPI     | API handling, business logic, data processing and orchestration                   |
| AI                  | IBM Bob AI          | Understanding device files and source code and assisting system analysis          |
| Machine Learning    | Python ML libraries | Health prediction and condition analysis using sensor/system data                 |
| Database            | PostgreSQL          | Storing application-related data and analysis information                         |
| Physical Asset      | Arduino + Sensors   | Providing real-world operational and sensor data                                  |
| Containerization    | Docker              | Containerizing the Python backend, FastAPI, ML libraries and project dependencies |

## Data Flow

The system combines static knowledge about the electronic device with its operational condition.

1. Device-related files and source code are provided to the system.
2. IBM Bob AI assists in understanding the files and source code.
3. Sensor data provides information about the current physical/operational condition of the asset.
4. The FastAPI backend receives and coordinates the required data and processing.
5. Machine-learning components analyze sensor/system information for health prediction.
6. AI and ML outputs are combined to support health and maintenance analysis.
7. The system generates maintenance alerts and relevant insights.
8. The engineer reviews the available information and makes the final maintenance decision.
9. PostgreSQL is used for required application and analysis data storage.

## Security Considerations

The prototype follows basic security practices appropriate for a hackathon environment.

* Sensitive configuration values should be stored using environment variables.
* API keys and credentials should not be committed to the Git repository.
* `.env` files containing secrets should remain local and should be excluded through `.gitignore`.
* Database credentials should be provided through environment configuration rather than hard-coded in source code.
* Access to physical hardware and sensor interfaces should be limited to the required local environment.

## Scalability Notes

The current implementation is a local hackathon prototype. The architecture can be extended for larger-scale industrial deployment.

* FastAPI can be deployed as a scalable backend service.
* Backend services can be containerized and replicated using Docker-based infrastructure.
* PostgreSQL can be expanded for larger volumes of asset, sensor, and maintenance data.
* Sensor data ingestion can be extended to support multiple assets simultaneously.
* AI and ML processing can be separated into dedicated services as workload increases.
* Additional asset types, data sources, and maintenance workflows can be integrated without changing the core **Understand → Monitor → Predict → Alert → Decide** concept.

```
