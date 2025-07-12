# LangGraph Agents + MCP


## Project Overview


`LangChain-MCP-Adapters` is a toolkit provided by **LangChain AI** that enables AI agents to interact with external tools and data sources through the Model Context Protocol (MCP). This project provides a user-friendly interface for deploying ReAct agents that can access various data sources and APIs through MCP tools.

### Features

- **Streamlit Interface**: A user-friendly web interface for interacting with LangGraph `ReAct Agent` with MCP tools
- **Tool Management**: Add, remove, and configure MCP tools through the UI (Smithery JSON format supported). This is done dynamically without restarting the application
- **Streaming Responses**: View agent responses and tool calls in real-time
- **Conversation History**: Track and manage conversations with the agent

## MCP Architecture

The Model Context Protocol (MCP) consists of three main components:

1. **MCP Host**: Programs seeking to access data through MCP, such as Claude Desktop, IDEs, or LangChain/LangGraph.

2. **MCP Client**: A protocol client that maintains a 1:1 connection with the server, acting as an intermediary between the host and server.

3. **MCP Server**: A lightweight program that exposes specific functionalities through a standardized model context protocol, serving as the primary data source.


## Software Installation Prior to using the Source Code

1. Verify Python version: MCP python librray library requires Python 3.10+ (with 3.12 recommended). The MCP Python REPL Server requires Python 3.11+. Please make sure to update the underlying Python version.

2. Install VS code community edition to navigate the codebase & edit.
https://code.visualstudio.com/docs/setup/setup-overview


## Using Source Code

1. Clone this repository

```bash
git clone 
cd langgraph-mcp-agents
```

2. Create a virtual environment and install dependencies.

```bash
# create virtual enviornment replace the content $$
python -m venv $virtual_env_name$
# Unix/ MAC
source $virtual_env_name$/bin/activate
# Windows
$virtual_env_name$\Scripts\activate
#Install the libraries
pip install -r requirements.txt
# If require to deactivate the virtual enviornment
deactivate
```

3. Create a `.env` file with your API keys (copy from `.env.example`)

```bash
cp .env.example .env
```

Enter your obtained API keys in the `.env` file.

(Note) Not all API keys are required. Only enter the ones you need.
- `ANTHROPIC_API_KEY`: If you enter an Anthropic API key, you can use "claude-3-7-sonnet-latest", "claude-3-5-sonnet-latest", "claude-3-haiku-latest" models.
- `OPENAI_API_KEY`: If you enter an OpenAI API key, you can use "gpt-4o", "gpt-4o-mini" models.
- `LANGSMITH_API_KEY`: If you enter a LangSmith API key, you can use LangSmith tracing.
```bash
ANTHROPIC_API_KEY=your_anthropic_api_key
OPENAI_API_KEY=your_openai_api_key
LANGSMITH_API_KEY=your_langsmith_api_key
LANGSMITH_TRACING=true
LANGSMITH_ENDPOINT=https://api.smith.langchain.com
LANGSMITH_PROJECT=LangGraph-MCP-Agents
```

4. (New) Use the login/logout feature

When using the login feature, set `USE_LOGIN` to `true` and enter `USER_ID` and `USER_PASSWORD`.

```bash
USE_LOGIN=true
USER_ID=admin
USER_PASSWORD=admin123
```

If you don't want to use the login feature, set `USE_LOGIN` to `false`.

```bash
USE_LOGIN=false
```

## Usage

1. Start the Streamlit application.

```bash
streamlit run app.py
```

2. The application will run in the browser and display the main interface.

![example execution](./assets/app_launch.PNG)

3.  One way to configure MCP tools is to use the sidebar. However we will build MCP tools ourselves following the steps mentioned in the section above.

4. Apply the agent's settings.

![check status](./assets/apply_setting.PNG)

5. It will take few moments to get the agent's settings applied.

![check status](./assets/settings_geting_applied.PNG)

6. Interact with the ReAct agent that utilizes the configured MCP tools by asking questions in the chat interface.

![project demo](./assets/ready_to_chat.PNG)




## References

- https://github.com/langchain-ai/langchain-mcp-adapters
