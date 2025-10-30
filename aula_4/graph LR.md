```mermaid
graph LR
    A[Eventos do Sistema] -->|Publica| B[RabbitMQ]
    B -->|Consome| C[Email Service]
    B -->|Consome| D[Push Notification Service]
    B -->|Consome| E[SMS Service]
```