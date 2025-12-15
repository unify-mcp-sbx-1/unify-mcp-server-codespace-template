# CloudBees Unify MCP Server - Codespace Template

This is a GitHub Codespaces template that automatically configures the CloudBees Unify MCP server for use with GitHub Copilot.

## Prerequisites

Before using this template, you need to configure the following secrets in your GitHub repository or organization:

### Required Secrets

1. **CLOUDBEES_PERSONAL_ACCESS_TOKEN**
   - Your CloudBees personal access token
   - Used to authenticate with CloudBees Unify

2. **ORGANIZATION_ID**
   - Your CloudBees Unify organization ID
   - Used to identify which organization to connect to

## Setting Up Secrets

### For Repository/Organization Secrets
1. Go to your repository or organization on GitHub
2. Navigate to **Settings** > **Secrets and variables** > **Codespaces**
3. Click **New repository secret** (or **New organization secret**)
4. Add both `CLOUDBEES_PERSONAL_ACCESS_TOKEN` and `ORGANIZATION_ID`

### For User Secrets (applies to all your Codespaces)
1. Go to your GitHub settings: https://github.com/settings/codespaces
2. Under **Codespaces secrets**, click **New secret**
3. Add both secrets with the appropriate values

## Usage

### Starting a Codespace

1. Click the **Code** button on the repository
2. Select the **Codespaces** tab
3. Click **Create codespace on main**

The devcontainer will automatically:
- Install Docker
- Pull the CloudBees Unify MCP server Docker image
- Configure the MCP server for GitHub Copilot

### Using the MCP Server with GitHub Copilot

Once your Codespace is running, the CloudBees Unify MCP server is automatically available to GitHub Copilot. Simply use Copilot Chat and ask questions related to CloudBees workflows, pipelines, or other CloudBees Unify capabilities.

**How it works:**
- GitHub Copilot automatically detects the MCP server configuration
- When you ask CloudBees-related questions, Copilot invokes the MCP server on-demand
- The server provides tools and context to help Copilot answer your questions

## Configuration

The MCP server configuration is defined in [.devcontainer/devcontainer.json](.devcontainer/devcontainer.json) under `customizations.vscode.mcp`.

**Current configuration:**
- **Server**: cloudbees-unify
- **Mode**: unify
- **Transport**: stdio (via Docker)
- **Container**: `cloudbees/unify-mcp-server:latest`

To modify the configuration, edit the `mcp.servers` section in the devcontainer.json file.

## Troubleshooting

### Secrets Not Available
If the secrets are not available in your Codespace:
1. Verify they are set correctly in your repository, organization, or user settings
2. Restart the Codespace
3. Check that the secret names match exactly (case-sensitive)

### MCP Server Not Working
If GitHub Copilot isn't using the MCP server:
1. Ensure you have GitHub Copilot Chat enabled
2. Check that the devcontainer was properly created
3. Try asking specific CloudBees-related questions to trigger the MCP server
