# Business Central MCP Workspaces

This repository contains separate Visual Studio Code workspaces for Microsoft Dynamics 365 Business Central. Open the folder for the tools you want to use; each folder loads only its own Model Context Protocol (MCP) servers and guidance.

## Choose a workspace

| Folder | Use it for | MCP servers |
| --- | --- | --- |
| [BC Knowledge](./BC%20Knowledge/) | Questions about Business Central objects, AL source code, and Microsoft guidance. | BC Observatory, BC Code Atlas, Microsoft Learn |
| [BC Telemetry](./BC%20Telemetry/) | Questions about telemetry in your Business Central Application Insights resource. | BC Telemetry Buddy |

## Open a workspace

1. In Visual Studio Code, select **File > Open Folder**.
2. Select **BC Knowledge** or **BC Telemetry**. Do not open the repository root when you want to use only one workspace.
3. Follow the setup instructions in that folder's README.
4. In Copilot Chat, use the tools for the workspace you opened.

Each workspace folder has its own `.vscode/mcp.json` file. VS Code reads the MCP configuration from the folder you open. This keeps each tool set separate.

## Why use separate workspaces?

- **Keep the context focused.** Copilot sees the instructions and MCP tools for the task at hand, rather than unrelated tools from other workspaces.
- **Use less context where possible.** A smaller set of relevant tools and instructions can reduce the context used in a chat.
- **Manage costs more effectively.** Lower context use may reduce usage costs, depending on the model, tools, and how you use Copilot.
- **Make each workspace easier to understand.** Its README, MCP configuration, and guidance relate to one purpose.

## Workspace guides

- [BC Knowledge setup and usage](./BC%20Knowledge/README.md)
- [BC Telemetry setup and usage](./BC%20Telemetry/README.md)

## Keep connection details private

The BC Telemetry workspace uses `.bctb-config.json` for connection details. Keep this file private and do not commit it.
