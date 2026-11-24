# Docker Learning Notes

## Core ideas

- An **image** is a packaged filesystem and configuration used to create containers.
- A **container** is an isolated process started from an image. It still shares the host kernel, so it is not a complete security boundary.
- A **Dockerfile** describes how to build an image.
- **Docker Compose** describes and runs related containers from a YAML file.
- A **bind mount** shares a host directory with a container. FitCoach mounts this project at `/workspace`, so processes in the container can read and change project files.
- A **named volume** stores container data separately from the project directory. FitCoach uses one for PNPM's package store.
- A **port mapping** forwards a host port to a container port. FitCoach binds development ports to `127.0.0.1`, making them available locally.

## FitCoach development container

`infrastructure/docker/Dockerfile.dev` uses the official Node 24 Debian slim image and installs PNPM 12.11.1. `docker-compose.yml` runs it as the non-root `node` user.

The container has a read-only root filesystem, drops Linux capabilities, enables `no-new-privileges`, and does not mount the Docker socket. The project mount remains writable because developers need to edit source files. The container has network access for package downloads.

Start it with `docker compose up -d --build dev`, then open a shell with `docker compose exec dev bash`. Stop it with `docker compose down`.

## Security limits

Containers reduce access when configured carefully, but they share the host kernel. A process in this development container can alter files under the mounted project directory and use the network. The mount includes ignored files such as `.env`, if present, so do not keep secrets in the project directory when running untrusted code. Never mount your home directory, SSH keys, cloud credentials, or the Docker socket into an untrusted container. Keep Docker and images updated, and do not treat container isolation as a substitute for dependency review or host security updates.
