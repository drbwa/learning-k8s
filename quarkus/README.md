# Brief evaluation of quarkus

## The good

* Promises lower memory usage and faster startup times. This
  [comparison](https://www.baeldung.com/spring-boot-vs-quarkus) shows that
  quarkus blows Spring out of the water in terms build time, startup time,
  artefact size, etc. The picture is more nuanced when it comes to memory usage
  and response times. Advantange shrinks if using OpenJDK instead of GraalVM.
* Integrates well with Kubernetes and OpenShift, which can be an advantage  (e.g., access ConfigMap and Secrets directly from K8s API server,  can generate Kubernetes and OpenShift YAML files for you).
* Has a live coding (hot reload) feature, which is really nice. 
* Reuses standard libraries (e.g., JAX-RS implemented by RESTeasy and Vert.x, Hibernate, JSON-P). 
* Embedded web server.
* Feature-rich and new extensions are added regularly.

## The bad

* New kid on the block. Fewer resources, including community resources,
  available compared with Spring and Spring Boot. Higher risk of getting stuck.

## Alternatives

* Spring Boot
* Micronaut
* Vert.X
* Microprofile
* Dropwizard