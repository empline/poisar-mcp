# Poisar MCP setup for Cline

Use the hosted endpoint `https://poisar.com/api/mcp` with Streamable HTTP. Read
README.md for the IDE settings example and the native Cline CLI add command.
The CLI transport flag is `http`; the IDE type is `streamableHttp`.

Preserve the user's existing MCP entries and keep `autoApprove` empty. Install
no local backend, hooks or additional dependencies for this connection.

Public discovery is available without an account or API key.

After connecting, discover the actual tool schemas. Test one read-only tool;
do not use registration, reporting, AI generation, billing or publication as a
setup probe. Do not invent credentials or grant broader scopes to pass a test.
Never write an account token or secret into a public file, issue or transcript.
OAuth consent and native approval remain separate user actions. Tool discovery
alone is not an execution grant.

Official setup: https://poisar.com/agents
Support: support@poisar.com
Privacy: https://poisar.com/privacy
Terms: https://poisar.com/terms
