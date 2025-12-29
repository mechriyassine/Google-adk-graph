# TalentGraph - HR Knowledge Graph

TalentGraph is an intelligent HR knowledge graph application built with [Graphiti](https://github.com/getzep/graphiti), [FalkorDB](https://falkordb.com/), and [Google Gemini](https://deepmind.google/technologies/gemini/). It models an organizational structure (employees, teams, projects, skills) and provides an AI agent to query and update this information using natural language.

## 🚀 Features

- **HR Knowledge Graph**: Realistic organizational modeling including reporting structures, project assignments, skills, and compliance requirements.
- **AI-Powered Ingestion**: automatically processes text descriptions of organizational changes into graph nodes and edges.
- **Intelligent HR Agent**: A conversational agent that can:
  - Answer complex queries about the organization (e.g., "Who reports to Bob?", "Find Kubernetes experts").
  - Add new information to the graph (e.g., "John was promoted to Senior Engineer").
  - Maintain temporal awareness of changes (validity periods, historical data).
- **Hybrid Search**: Combines semantic search with graph traversal for accurate retrieval.

## 🛠️ Prerequisites

- Python 3.10+
- [FalkorDB](https://falkordb.com/) (running locally or via Docker)
- Google AI Studio API Key (for Gemini models)

## 📦 Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/mechriyassine/Google-adk-graph.git
    cd Google-adk-graph
    ```

2.  **Create and activate a virtual environment:**

    ```bash
    python -m venv .venv
    # Windows
    .venv\Scripts\activate
    # macOS/Linux
    source .venv/bin/activate
    ```

3.  **Install dependencies:**

    ```bash
    pip install -r requirement.txt
    ```

4.  **Set up environment variables:**
    Copy `.env.example` to `.env` (if available) or create a `.env` file with:
    ```ini
    GOOGLE_API_KEY=your_google_api_key_here
    FALKORDB_HOST=localhost
    FALKORDB_PORT=6379
    ```

## 🏃 Usage

### 1. Start FalkorDB

Ensure FalkorDB is running. If using Docker:

```bash
docker run -p 6379:6379 -it --rm falkordb/falkordb
```

### 2. Initialize the Knowledge Graph

Run the setup script to populate the graph with sample data for "TechNova":

```bash
python setup_hr_graph.py
```

This will create employees, teams, and projects in the graph.

### 3. Run the HR Agent

The agent is defined in `hr_agent/agent.py` using the Google ADK framework. You can integrate this agent into your ADK application or run it using an ADK runner.

### 4. Tests

Run the Graphiti test script to verify basic functionality:

```bash
python graphiti-test.py
```

## 📂 Project Structure

- `setup_hr_graph.py`: Script to initialize the HR knowledge graph with sample data.
- `hr_agent/`: Contains the AI agent definition.
  - `agent.py`: Defines the ADK agent and tools for adding/searching HR info.
- `graphiti-test.py`: detailed usage examples and tests for Graphiti and FalkorDB.
- `requirement.txt`: Project dependencies.
