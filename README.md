# Graphiti MCP Server (Personality Knowledge Graph)

A private MCP server for querying a personality psychology knowledge graph, powered by [Graphiti](https://github.com/getzep/graphiti) and Neo4j Aura.

## Features

- **Knowledge Graph**: 16,000+ nodes covering personality psychology research, traits, types, frameworks, and assessments
- **Semantic Search**: Search facts and entities using natural language
- **MCP Protocol**: Compatible with Claude, Cursor, and other MCP clients
- **Cloud Hosted**: Runs on Railway with Neo4j Aura backend

## Quick Start

### For MCP Clients (Cursor, Claude Desktop)

Connect to the hosted server:

```json
{
  "mcpServers": {
    "personality-knowledge": {
      "url": "https://YOUR_RAILWAY_URL/mcp/"
    }
  }
}
```

### Local Development

1. Clone and install dependencies:
```bash
git clone https://github.com/YOUR_USERNAME/graphiti-mcp-server.git
cd graphiti-mcp-server
uv sync
```

2. Set environment variables:
```bash
cp .env.example .env
# Edit .env with your credentials
```

3. Run the server:
```bash
uv run main.py --config config/config-aura.yaml
```

## Configuration

The server is configured via YAML files in `config/`:

- `config-aura.yaml` - Production config for Neo4j Aura
- `config-docker-neo4j.yaml` - Local development with Docker Neo4j

### Required Environment Variables

| Variable | Description |
|----------|-------------|
| `NEO4J_URI` | Neo4j Aura connection URI |
| `NEO4J_USER` | Neo4j username (usually `neo4j`) |
| `NEO4J_PASSWORD` | Neo4j password |
| `OPENAI_API_KEY` | OpenAI API key for LLM/embeddings |

## Available MCP Tools

- `search_nodes` - Search for entity summaries by semantic similarity
- `search_facts` - Search for relationships/facts between entities
- `get_entity_edge` - Get details of a specific relationship
- `get_episodes` - Get recent episodes for a group
- `add_episode` - Add new information to the knowledge graph
- `get_status` - Check server and database status

## Deployment

### Railway

1. Create a new Railway project
2. Connect this repository
3. Set environment variables in Railway dashboard
4. Deploy

The `railway.toml` and `docker/Dockerfile.standalone` are pre-configured for Railway deployment.

## Knowledge Graph Contents

This instance contains indexed personality psychology textbooks covering:

- **Personality Traits**: Big Five, HEXACO, temperament dimensions
- **Personality Types**: MBTI, Enneagram, Socionics
- **Frameworks**: Theoretical models and assessment frameworks
- **Researchers**: Key figures in personality psychology
- **Assessments**: Psychological inventories (NEO-PI-R, HEXACO-PI-R, etc.)

## License

This MCP server configuration is for private use. The underlying Graphiti framework is licensed under Apache 2.0.

