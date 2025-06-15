MCP Weather Tool — Sample Server

This repo contains a working Model Context Protocol (MCP) server that integrates a custom weather tool. It responds to AI agent tool calls and returns current or multi-day weather forecasts using OpenWeatherMap.

🌐 Live Server

https://mcp-weathertrax.jaredco.com

This server is intended for use with AI agents or tools.
Browser visits to / redirect here.

⸻

💡 What It Does
	•	Accepts structured tool calls (e.g., from n8n or any MCP agent)
	•	Returns a weather forecast based on location and forecast type
	•	Responds with short, clear summaries for agent-friendly output

⸻

🚀 Try It Out

To test this server locally:

git clone https://github.com/jaredco-ai/mcp-weather-sample.git
cd mcp-weather-sample
yarn install
node mcp-server.js

🔓 No API key is required for this sample server.

⸻

🧠 Agent System Message

You are a helpful weather assistant. Given a location and forecast type (current or 3-day), return a short summary of the weather conditions using the tool provided.

⸻

🔧 Tool Input Format

{
  "location": "New York",
  "forecastType": "current" // or "3-day"
}


⸻

🛠 Built With
	•	Model Context Protocol SDK — https://github.com/modelcontext/protocol
	•	OpenWeatherMap API — https://openweathermap.org/api
	•	n8n — https://n8n.io/

⸻

🙋 Feedback or Questions?

I’m experimenting with MCP and n8n integrations — feel free to open an issue or submit a PR.
Would love to hear from others building similar tools!

 
