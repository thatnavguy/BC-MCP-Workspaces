# BC Knowledge

Use this workspace to ask GitHub Copilot questions about Microsoft Dynamics 365 Business Central. Three Model Context Protocol (MCP) servers provide object metadata, source-code details, and official Microsoft guidance.

## Choose a source

| Source | Use it for |
| --- | --- |
| BC Observatory (`bc-observatory`) | Object contents, fields, keys, obsolete status, version differences, localizations, and broad feature overviews. |
| BC Code Atlas (`bc-code-atlas`) | How standard AL source works, including procedure bodies, callers, event subscribers, and object relationships. |
| Microsoft Learn (`microsoft-learn`) | Official product documentation, setup guidance, tutorials, and Microsoft code samples. |

For questions about an object or its obsolete members, use Observatory. For exact implementation details, use Code Atlas. Use Microsoft Learn for official product guidance. These sources complement each other; Microsoft Learn is not a substitute for base-application object metadata or source code.

## Ask a question

Name the Business Central version and country or localization when they matter. Ask about one object or behavior at a time when you need a precise answer.

Examples:

- "In my BC version and localization, which fields on Customer (table 18) are obsolete?"
- "What does this standard procedure do, and what calls it?"
- "What does Microsoft Learn recommend for this Business Central setup?"

Ask for evidence or links when you need to verify an answer. The agent should say when a source does not cover the requested version or localization.

## Start the servers

The workspace configuration is in `.vscode/mcp.json`. It defines these servers:

- `bc-observatory`: local `npx` process. Node.js, `npx`, and network access are required.
- `bc-code-atlas`: remote HTTP server. Network access is required.
- `microsoft-learn`: remote HTTP server. Network access is required.

To start a server in VS Code:

1. Open the Command Palette with **Ctrl+Shift+P**.
2. Run **MCP: List Servers**.
3. Select the server and choose **Start Server**. If it is already running but not responding, choose **Restart Server**.
4. In Copilot Chat, use **Agent** mode and make sure the server's tools are enabled for the session.

A server entry in `mcp.json` means it is configured. It does not confirm that the server is running or that its tools are available to the current chat.

VS Code's experimental MCP auto-start runs when you submit a chat message; it does not start servers just because you opened the project. Its default setting is `chat.mcp.autostart: newAndOutdated`. A server that was stopped manually may need to be started from **MCP: List Servers**.

## Troubleshoot

- If a needed server's tools are missing, run **MCP: List Servers** and start or restart that server. Continue once its tools appear in the session.
- If the server fails to start, open the server's menu in **MCP: List Servers** and choose **Show Output**. Check the message for startup, network, or authentication errors.
- If `bc-observatory` fails to start, check that `node` and `npx` are available in the environment where VS Code runs.
- If a server is running but Copilot does not use it, check **Agent** mode and the session's tool selection. A running server does not guarantee that its tools are enabled or selected for a request.
- Do not treat Microsoft Learn or generic AL symbol search as a replacement for Observatory object metadata or Code Atlas source details. If the required source is unavailable, state that and ask for the server to be started or reconnected.

## Project files

- `.vscode/mcp.json` defines the three MCP servers.
- `.github/skills/bc-knowledge/SKILL.md` guides source selection and evidence-based answers.