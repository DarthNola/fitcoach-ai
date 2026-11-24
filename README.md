# FitCoach AI

Personal fitness and nutrition assistant. See the [architecture proposal](docs/architecture/architecture.md) and [mentor guidelines](AGENTS.md).

## Development environment

The Node.js and PNPM toolchain runs in Docker; it does not need to be installed on the host.

Build and start the development container:

```sh
docker compose up -d --build dev
```

Open a shell in the container:

```sh
docker compose exec dev bash
```

Check the tool versions inside the container:

```sh
node --version
pnpm --version
```

The project directory is mounted at `/workspace`. The container runs as the non-root `node` user, has a read-only root filesystem, and exposes the future Vue and NestJS development ports on localhost. It does not receive the host Docker socket.

Stop the container from the project directory with:

```sh
docker compose down
```

See [Docker learning notes](docs/learning/docker.md) for how this setup works.
