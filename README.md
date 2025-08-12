# Using MCP with OpenWebUI

This repository demonstrates how to integrate Model Context Protocol (MCP) with OpenWebUI to connect to Confluence data through a local LLM server.

## Prerequisites

### 1. LM Studio Setup
You need to have **LM Studio** running locally with an LLM server:

1. Download and install [LM Studio](https://lmstudio.ai/)
2. Load a compatible LLM model in LM Studio
3. Start the local server in LM Studio:
   - Go to the "Local Server" tab
   - Click "Start Server"
   - The server typically runs on `http://localhost:1234/v1`

### 2. OpenWebUI
OpenWebUI will connect to your local LLM server and integrate with the Confluence MCP.

### 3. Environment Configuration
You need to create a `.env` file to provide your Atlassian credentials for Confluence access:

```bash
# Create .env file in the project root
touch .env
```

Add your Atlassian credentials to the `.env` file:
```env
CONFLUENCE_USERNAME=your-email@example.com
CONFLUENCE_API_TOKEN=your-api-token
CONFLUENCE_URL=https://your-domain.atlassian.net
```

**Note**: You can generate an API token from your Atlassian account settings.

## Architecture

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   LM Studio │    │ OpenWebUI   │    │ Confluence  │
│   (Local    │◄──►│             │◄──►│ MCP Server  │
│   LLM)      │    │             │    │             │
└─────────────┘    └─────────────┘    └─────────────┘
```

## Setup Instructions

1. **Start LM Studio Server**
   - Launch LM Studio
   - Load your preferred LLM model
   - Start the local server on port 1234

2. **Configure OpenWebUI**
   - OpenWebUI will connect to your local LLM server
   - Configure the MCP integration for Confluence

3. **Connect to Confluence MCP**
   - The system will connect to Confluence through the MCP server
   - This allows the LLM to access and query Confluence data

## Configuration Files

- `docker-compose.yml` - Docker configuration for the services
- `nginx.conf` - Nginx reverse proxy configuration
- `openwebui-config.json` - OpenWebUI configuration settings

## Usage

Once everything is set up:

1. Ensure LM Studio is running with the local server active
2. Start the OpenWebUI services using Docker Compose
3. Access OpenWebUI through your browser
4. The LLM will be able to access Confluence data through the MCP integration

## Troubleshooting

- **LM Studio not connecting**: Ensure the local server is started and running on the correct port
- **MCP connection issues**: Check that the Confluence MCP server is properly configured
- **OpenWebUI errors**: Verify the configuration in `openwebui-config.json`

## Requirements

- LM Studio with a compatible LLM model
- Docker and Docker Compose
- Access to Confluence (for MCP integration)
- Network connectivity for MCP server communication