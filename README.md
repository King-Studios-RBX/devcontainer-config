# devcontainer-config

Shared devcontainer configuration for all Anime Reborn repos in the King-Studios-RBX organization.

## What's included

- **docker/Dockerfile** — Base image (Bun on Debian) with common system packages
- **devcontainer.json** — VS Code settings, extensions, and post-create setup (Rokit, Bun install, etc.)
- **.env.example** — Template for environment variables (NODE_AUTH_TOKEN for GitHub Packages)

## Usage

### Option 1: Copy (recommended)

Copy the `.devcontainer/` folder contents into your repo:

```bash
# From your repo root
mkdir -p .devcontainer
cp /path/to/devcontainer-config/docker/Dockerfile .devcontainer/Dockerfile
cp /path/to/devcontainer-config/devcontainer.json .devcontainer/devcontainer.json
```

Then customize the `"name"` field in `devcontainer.json` to match your repo (e.g., `"Anime Reborn Lobby Development"`).

### Option 2: Git submodule

```bash
git submodule add https://github.com/King-Studios-RBX/devcontainer-config.git .devcontainer-shared
```

Then create a `.devcontainer/devcontainer.json` that references the shared Dockerfile.

## Environment Setup

1. Copy `.env.example` to `.env` in your repo root
2. Fill in `NODE_AUTH_TOKEN` with a GitHub PAT that has `read:packages` scope
3. The devcontainer's `postCreateCommand` will automatically source `.env` and run `bun install`

## Customization

Each repo should customize at minimum:
- `"name"` in `devcontainer.json` — set to your project name
- Any repo-specific VS Code settings or extensions can be added on top

## Repos using this config

- [Anime-Reborn](https://github.com/King-Studios-RBX/Anime-Reborn)
- [Anime-Reborn-Interface](https://github.com/King-Studios-RBX/Anime-Reborn-Interface)
- [Anime-Reborn-Gameplay-Core](https://github.com/King-Studios-RBX/Anime-Reborn-Gameplay-Core)
- [Anime-Reborn-Lobby](https://github.com/King-Studios-RBX/Anime-Reborn-Lobby)
- [Anime-Reborn-Common](https://github.com/King-Studios-RBX/Anime-Reborn-Common)
- [Anime-Reborn-Configuration](https://github.com/King-Studios-RBX/Anime-Reborn-Configuration)
- [Anime-Reborn-Assets](https://github.com/King-Studios-RBX/Anime-Reborn-Assets)
