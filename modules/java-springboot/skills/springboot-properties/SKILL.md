# Spring Boot Properties

Follow these rules whenever declaring, binding, validating, or consuming externalized configuration in a Spring Boot application.

## Typed Configuration Binding

- Bind externalized configuration through `@ConfigurationProperties` types instead of `@Value`, `Environment.getProperty(...)`, `System.getenv(...)`, or `System.getProperty(...)` inside application components.
- Group related settings under a cohesive, domain-oriented prefix in lowercase `kebab-case` rather than scattering isolated keys across services.
- Inject the typed properties object into consumers via constructor injection so components remain trivially instantiable in plain unit tests without starting a Spring context.
- Register `@ConfigurationProperties` types via `@EnableConfigurationProperties` or `@ConfigurationPropertiesScan` on a dedicated `@Configuration` class rather than on the main application class.

## Immutability and Value Types

- Prefer Java `record` types for `@ConfigurationProperties` using constructor binding; when a class is necessary, declare all fields `private final` with a single constructor and no setters.
- Define explicit defaults in the canonical constructor or with `@DefaultValue` instead of duplicating fallback logic in consuming services.
- Use rich value types such as `Duration`, `DataSize`, `URI`, or domain types instead of raw primitives with implicit units.

## Fail-Fast Validation

- Annotate `@ConfigurationProperties` types with `@Validated` and apply Jakarta Bean Validation constraints (`@NotNull`, `@NotBlank`, `@NotEmpty`, `@Positive`, `@PositiveOrZero`, `@Pattern`, `@Min`, `@Max`) so invalid configuration fails immediately at startup.
- Annotate nested property objects with `@Valid` for recursive validation and validate collection or map elements explicitly (`List<@NotBlank String>`, `Map<@NotNull String, @Valid NestedProperties>`) rather than validating only the outer container.
- Enforce cross-field invariants with validation constraints (such as `@AssertTrue`) or canonical constructor checks that produce clear startup failure messages.
