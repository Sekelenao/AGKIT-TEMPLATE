## Spring Boot

This project uses Spring Boot.
Prefer Spring Boot auto-configuration, starters, and built-in abstractions (such as SSL Bundles for TLS/certificates, `RestClient` or HTTP Interfaces, Actuator, and Micrometer) over hand-rolled infrastructure plumbing.
When wiring standard infrastructure (TLS, HTTP clients, serialization, health checks, observability, retries, or persistence) starts requiring dozens of lines of manual boilerplate, stop and check for a native Spring Boot feature or property first.
