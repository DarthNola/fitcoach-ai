# API Guidelines

- Use NestJS and TypeScript, following the project architecture in `../../docs/architecture/architecture.md`.
- Keep business logic in appropriate modules and explain unfamiliar NestJS concepts.
- Before implementing a feature, inspect the existing app and agree on a plan.
- Validate incoming data, enforce authentication and authorization, and keep secrets out of source control.
- Treat AI output as untrusted and require user approval for proposed workout schedule changes and food estimates.
- Verify changes with the relevant checks when requested; report only checks that were run.
