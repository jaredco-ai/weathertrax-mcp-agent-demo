# MCP Weather Tool — Sample Server

This repo contains a working MCP server that integrates a custom weather tool. It responds to AI agent calls to fetch current or multi-day weather forecasts using OpenWeatherMap.

## 🌦 Demo
Visit: [https://mcp-weathertrax.jaredco.com](https://mcp-weathertrax.jaredco.com)  
> For agents only — browser access redirects to this repo.

## 🔧 How It Works

- Accepts a tool call via `/call-tool` with a location and forecast type
- Uses OpenWeatherMap API to return JSON data
- Designed to integrate with the [n8n MCP Agent node](https://community.n8n.io/)

## 📦 Install Locally

```bash
git clone https://github.com/stevenkader/mcp-weather-sample.git
cd mcp-weather-sample
yarn install
