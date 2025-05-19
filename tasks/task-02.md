# Task 02: Implementing a Simple MCP Server

## Objective
In this task, you will implement a simple server using the Model Context Protocol (MCP). This server will expose basic functionalities that can be utilized by an MCP client.

## Instructions

1. **Set Up Your Environment**:
   - Ensure you have Python 3.10 or higher installed.
   - Install the MCP SDK by running:
     ```
     pip install mcp[cli] httpx
     ```

2. **Create a New Python File**:
   - Create a new file named `simple_mcp_server.py` in your project directory.

3. **Implement the Server**:
   - Open `simple_mcp_server.py` and add the following code:

     ```python
     from typing import Any
     import httpx
     from mcp.server.fastmcp import FastMCP

     # Initialize FastMCP server
     mcp = FastMCP("simple_server")

     @mcp.tool()
     async def greet(name: str) -> str:
         """Greet the user by name."""
         return f"Hello, {name}!"

     if __name__ == "__main__":
         mcp.run(transport='stdio')
     ```

4. **Run Your Server**:
   - Execute the server by running:
     ```
     uv run simple_mcp_server.py
     ```

5. **Test Your Server**:
   - Connect to your server using an MCP client and test the `greet` tool by sending a request with a name.

## Goals
- Successfully implement and run a simple MCP server.
- Understand how to expose tools using the MCP framework.
- Test the server functionality using an MCP client.

## Additional Resources
- Refer to the official MCP documentation for more details on server implementation and tool creation.