---
name: bc-knowledge
description: "Use when asking questions about Microsoft Dynamics 365 Business Central, including AL development, standard application behavior, objects, events, versions, localizations, documentation, and ecosystem updates."
---

# Business Central Knowledge

Use the connected Business Central sources to answer questions with evidence. Choose the source that best fits the question; do not call every server for every request.

## Choose the right source

| Question | Source |
|---|---|
| What an object contains, version differences, country localizations, or what is new | BC Observatory |
| How standard AL source works, the exact body of a procedure, callers, subscribers, or object relationships | BC Code Atlas |
| Official product guidance, full documentation, or Microsoft code samples | Microsoft Learn |
| How the user's own extension works | Workspace source code |

For broad questions, start with the Observatory's `bc_brief`. Follow up with Code Atlas for source-level details or Microsoft Learn for official guidance when useful.

## When a required source is unavailable

If the required Observatory or Code Atlas tools are missing from the current session, or a call fails because the server is stopped or disconnected:

1. Check `.vscode/mcp.json` when it is available. A server entry shows that it is configured, not that it is running or available to this session.
2. If the matching server is configured, stop the lookup and ask the user to run **MCP: List Servers**, select `bc-observatory` or `bc-code-atlas`, and choose **Start Server** or **Restart Server**. Continue only after the tools become available.
3. If the server is not configured, or its tools are still unavailable after restart, explain that the source is unavailable in this session and stop. Do not guess or silently substitute another source.

Do not use generic AL symbol search or Microsoft Learn as a substitute for Observatory object metadata or Code Atlas source details. Use Microsoft Learn when the question is about official product guidance, as described above.

## Find evidence

### BC Observatory

- Use `bc_search` to find objects, fields, events, documentation, or community posts by topic.
- Use `bc_get_object` for object metadata, fields, keys, events, procedures, obsolete state, and version history.
- Use `bc_brief` for a broad, evidence-based overview of a feature.
- Use `bc_diff_object` to compare a W1 object across versions and `bc_localization` to compare a country layer with W1.
- Use `bc_whats_new` for updates since a date.
- Use `bc_ls` and `bc_cat` to browse and read indexed pages.
- Use `bc_status` to check data coverage and freshness.

### BC Code Atlas

- Use `bcatlas_search` to find source code or documentation by meaning.
- Use `bcatlas_query_graph` to investigate calls, subscriptions, extensions, and other relationships.
- Use `bcatlas_get_node` or `bcatlas_get_neighbors` to inspect a node and its connections.
- Use `bcatlas_get_signature` before retrieving more source when a declaration needs confirmation.
- Use `bcatlas_get_procedure_body` for the exact body of a procedure or trigger.
- Use `bcatlas_get_object_source` for the full source of an object.
- Use the country and version tools to resolve a source scope. For a non-default scope, follow the server's request and readiness workflow before querying it.

### Microsoft Learn

- Use `microsoft_docs_search` to find official Learn articles.
- Use `microsoft_docs_fetch` to read an article.
- Use `microsoft_code_sample_search` to find official code samples.

## Answer with care

1. Ground product and source-code claims in retrieved evidence. Link the relevant source when possible.
2. State version and country scope when the answer depends on them. Do not treat W1 as universal across localizations.
3. Use exact source text for procedure behavior. A graph relationship alone does not prove what the procedure does.
4. Distinguish Microsoft Learn guidance from findings in unofficial sources such as Observatory and Code Atlas.
5. Say when evidence is missing or incomplete. Do not invent object members, behavior, events, or release details.
6. For questions about the user's extension, inspect workspace code. Do not treat standard Business Central source as proof of custom-code behavior.
