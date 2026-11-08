# Poisar MCP connector

Connect [Gemini CLI](https://geminicli.com/docs/get-started/installation/) to
[Poisar](https://poisar.com)'s existing public MCP server. Read its product
overview, discover agent access documentation, and understand the boundary
between public information and authenticated application features.

## Install

```sh
gemini extensions install https://github.com/empline/poisar-mcp
```

Restart an existing Gemini CLI session after installation. Run `/mcp` inside
Gemini CLI to inspect the connection. No Poisar account or API key is required.
The extension connects over Streamable HTTP to `https://poisar.com/api/mcp`;
it installs no local server or additional dependencies.

## Try it

- "Use Poisar to explain its public agent access capabilities and boundaries."
- "Use Poisar to find the canonical agent guide and API discovery documents."

## Available tools

| Tool | Purpose |
| --- | --- |
| `poisar_get_public_overview` | Read the public product overview, discovery links, and protected-route boundaries. |
| `poisar_get_agent_readiness_links` | Get canonical public agent discovery links. |
| `poisar_get_support` | Read the manual public protocol support workflow and its privacy limits. |

All three tools take no arguments and are read-only. This integration cannot access
accounts, broker state, market feeds, authenticated application data, or submit
trades. It does not provide portfolio analysis, signals, or trading advice.

The manifest explicitly allows these three tools. New server tools need a reviewed
manifest update before they become available through this extension. No
automatic approval, credentials, local commands, hooks, or additional model
instructions are configured. The server enforces the public access boundary.

See the [agent guide](https://poisar.com/agents) and
[Privacy](https://poisar.com/privacy).

## Update or uninstall

```sh
gemini extensions update poisar
gemini extensions uninstall poisar
```

For a reproducible installation, append `--ref <full-commit-sha>` to the install
command. Review changes before updating an installed extension.

## Maintainers

The root `gemini-extension.json` is the complete integration. Its version is
independent of the remote MCP server version. Before releasing:

1. Compare the allowlist with live `tools/list`; require all three tools to advertise
   `readOnlyHint: true` and accept no arguments.
2. Verify initialization and all three tool calls with an MCP SDK client.
3. Confirm a call to an undeclared tool is refused.
4. Install from the public repository in a fresh `GEMINI_CLI_HOME` and require
   `gemini mcp list` to report Connected.
5. Confirm the public root manifest matches the tested file and that GitHub's
   `gemini-cli-extension` topic is present.

Google's [gallery](https://geminicli.com/extensions/) discovers public tagged
repositories on a documented daily crawl and lists extensions that pass
validation. Publishing here does not establish inclusion or endorsement.
[Release requirements](https://geminicli.com/docs/extensions/releasing/#list-your-extension-in-the-gallery).
