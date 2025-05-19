# Client Demo for Model Context Protocol (MCP)

In this section, we will demonstrate how to create a client that interacts with MCP servers. This client will be able to send requests to the server and handle responses effectively.

## Overview

The client will be built using Python and will utilize the MCP client SDK to establish a connection with the MCP server. We will cover the following steps:

1. **Setting Up the Environment**
2. **Creating the Client**
3. **Connecting to the MCP Server**
4. **Sending Requests and Handling Responses**
5. **Testing the Client**

## 1. Setting Up the Environment

Before we begin, ensure you have the following installed:

- Python 3.10 or higher
- MCP client SDK

You can set up your environment using the following commands:

```bash
# Create a new directory for your project
mkdir mcp-client-demo
cd mcp-client-demo

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

# Install the MCP client SDK
pip install mcp
```

## 2. Creating the Client

Create a new file named `client.py` in your project directory. This file will contain the code for our client.

## 3. Connecting to the MCP Server

In `client.py`, we will establish a connection to the MCP server. Here’s a basic example:

```python
import asyncio
from mcp import ClientSession

async def main():
    # Replace 'server_address' with the actual address of your MCP server
    async with ClientSession('server_address') as session:
        # Your code to interact with the server goes here

if __name__ == "__main__":
    asyncio.run(main())
```

## 4. Sending Requests and Handling Responses

Once connected, you can send requests to the server. For example, to call a tool exposed by the server:

```python
response = await session.call_tool('tool_name', {'param1': 'value1'})
print(response)
```

## 5. Testing the Client

Run your client using the following command:

```bash
python client.py
```

Make sure your MCP server is running and accessible. You should see the output from your tool calls in the console.

## Conclusion

This demo provides a basic framework for creating a client that interacts with MCP servers. You can expand upon this by adding more functionality, error handling, and user interaction as needed.