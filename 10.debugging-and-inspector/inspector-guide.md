# MCP Inspector Guide

The MCP Inspector is an interactive developer tool for testing and debugging MCP servers.

## Getting Started
- Run Inspector via npx: `npx @modelcontextprotocol/inspector <command>`
- Inspect NPM/PyPi servers: `npx -y @modelcontextprotocol/inspector npx <package-name> <args>`
- Inspect local servers: `npx @modelcontextprotocol/inspector node path/to/server/index.js args...`

## Feature Overview
- **Server Connection Pane**: Select transport, customize args/env
- **Resources Tab**: List and inspect resources, metadata, and content
- **Prompts Tab**: View and test prompt templates
- **Tools Tab**: List, test, and execute tools
- **Notifications Pane**: View logs and notifications

## Development Workflow
- Launch Inspector and verify connectivity
- Test resources, prompts, and tools
- Make code changes, rebuild, and reconnect Inspector
- Test edge cases and error handling

## Best Practices
- Use Inspector for iterative development
- Test invalid inputs and concurrent operations
- Monitor logs and error responses
