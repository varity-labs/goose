---
title: Varity Extension
description: Add Varity MCP Server as a goose Extension
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import GooseDesktopInstaller from '@site/src/components/GooseDesktopInstaller';
import CLIExtensionInstructions from '@site/src/components/CLIExtensionInstructions';

This tutorial covers how to add the [Varity MCP Server](https://github.com/varity-labs/varity-mcp) as a goose extension to deploy apps, AI agents, and self-hosted LLMs to production, with the monthly cost shown before anything is deployed.

:::tip Quick Install
<Tabs groupId="interface">
  <TabItem value="ui" label="goose Desktop" default>
  [Launch the installer](goose://extension?cmd=npx&arg=-y&arg=%40varity-labs%2Fmcp&id=varity-mcp&name=Varity&description=Deploy%20apps%2C%20AI%20agents%2C%20and%20LLMs%20to%20production%20with%20the%20cost%20shown%20before%20you%20deploy.)
  </TabItem>
  <TabItem value="cli" label="goose CLI">
  **Command**
  ```sh
  npx -y @varity-labs/mcp
  ```
  </TabItem>
</Tabs>
:::

## Configuration

:::info
You need [Node.js](https://nodejs.org/) 22.11 or later to run this command, as it uses `npx`.
:::

Deploys use the Varity CLI. Install it and sign in with a deploy key from the [Varity developer portal](https://developer.store.varity.so):

```bash
pipx install varitykit
varitykit auth login
```

### Add Varity MCP Server

<Tabs groupId="interface">
  <TabItem value="ui" label="goose Desktop" default>
  <GooseDesktopInstaller
    extensionId="varity-mcp"
    extensionName="Varity"
    description="Deploy apps, AI agents, and LLMs to production with the cost shown before you deploy."
    command="npx"
    args={["-y", "@varity-labs/mcp"]}
  />
  </TabItem>
  <TabItem value="cli" label="goose CLI">
    <CLIExtensionInstructions
      name="Varity"
      description="Deploy apps, AI agents, and LLMs to production with the cost shown before you deploy"
      command="npx -y @varity-labs/mcp"
    />
  </TabItem>
</Tabs>

## What you can do

- Deploy a project from its Git repository (or a prebuilt container image) with `varity_deploy`. Varity detects the framework (Next.js, React, Vue, Astro, Express, Fastify, NestJS, FastAPI, Django, Flask, static sites, Dockerfile apps), builds it, and attaches the databases the app needs.
- Run open-source apps such as Open WebUI, Langflow, Uptime Kuma, or Metabase with `varity_list_templates` and `varity_deploy_template`.
- Check the monthly cost before deploying with `varity_cost_calculator`.
- Follow a deploy with `varity_deploy_status` and `varity_deploy_logs` and stop an app and its billing with `varity_delete_deployment`.

## Example Usage

### goose Prompt

> Check what it would cost to host this app on Varity, then deploy it and give me the live URL.

goose checks the setup with `varity_doctor`, shows the monthly cost from `varity_cost_calculator`, deploys with `varity_deploy` once you agree, and returns the live URL from `varity_deploy_status`.
