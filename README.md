# developer-presence-mcp

An MCP server that connects your **GitHub** and **DEV.to** profiles to Claude (or any MCP client). Query your repos, stats, and articles — or create and publish new DEV.to posts — all from a conversation.

Built with [FastMCP](https://github.com/modelcontextprotocol/python-sdk) · Python stdlib only for HTTP · No heavy dependencies.

## Tools

### GitHub
| Tool | Description |
|------|-------------|
| `get_github_profile` | Followers, repos, bio |
| `list_repos` | Public repos sorted by updated/stars/forks |
| `get_repo_stats` | Stars, forks, watchers, open issues for a repo |

### DEV.to
| Tool | Description |
|------|-------------|
| `list_articles` | Your published articles with reaction/view counts |
| `create_article` | Draft or publish a new article |
| `update_article` | Edit title, body, or publish state |
| `get_article_stats` | Reactions, comments, page views for an article |

## Setup

**1. Clone and install**
```bash
git clone https://github.com/enjoykumawat/developer-presence-mcp
cd developer-presence-mcp
pip install -r requirements.txt
```

**2. Create `.env`**
```bash
cp .env.example .env
# Fill in your credentials
```

Get your keys:
- **GitHub token**: [github.com/settings/tokens](https://github.com/settings/tokens) → scopes: `repo`, `user`
- **DEV.to API key**: [dev.to/settings/extensions](https://dev.to/settings/extensions) → DEV Community API Keys

**3. Run**
```bash
# Dev mode with MCP Inspector
mcp dev server.py

# Or directly
python server.py
```

## Claude Desktop

Add to `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "developer-presence": {
      "command": "python",
      "args": ["/path/to/developer-presence-mcp/server.py"],
      "env": {
        "GITHUB_TOKEN": "your_token",
        "GITHUB_USERNAME": "your_username",
        "DEV_TO_API": "your_devto_key",
        "DEV_USERNAME": "your_devto_username"
      }
    }
  }
}
```

## Example prompts

Once connected to Claude:

> "Show me my most starred GitHub repos"

> "Draft a DEV.to article about my latest project and publish it"

> "How many reactions did my last article get?"

> "List my repos sorted by stars"

## Author

Built by [@enjoykumawat](https://github.com/enjoykumawat) — AI agent tooling contributor, MCP python-sdk contributor.

- DEV.to: [@enjoy_kumawat](https://dev.to/enjoy_kumawat)
- GitHub: [@enjoykumawat](https://github.com/enjoykumawat)
