# Workspace Agent Instructions

For every Business Central-related request in this workspace, follow `.github/skills/bc-knowledge/SKILL.md` before researching or answering. This includes questions about Business Central versions, product behavior, AL development, standard application objects, localizations, and this workspace's BC knowledge sources. Do not apply this workflow to unrelated questions.

Use the source selection and evidence rules in the BC knowledge skill. For broad questions such as what's new in a version, start with BC Observatory's `bc_brief`. Use Microsoft Learn for official product guidance, not as a substitute for Observatory object metadata or Code Atlas source details.

If a required source is unavailable, check `.vscode/mcp.json`. When its server is configured, tell the user to start or restart it with **MCP: List Servers**, and continue only after its tools are available. If it is not configured or remains unavailable, explain that and stop; do not silently substitute another source or guess.

Do not assume that a server configured for one editor is available to another agent client. Verify that the required MCP tools are available in the current session.
