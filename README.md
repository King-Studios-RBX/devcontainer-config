# devcontainer-config

Shared [Dev Container](https://containers.dev/) configuration for King-Studios-RBX module repos. Provides a consistent, reproducible development environment with Bun, Rokit, roblox-ts tooling, and all required VS Code extensions.

## Repos Using This Config

| Repository | Description |
|---|---|
| [Interface](https://github.com/King-Studios-RBX/Anime-Reborn-Interface) | UI layer |
| [Gameplay-Core](https://github.com/King-Studios-RBX/Anime-Reborn-Gameplay-Core) | Core gameplay logic |
| [Lobby](https://github.com/King-Studios-RBX/Anime-Reborn-Lobby) | Lobby systems |
| [Common](https://github.com/King-Studios-RBX/Anime-Reborn-Common) | Shared utilities and types |
| [Configuration](https://github.com/King-Studios-RBX/Anime-Reborn-Configuration) | Game configuration data |
| [Assets](https://github.com/King-Studios-RBX/Anime-Reborn-Assets) | Asset pipeline |

> **Note:** The main [Anime-Reborn](https://github.com/King-Studios-RBX/Anime-Reborn) repo does **not** use this config.

## What's Included

```
├── docker/Dockerfile        # Base image — oven/bun:debian with system packages
├── devcontainer.json        # VS Code settings, extensions, post-create setup
├── .env.example             # Template for required environment variables
└── .github/workflows/       # CI validation
```

## Adding to a New Repo

1. Copy the `.devcontainer/` folder structure into your repo:

   ```bash
   mkdir -p .devcontainer
   cp docker/Dockerfile .devcontainer/Dockerfile
   cp devcontainer.json .devcontainer/devcontainer.json
   cp .env.example .env.example
   ```

2. Update the `"name"` field in `.devcontainer/devcontainer.json` to match your project (e.g., `"Lobby Development"`).

3. Commit the `.devcontainer/` folder and `.env.example` to your repo.

## Developer Setup

1. **Create a GitHub PAT** with the `read:packages` scope:
   [https://github.com/settings/tokens](https://github.com/settings/tokens) → Generate new token (classic)

2. **Copy the environment template:**

   ```bash
   cp .env.example .env
   ```

3. **Fill in your token** in `.env`:

   ```bash
   export NODE_AUTH_TOKEN="ghp_your_token_here"
   ```

4. **Open the repo in VS Code** and run the command:
   `Dev Containers: Reopen in Container`

The container will automatically install Rokit tools and run `bun install` using your token for `@king-studios-rbx` package authentication.

### Authentication Note

Package authentication is handled via **`bunfig.toml`**, not `.npmrc`. The `NODE_AUTH_TOKEN` environment variable is read by Bun's config to authenticate against GitHub Packages. No `.npmrc` file is needed.

## Included Extensions

| Extension | Purpose |
|---|---|
| `oven.bun-vscode` | Bun runtime support |
| `biomejs.biome` | Formatter & linter |
| `roblox-ts.vscode-roblox-ts` | roblox-ts language support |
| `flamework.flamework-vscode` | Flamework framework support |
| `johnnymorganz.luau-lsp` | Luau language server |
| `johnnymorganz.stylua` | Lua/Luau formatter |
| `kampfkarren.selene-vscode` | Selene linter |
| `streetsidesoftware.code-spell-checker` | Spell checking |
| `EditorConfig.EditorConfig` | EditorConfig support |
| `codecov.codecov` | Codecov YAML validation |
| `eamodio.gitlens` | Git history & blame |
| `github.vscode-github-actions` | GitHub Actions support |

## License

[MIT](LICENSE) © King-Studios-RBX
