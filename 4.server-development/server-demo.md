# Server Demo for Model Context Protocol (MCP)

In this section, we will walk through the process of setting up a server using the Model Context Protocol (MCP). This demonstration will include code examples and explanations to help you understand how to create a functional server that can interact with clients.

## Prerequisites

Before we begin, ensure you have the following installed:

- Python 3.10 or higher
- MCP Python SDK (version 1.2.0 or higher)
- Required libraries (e.g., `httpx`, `mcp`)

## Setting Up Your Server

1. **Create a New Directory for Your Project**

   Start by creating a new directory for your server project:

   ```bash
   mkdir my_mcp_server
   cd my_mcp_server
   ```

2. **Initialize Your Environment**

   Set up a virtual environment and install the necessary dependencies:

   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows use .venv\Scripts\activate
   pip install mcp[cli] httpx
   ```

3. **Create Your Server File**

   Create a new Python file for your server, e.g., `server.py`:

   ```bash
   touch server.py
   ```

4. **Implement the Server Logic**

   Open `server.py` and add the following code:

   ```python
   from typing import Any
   import httpx
   from mcp.server.fastmcp import FastMCP

   # Initialize FastMCP server
   mcp = FastMCP("my_server")

   # Constants
   API_BASE = "https://api.example.com"
   USER_AGENT = "my-server/1.0"

   async def make_request(url: str) -> dict[str, Any] | None:
       headers = {
           "User-Agent": USER_AGENT,
           "Accept": "application/json"
       }
       async with httpx.AsyncClient() as client:
           try:
               response = await client.get(url, headers=headers)
               response.raise_for_status()
               return response.json()
           except Exception:
               return None

   @mcp.tool()
   async def get_data(param: str) -> str:
       """Fetch data based on the provided parameter."""
       url = f"{API_BASE}/data/{param}"
       data = await make_request(url)
       return data if data else "No data found."

   if __name__ == "__main__":
       mcp.run(transport='stdio')
   ```

5. **Run Your Server**

   To start your server, run the following command in your terminal:

   ```bash
   uv run server.py
   ```

## Testing Your Server

Once your server is running, you can test it by sending requests through an MCP client. Ensure that your client is configured to connect to your server and that you have defined the necessary tools.

## Conclusion

This demonstration provided a basic setup for an MCP server. You can expand upon this foundation by adding more tools and functionalities as needed. For further exploration, refer to the best practices and troubleshooting sections in this course.