# Guided Demo: Building a Cloudy Weather MCP Server with Claude and Online API

## Objective
Build an MCP server that fetches real-time weather data from an online API (e.g., Open-Meteo) using Python, with step-by-step guidance and smart tips. You will use Claude (or another LLM) to help you write, debug, and improve your code.

---

## Prerequisites
- Python 3.10+
- `uv` package manager ([install guide](https://astral.sh/uv/))
- Claude or another LLM access

---

## Step 1: Prepare Your Workspace
1. Create a new directory for your project:
   ```sh
   uv init cloud-weather
   cd cloud-weather
   ```
2. Set up a virtual environment:
   ```sh
   uv venv
   source .venv/bin/activate
   ```
3. Install dependencies:
   ```sh
   uv add "mcp[cli]" httpx
   ```

---

## Step 2: Describe Your Goal to Claude
- Open Claude and paste this prompt:
  > I want to build an MCP server in Python that fetches current weather data for any city using the Open-Meteo API. The server should expose a tool called `get_weather` that takes a city name and returns the current weather. Please help me write the code step by step, explain each part, and suggest improvements.

---

## Step 3: Build the Server with Claude’s Help
1. **Ask Claude for the initial code structure.**
   - Request imports, server setup, and a basic tool definition.
2. **Iterate:**
   - If you get stuck, ask Claude for clarification or debugging help.
   - Request code comments and best practices.
3. **Sample code outline:**
   ```python
   from mcp.server.fastmcp import FastMCP
   import httpx

   mcp = FastMCP("cloud-weather")

   @mcp.tool()
   async def get_weather(city: str) -> str:
       # Use Open-Meteo or another API to fetch weather for the city
       ...

   if __name__ == "__main__":
       mcp.run(transport='stdio')
   ```
4. **Ask Claude to help you implement the API call logic.**
   - Use the Open-Meteo API docs: https://open-meteo.com/en/docs
   - Example endpoint: `https://api.open-meteo.com/v1/forecast?latitude=...&longitude=...&current_weather=true`
   - You may need to convert city names to coordinates (Claude can help with this logic or suggest a geocoding API).

---

## Step 4: Test Your Server
1. Run your server:
   ```sh
   uv run cloud-weather.py
   ```
2. Use the MCP Inspector or Claude Desktop to connect and test the `get_weather` tool.
3. Try queries like:
   - "What is the weather in London?"
   - "Get the current weather for New York."

---

## Step 5: Smart Guidance & Tips
- **Iterate with Claude:**
  - Ask for error handling, logging, and code improvements.
  - Request explanations for any part you don’t understand.
- **Security:**
  - Never expose API keys or sensitive data in code.
- **Documentation:**
  - Ask Claude to help you write clear docstrings and usage instructions.
- **Debugging:**
  - Use the Inspector and logs to troubleshoot issues.

---

## Step 6: (Optional) Extend the Demo
- Add more tools (e.g., weather forecast, severe alerts).
- Support more cities or languages.
- Connect to other online services (e.g., news, air quality).

---

## Reflection
- What did you learn from working with Claude?
- How did LLM guidance help you solve problems?
- What would you improve next time?

---

**Congratulations!** You’ve built a real MCP server with LLM-powered guidance and live online data.
