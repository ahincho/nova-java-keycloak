# nova-java-keycloak

> Nova Keycloak core library: pure-Java (no framework) token and user profile
> management for Keycloak-issued JWTs.

[![Nova Platform](https://img.shields.io/badge/Nova-Platform-00add8)](https://github.com/ahincho/nova-platform)
[![Java](https://img.shields.io/badge/Java-25-b07219)](https://openjdk.org/projects/jdk/25/)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](LICENSE)

## What it is

A **pure-Java** library (no Spring, no Quarkus, no framework dependency) that
exposes a small, framework-agnostic facade to:

- parse and validate Keycloak-issued JWTs (signed by the realm's public key),
- extract the **public payload claims** into a typed `KeycloakProfile`
  (`sub`, `preferred_username`, `email`, `email_verified`, `name`, `realm_access.roles`,
  `resource_access.<client>.roles`, etc.),
- resolve the current request's principal (bearer token -> profile) without
  coupling to any HTTP framework.

It is consumed by `nova-java-keycloak-quarkus-extension`, which auto-wires it
into a Quarkus application.

## When to use this directly

If you are integrating Keycloak JWT handling in a **non-Quarkus** Java app
(plain JEE, Micronaut, Spring without `spring-boot-starter-oauth2-resource-server`,
vanilla `main(...)`, etc.), depend on this library and call the facade directly.

For Quarkus apps prefer the extension:

- `nova-java-keycloak-quarkus-extension`

## Status

> **Work in progress.** Package coordinates, API surface and module layout
> will change. Track issues for progress.

## Modules (planned)

| Artifact                         | Purpose                                              |
| -------------------------------- | ---------------------------------------------------- |
| `nova-java-keycloak`             | Pure-Java facade (this repo, single module)          |
| `nova-java-keycloak-quarkus-extension` | Quarkus build-time extension + CDI auto-wiring |

## Build

```bash
./mvnw clean verify
```

Requires **JDK 25** and **Maven 3.9+**.

## License

Apache License 2.0. See [LICENSE](LICENSE).
