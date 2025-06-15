# 🌦 MCP Weather Tool for n8n (Demo Workflow)

This repo provides a **ready-to-use n8n workflow** that connects to a hosted [Model Context Protocol (MCP)](https://modelcontextprotocol.org/) server for weather forecasts.

---

## 🚀 What This Is

- A working example of how to call a **custom MCP tool** from n8n
- The tool fetches **current or 3-day weather forecasts**
- Hosted MCP endpoint:  
  👉 https://mcp-weathertrax.jaredco.com/call-tool

This demo uses the **MCP Agent node** in n8n to send tool calls to the server.

---

## 🧪 Try It in n8n

Download or import the sample workflow:

➡ [View or download the sample n8n workflow (GitHub Gist)](https://gist.github.com/jaredco-ai/103b2ac9fc56dcdf8dc92fcb8d33a187)

### How to Use

1. Open the link above and click **"Raw"**
2. Copy the JSON and go to n8n
3. Use **Import Workflow → Paste JSON**
4. Update the `MCP Agent` node with the tool call:

```
POST https://mcp-weathertrax.jaredco.com/call-tool
```

---

## 📥 Tool Input Format

The weather tool accepts this JSON input:

```json
{
  "location": "New York",
  "forecastType": "current" // or "3-day"
}
```

---

## 🧠 Suggested Agent System Message

```
You are a helpful weather assistant. Given a location and forecast type (current or 3-day), return a short summary of the weather conditions using the tool provided.
```

---

## 🛠 Built With

- [Model Context Protocol](https://modelcontextprotocol.org/)
- [n8n.io](https://n8n.io/)
- Hosted weather tool by [JaredCo](https://jaredco.com/)

---

## 🙋 Feedback?

Feel free to open an issue or fork this repo with improvements.  
Would love to hear from others experimenting with MCP or tool-driven AI workflows!
