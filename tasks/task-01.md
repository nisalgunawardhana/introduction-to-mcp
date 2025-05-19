# Task 01: Getting Started with MCP

## Objective
The goal of this task is to familiarize yourself with the Model Context Protocol (MCP) and set up your first MCP server.

## Instructions
1. **Read the Introduction**: Begin by reviewing the `01-introduction.md` file to understand the basics of MCP and its significance in AI applications.

2. **Set Up Your Environment**:
   - Ensure you have the necessary software installed:
     - Python 3.10 or higher
     - The MCP Python SDK (version 1.2.0 or higher)
   - Create a new directory for your MCP project:
     ```
     mkdir my-mcp-project
     cd my-mcp-project
     ```

3. **Install Dependencies**:
   - Use the following command to set up your environment:
     ```
     uv init my-mcp-server
     cd my-mcp-server
     uv venv
     source .venv/bin/activate  # For MacOS/Linux
     .venv\Scripts\activate     # For Windows
     uv add "mcp[cli]" httpx
     ```

4. **Create Your Server File**:
   - Create a new file named `server.py` in your project directory:
     ```
     touch server.py
     ```

5. **Implement Basic Server Code**:
   - Open `server.py` and add the following code to initialize a simple MCP server:
     ```python
     from mcp.server.fastmcp import FastMCP

     mcp = FastMCP("my-server")

     @mcp.tool()
     async def hello() -> str:
         return "Hello, MCP!"

     if __name__ == "__main__":
         mcp.run(transport='stdio')
     ```

6. **Run Your Server**:
   - Start your MCP server using the command:
     ```
     uv run server.py
     ```

7. **Test Your Server**:
   - Use a client (like Claude for Desktop) to connect to your server and test the `hello` tool by sending a request.

## Completion
Once you have successfully set up and tested your MCP server, you can move on to the next task. Document any issues you encountered and how you resolved them in your project notes.