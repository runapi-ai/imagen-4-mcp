# @runapi.ai/imagen-4-mcp

RunAPI MCP server for the **Imagen 4** model line. Create tasks,
poll their status, and check pricing through a single RunAPI API key.

## Tools

- `remix_image` — create a Imagen 4 task (remix image) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `imagen-4-pro-remix-image`, `imagen-4`, `imagen-4-fast`, `imagen-4-ultra`.
- `text_to_image` — create a Imagen 4 task (text to image) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `imagen-4-pro-remix-image`, `imagen-4`, `imagen-4-fast`, `imagen-4-ultra`.
- `get_task` — fetch the current status and latest payload for a task.
- `check_pricing` — look up pricing for a model in this line.

## Configuration

Set a RunAPI API key via the `RUNAPI_API_KEY` environment variable, or write
it to `~/.config/runapi/config.json`:

```bash
mkdir -p ~/.config/runapi
echo '{"api_key":"YOUR_KEY"}' > ~/.config/runapi/config.json
```

Get an API key at https://runapi.ai. Pricing is listed at
https://runapi.ai/pricing.

## Usage

Run the server over stdio:

```bash
npx -y @runapi.ai/imagen-4-mcp
```

Add it to an MCP client (see `examples/` for per-client configs):

```json
{
  "mcpServers": {
    "imagen-4": {
      "command": "npx",
      "args": ["-y", "@runapi.ai/imagen-4-mcp"],
      "env": { "RUNAPI_API_KEY": "${RUNAPI_API_KEY}" }
    }
  }
}
```

## License

Apache-2.0
