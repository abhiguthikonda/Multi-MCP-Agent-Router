Multi-MCP Agent Router
A Streamlit app that demonstrates the multi-agent + MCP pattern: specialized AI agents that each connect to different MCP servers to handle domain-specific tasks.

Instead of one agent with all tools, The router sends your request to a specialist — a code reviewer, security auditor, researcher, or BIM engineer — each with access to only the MCP tools they need.

Features
4 Specialized Agents: Code Reviewer, Security Auditor, Researcher, and BIM Engineer
MCP Tool Routing: Each agent connects to different MCP servers (GitHub, filesystem, fetch, etc.)
Agent Selection: Automatic routing based on query type, or manual agent selection
Streaming Responses: Real-time output from Claude via the Anthropic API
Conversation Memory: Per-agent conversation history within a session
Architecture
User Query
    |
    v
[Router] --> Classifies intent
    |
    +-- Code Review  --> GitHub MCP + Filesystem MCP
    +-- Security     --> GitHub MCP + Fetch MCP  
    +-- Research     --> Fetch MCP + Filesystem MCP
    +-- BIM/Revit    --> Custom MCP (named pipes)
Setup
Requirements
Python 3.10+
Anthropic API Key
MCP servers (optional — the app works with or without them)
Installation
Clone this repository:

git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd mcp_ai_agents/multi_mcp_agent_forge
Install dependencies:

pip install -r requirements.txt
Run the app:

streamlit run agent_forge.py
Enter your Anthropic API key in the sidebar and start asking questions.

How It Works
Agent Definitions: Each agent has a name, system prompt, and list of MCP server configs
Router: Classifies the user's query and selects the best agent
MCP Connection: The selected agent connects to its assigned MCP servers
Execution: Claude processes the query with access to the agent's specific tools
Response: Results stream back to the Streamlit UI
