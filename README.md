# Agent Kit

Production-ready AI agent development framework powered by the Claude Agent SDK. Agent Kit provides a complete frontend-to-backend solution for building, deploying, and scaling AI agent applications with built-in multi-channel access via WebSocket, Discord, and Telegram.

## Features

- **Claude Agent SDK integration** — streaming responses with unified session routing
- **Multi-channel access** — WebSocket (web UI), Discord, and Telegram out of the box
- **Multi-agent management** — create and configure multiple agents with independent workspaces
- **Real-time web UI** — Next.js frontend with WebSocket-based conversation streaming
- **FastAPI backend** — async Python backend with file-based workspace storage
- **Docker-ready** — one-command deployment with Docker Compose

## Prerequisites

- Python 3.11+
- Node.js 20+
- Docker & Docker Compose (for containerized deployment)
- An API key from [Anthropic](https://console.anthropic.com/) or [Bigmodel](https://open.bigmodel.cn/)

## Quick Start

### Docker (Recommended)

```bash
git clone https://github.com/Abdullah-0419/Agentic-kit.git
cd Agentic-kit

# Configure your API key
cp example.env .env
# Edit .env and set ANTHROPIC_AUTH_TOKEN

# Start everything
make start
```

Open `http://localhost` in your browser.

### Local Development

```bash
git clone https://github.com/Abdullah-0419/Agentic-kit.git
cd Agentic-kit

# Backend
pip install -e .
cp example.env .env
# Edit .env and set ANTHROPIC_AUTH_TOKEN
agent-kit run

# Frontend (in a separate terminal)
cd web
npm install
cp example.env .env.local
npm run dev
```

Open `http://localhost:3000` in your browser.

## Configuration

### Backend (.env)

| Variable | Description | Default |
|---|---|---|
| `ANTHROPIC_AUTH_TOKEN` | Claude API auth token | — |
| `ANTHROPIC_BASE_URL` | API base URL | `https://api.anthropic.com` |
| `ANTHROPIC_MODEL` | Model to use | `glm-5` |
| `PORT` | Server port | `8010` |
| `WORKSPACE_PATH` | Workspace root | `~/.agent-kit/workspace` |

### Frontend (.env.local)

| Variable | Description | Default |
|---|---|---|
| `NEXT_PUBLIC_API_URL` | Backend API URL | `http://localhost:8010/agent/v1` |
| `NEXT_PUBLIC_WS_URL` | WebSocket URL | `ws://localhost:8010/agent/v1/chat/ws` |
| `NEXT_PUBLIC_DEFAULT_MODEL` | Default model | `glm-5` |

## Project Structure

```
agent-kit/
├── agent/          # FastAPI backend (API routes, services, storage)
├── web/            # Next.js frontend (React components, Zustand state)
├── deploy/         # Docker and deployment configs
├── docs/           # Documentation and guides
├── main.py         # Application entry point
└── example.env     # Environment variable template
```

## Third-Party IM Integration

Agent Kit supports Discord and Telegram bots alongside the web UI. Enable them by setting `DISCORD_ENABLED=true` or `TELEGRAM_ENABLED=true` in your `.env` file along with the corresponding bot tokens. All channels share a unified session routing system.

## Documentation

Detailed guides are available in the [docs](docs/) directory, covering session management, streaming modes, custom tools, slash commands, MCP integration, hosting, and permissions.

## License

Apache License 2.0 — see [LICENSE](LICENSE) for details.
