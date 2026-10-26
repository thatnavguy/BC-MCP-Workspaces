# BC Telemetry Workspace

This workspace connects GitHub Copilot to Business Central telemetry through the BC Telemetry Buddy MCP server.

## What You Need

- Visual Studio Code with GitHub Copilot Chat.
- Node.js 22.23.4+, 24.22.1+, or 26.12.1+, and npm 9+.
- Azure CLI, if you use the recommended `azure_cli` sign-in method.
- A Business Central Application Insights resource and permission to read its data.

## Set Up the Workspace

### 1. Create the telemetry configuration

This workspace uses `.bctb-config.json` for its connection details. If the file does not exist, create a starter file from the workspace folder:

```powershell
npx -y bc-telemetry-buddy-mcp init --output .bctb-config.json
```

If the file already exists, edit it instead of running the initialization command again.

For the default profile, set these values:

| Field | Value |
| --- | --- |
| `connectionName` | A name for this connection, such as `BC Production` |
| `authFlow` | `azure_cli` |
| `applicationInsightsAppId` | The Application ID from the Application Insights resource's **API access** page |
| `kustoClusterUrl` | `https://ade.applicationinsights.io/subscriptions/<subscription-id>` |
| `workspacePath` | The workspace folder, usually `.` |
| `queriesFolder` | The folder for saved queries, usually `queries` |

The Application ID is not the instrumentation key or the Azure subscription ID. The subscription ID belongs in `kustoClusterUrl`.

Do not commit `.bctb-config.json`. It can contain private connection details. If this workspace uses Git, add the file to `.gitignore`.

### 2. Sign in to Azure

The `azure_cli` method uses your existing Azure CLI session. Sign in and select the subscription that contains the Application Insights resource:

```powershell
az login
az account set --subscription "<subscription-id>"
```

Your signed-in account must have permission to read the Application Insights resource.

### 3. Check the configuration and access

Run these commands from the workspace folder:

```powershell
npx -y bc-telemetry-buddy-mcp validate --config .bctb-config.json
npx -y bc-telemetry-buddy-mcp test-auth --config .bctb-config.json
```

The first command checks the configuration. The second checks Azure sign-in and access to Application Insights.

## Start the MCP Server

The workspace already registers the server in `.vscode/mcp.json`. VS Code runs it with `npx`; the first start may download the package.

1. Open the Command Palette with `Ctrl+Shift+P`.
2. Run **MCP: List Servers**.
3. Select `bc-telemetry-buddy` and start it.
4. Open Copilot Chat and ask: “List available BC telemetry profiles.”

For a live-data check, ask Copilot to list recent Business Central telemetry events. The server must be running, and your Azure account must have access to the configured resource.

## Telemetry Skill

The workspace skill in `.github/skills/bc-telemetry-buddy/SKILL.md` guides Copilot to use the MCP tools for telemetry questions. If the tools are unavailable, it tells Copilot to stop live-data analysis and ask you to start the server. It does not start the server itself.

The skill can also be invoked in chat with `/bc-telemetry-buddy`. General explanations and example KQL can still be provided without live data, but they should not be presented as results from your Application Insights resource.