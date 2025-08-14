# 🌦 WeatherTrax MCP Agent Demo — n8n Workflow

This is a fully working example of how to call an external [MCP](https://modelcontext.org/) weather tool using **OpenAI's function-calling agent node inside n8n**.

✅ Ready to run — no editing required. Includes a manual trigger for quick testing.

✅ No authentication required; public endpoint for testing.

---

## 🚀 Features

- 📍 Natural language weather questions (e.g., “What's the 3-day forecast in Miami?”)
- ⚙️ Calls an external MCP server at [`https://mcp-weathertrax.jaredco.com`](https://mcp-weathertrax.jaredco.com)
- 🧠 Uses OpenAI GPT-4o via the Langchain Agent Node
- 🧪 Includes a built-in test input — no need to use a form on first run
- 🧾 Final debug node clearly shows function call + extracted parameters

---
![WeatherTrax Agent Workflow](https://github.com/jaredco-ai/weathertrax-mcp-agent-demo/raw/main/WeatherTrax-n8n.jpg)

---

## 📦 Quickstart (MCP / JSON-RPC)

You can call WeatherTrax directly as an MCP server in any MCP-compatible client, including Claude.

### JSON-RPC (Root `/` endpoint)

**Request:**
```bash
curl -s -X POST https://mcp-weathertrax.jaredco.com/   -H 'Content-Type: application/json'   -d '{
    "jsonrpc":"2.0",
    "id":"call-1",
    "method":"tools/call",
    "params":{
      "tool":"weatherTool",
      "arguments":{
        "location":"Miami, FL",
        "query_type":"current"
      }
    }
  }'
```

**Response:**
```json
{
  "jsonrpc": "2.0",
  "id": "call-1",
  "result": {
    "toolUseId": "call-1",
    "isFinal": true,
    "output": {
      "temperature_c": 31.2,
      "condition": "Partly Cloudy",
      "wind_kph": 14,
      "precip_mm": 0.0,
      "observed_at": "2025-08-12T20:12:00Z",
      "source": "WorldWeatherOnline"
    }
  }
}
```

---

## ⚡ Quickstart (Direct Tool Call)

If you just need weather data without JSON-RPC, call the `/tools/weatherTool` endpoint directly:

**Request:**
```bash
curl -s -X POST https://mcp-weathertrax.jaredco.com/tools/weatherTool   -H 'Content-Type: application/json'   -d '{
    "location":"40.7128,-74.0060",
    "query_type":"multi_day",
    "num_days":3
  }'
```

**Response:**
```json
{
  "forecast": [
    {
      "date": "2025-08-12",
      "high": 94,
      "low": 69,
      "condition": "Sunny"
    },
    {
      "date": "2025-08-13",
      "high": 88,
      "low": 73,
      "condition": "Patchy rain nearby"
    },
    {
      "date": "2025-08-14",
      "high": 86,
      "low": 75,
      "condition": "Moderate rain"
    }
  ]
}
```

---

## 💡 Example Use Cases

1. **Current Weather by City**  
   Query type: `current`  
   Example: *“What’s the weather in Boca Raton?”*

2. **5-Day Forecast by Coordinates**  
   Query type: `multi_day`  
   Example: *40.7128,-74.0060*

3. **Rain Timing Check**  
   Query type: `rain_check`  
   Include `date` to target a specific day.

---

## 📥 How to Use (n8n Workflow)

### 1. 🧠 Connect Your OpenAI API Key (Required)

Before running:

1. Click the `OpenAI Chat Model` node
2. Under **Credentials**, select your OpenAI account or click "Create New"
3. Paste your [OpenAI API key](https://platform.openai.com/account/api-keys)
4. Save

---

### 2. ▶️ Run the Workflow

1. Click the `🧪 Enter weather request` node
2. Press “Execute Workflow” from the top
3. The agent will parse the request and call the weather tool

---

### 3. 🧪 View the Output

Click the `🧪 View Results Here` node after execution to see:

- Full agent output
- The generated `tool_call`
- Parsed weather parameters (e.g., `location`, `query_type`, `num_days`)

---

## 🌤 About the Weather Tool

This MCP tool is hosted at:

```
https://mcp-weathertrax.jaredco.com
```

### Example Inputs:

```json
{
  "tool": "weatherTool",
  "input": {
    "location": "Boca Raton",
    "query_type": "current"
  }
}
```

```json
{
  "tool": "weatherTool",
  "input": {
    "location": "Miami",
    "query_type": "multi_day",
    "num_days": 5
  }
}
```

---

## 🔽 Download & Import into n8n

1. Download [`WeatherTrax_MCP_Agent_Demo.json`](./WeatherTrax_MCP_Agent_Demo.json)
2. In n8n, click **Import workflow** > **From file**
3. Attach your OpenAI credential and click “Execute Workflow”

---
