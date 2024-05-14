## Quick view

0. Project has 3 main ms: accounts, loans, cards
1. eurekaserver (registry/discovery server): microservices regis without port number
2. configserver (load-profile): customize properties
3. gatewayserver (gateway): routing, metric, load balancer, security
4. message (event-streaming with kafka): 
   * Thead 1:
   - accounts-ms receive update-account-request 
   - accounts-ms send account-dto to message-ms
   - after accounts receive message from message-ms, it will update database
   * Thread 2:  
   - message-ms receive account-dto and response to client
   - message-ms send back to account-ms a message that process is complete
   * 2 Thread process independence, kafka hold events to make asynchronous
    
## Docker cmd
| "docker compose up" | To create and start containers based on given docker compose file | 

| "docker compose down" | To stop and remove containers |

## Main features
- Mapper: Model Mapper - http://modelmapper.org/
- Write docs: Open API - https://www.openapis.org/
- Build container: Google Jib - https://github.com/GoogleContainerTools/jib
- Build external container: Docker compose - https://docs.docker.com/compose/
- Build config server-client: Spring Cloud Config - https://spring.io/projects/spring-cloud-config
- Microservice API communication: Spring Cloud Netflix - https://spring.io/projects/spring-cloud-netflix
- Microservice API communication: Spring Cloud OpenFeign - https://spring.io/projects/spring-cloud-openfeign
- Fault tolerance: Resilience4j website - https://resilience4j.readme.io
- Build gateway: Spring Cloud Gateway - https://spring.io/projects/spring-cloud-gateway
- RateLimitter - https://stripe.com/blog/rate-limiters
- Tracing logs, metrics, check health: Grafana - https://grafana.com
- Get logs from MinIO: Grafana Loki - https://grafana.com/docs/loki/latest/getting-started/
- Exposes metrics data: Micrometer - https://micrometer.io
- Monitoring show metrics: Prometheus - https://prometheus.io/
- Monitoring include health,tracing, metrics: Grafana Dashboards - https://grafana.com/grafana/dashboards/
- Attach [service_name,correlationID,spanID] in log: OpenTelemetry - https://opentelemetry.io/
- OpenTelemetry automatic instrumentation - https://opentelemetry.io/docs/instrumentation/java/automatic/
- Give access token: Keycloak - https://www.keycloak.org/
- Docker compose file for Kafka - https://github.com/bitnami/containers/blob/main/bitnami/kafka/docker-compose.yml
