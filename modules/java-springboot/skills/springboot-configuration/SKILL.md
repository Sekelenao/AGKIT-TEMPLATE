# Spring Boot Configuration

Follow these rules when structuring the application bootstrap class, `@Configuration` classes, `@Enable*` capabilities, and `@Bean` definitions in a Spring Boot application.

## Main Application Class

- Annotate the main application class solely with `@SpringBootApplication`.
- Never place `@Enable*` annotations (such as `@EnableJpaAuditing`, `@EnableScheduling`, `@EnableAsync`, `@EnableCaching`, `@EnableFeignClients`, `@EnableConfigurationProperties`, or `@MapperScan`), `@Import`, `@ComponentScan`, or `@Bean` methods on the main application class.
- Keep the main class free of extra configuration so sliced tests (`@WebMvcTest`, `@DataJpaTest`, `@JsonTest`, etc.), which bootstrap from the main class, do not pull in unrelated infrastructure or force artificial bean mocking.

## Modular Configuration Classes

- Isolate each cross-cutting capability and its `@Enable*` annotation in a dedicated, cohesive `@Configuration` class.
- Set `proxyBeanMethods = false` on `@Configuration` classes whose `@Bean` methods do not invoke one another directly.
- Guard background or environment-sensitive capabilities (such as scheduling, async execution, or messaging listeners) with `@ConditionalOnProperty` or explicit conditions so tests and local environments can disable them cleanly.
- Keep `@Bean` factory methods focused on wiring and infrastructure instantiation; do not embed business logic or blocking I/O inside configuration classes.
