# Flinkboot Configuration

Follow these rules when declaring, loading, and validating YAML configurations in a Flinkboot application.

## Job Bootstrap and Loading

- Initialize the application with `Flinkboot.initialize(args)` and load validated YAML configuration via `boot.configuration(ConfigClass.class)`.
- Keep runtime environment settings (parallelism, checkpointing, state backend, restart strategy, local Web UI) declarative in YAML and create the `StreamExecutionEnvironment` via `boot.executionEnvironment(jobProperties)` rather than hardcoding them in Java.
- Use `boot.flag(...)` and `boot.parameter(...)` for CLI or environment overrides, and `Resource.of(...)` for unified resource loading.

## Configuration DTO Design

- Model YAML sections as immutable `Serializable` classes or records composing Flinkboot built-in property types (such as `JobProperties` and connector properties) where available.
- For class-based DTOs, declare all fields `private final` with a single `@JsonCreator` canonical constructor and `@JsonProperty` using `kebab-case` names on every parameter.
- Do not call `Objects.requireNonNull(...)` inside `@JsonCreator` constructors; allow Jackson to build the full object graph so Jakarta Bean Validation can report all missing or invalid properties together at startup.

## Fail-Fast Validation

- Annotate single-field constraints with Jakarta Bean Validation (`@NotNull`, `@NotBlank`, `@NotEmpty`, `@Positive`, `@PositiveOrZero`, `@Pattern`) and mark nested configuration objects with `@Valid` for recursive validation.
- Validate container elements explicitly (`List<@NotBlank String>`, `Map<@NotNull String, @NotNull String>`, `List<@NotNull @Valid NestedProperties>`) rather than validating only the outer collection.
- Implement `ValidatableProperties` for cross-field invariants instead of duplicating manual validation logic in constructors.
