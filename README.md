# 🌦 WeatherTrax MCP Agent Demo — n8n Workflow

This is a fully working example of how to call an external [MCP](https://modelcontext.org/) weather tool using **OpenAI's function-calling agent node inside n8n**.

✅ Ready to run — no editing required. Includes a manual trigger for quick testing.

---

## 🚀 Features

- 📍 Natural language weather questions (e.g., “What's the 3-day forecast in Miami?”)
- ⚙️ Calls an external MCP server at [`https://mcp-weathertrax.jaredco.com`](https://mcp-weathertrax.jaredco.com)
- 🧠 Uses OpenAI GPT-4o via the Langchain Agent Node
- 🧪 Includes a built-in test input — no need to use a form on first run
- 🧾 Final debug node clearly shows function call + extracted parameters

---

## 📥 How to Use

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
