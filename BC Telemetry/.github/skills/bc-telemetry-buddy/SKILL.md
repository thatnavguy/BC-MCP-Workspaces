---
name: bc-telemetry-buddy
description: 'Use when querying or analyzing Business Central telemetry, investigating BC errors or performance, or writing KQL for Application Insights. Prefer live BC Telemetry Buddy MCP tools; if they are unavailable, stop live-data analysis and tell the user how to start the server.'
---

# BC Telemetry Buddy

Use the BC Telemetry Buddy MCP tools as the source of truth for live Business Central telemetry. For exploratory questions, discover relevant events and fields before writing a query. Use the query tools to retrieve and analyze actual data rather than guessing results.

## MCP Availability

- If the BC Telemetry Buddy tools are not available in the current chat, do not claim to have queried telemetry or fabricate results.
- Stop the live-data workflow and tell the user to run **MCP: List Servers** from the VS Code Command Palette, start `bc-telemetry-buddy`, and retry the request.
- Do not attempt to launch the stdio MCP server manually in a terminal.
- If a Buddy tool is available but reports a configuration or authentication error, report the error and suggest checking `.bctb-config.json`, Azure CLI sign-in, and access to the configured Application Insights resource.
- General BC telemetry explanations and KQL syntax help can still be answered without live data; clearly distinguish examples from verified telemetry results.