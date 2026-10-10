# playwright for OpenAgent

Browser automation through the Microsoft Playwright MCP server.

Install the release archive through OpenAgent Integrations → Plugins. This is an independent adaptation.

## Setup

- Node.js/npm and browser installation required by @playwright/mcp 0.0.83.

Run /playwright:setup. Package state and credentials belong in the active OpenAgent home at plugin-data/playwright/. Never place secrets in plugin.json or commit them. Refresh the plugin after changing credentials.

## Verification

bun test tests

Bundled tests cover immutable artifacts, config conversion and service configuration and missing prerequisites. Runtime acceptance also verifies a real staged installation, slash-command catalog and integration_status. External account authentication, real provider operations and macOS permissions require the prerequisites above; package tests do not claim those credentials are available.

## 中文

通过 Microsoft Playwright MCP 服务自动操作浏览器。 安装发布包后运行 /playwright:setup 查看配置要求。凭据和状态保存在当前 OpenAgent 数据目录的 plugin-data/playwright/ 下，修改后刷新插件。

Upstream source and exact revision are recorded in provenance.json. Bundled source remains available for inspection.

Dependency download caches and managed Python installations stay under PLUGIN_DATA; the user-home npm/uv cache is not writable under confinement.

## Windows managed sandbox qualification

The shipped Runtime can connect the setup MCP, but this qualification environment rejects secondary native process launches (Chrome/Python and some npm commands) with EPERM/Access denied. Service operations requiring those children are not qualified on this Windows Runtime. Keep confinement enabled; setup status does not claim those operations work. Use a supported Runtime/platform and independently verify the primary service before relying on it.
