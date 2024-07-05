# llm-movieagent

This project is designed to implement an agent capable of interacting with a graph database like Neo4j through a semantic layer using OpenAI function calling.
The semantic layer equips the agent with a suite of robust tools, allowing it to interact with the graph database based on the user's intent.

![Workflow diagram](https://raw.githubusercontent.com/tomasonjo/llm-moaz acr login --name <acrName>az acr login --name <acrName>vieagent/main/api/packages/neo4j-semantic-layer/static/workflow.png)

To start the project, run the following command:

```
docker-compose up
```

Open `http://localhost:8501` in your browser to interact with the agent.

## Tools

The agent utilizes several tools to interact with the Neo4j graph database effectively:

1. **Information tool**:
   - Retrieves data about movies or individuals, ensuring the agent has access to the latest and most relevant information.
2. **Recommendation Tool**:
   - Provides movie recommendations based upon user preferences and input.
3. **Memory Tool**:
   - Stores information about user preferences in the knowledge graph, allowing for a personalized experience over multiple interactions.

## Environment Setup

You need to define the following environment variables in the `.env` file.

```
OPENAI_API_KEY=<YOUR_OPENAI_API_KEY>
NEO4J_URI=<YOUR_NEO4J_URI>
NEO4J_USERNAME=<YOUR_NEO4J_USERNAME>
NEO4J_PASSWORD=<YOUR_NEO4J_PASSWORD>
```

## Docker containers

This project contains the following services wrapped as docker containers

1. **Neo4j**:
   - Neo4j, a graph database, is used to store the information about actors, movies, and their ratings.
2. **API**:
   - Uses LangChain's `neo4j-semantic-layer` template to implement the OpenAI LLM and function calling capabilities.
3. **UI**:
   - Simple streamlit chat user interface. Available on `localhost:8501`.

## Populating with data

If you want to populate the DB with an example movie dataset, you can run `python ingest.py`.
The script import information about movies and their rating by users.
Additionally, the script creates two [fulltext indices](https://neo4j.com/docs/cypher-manual/current/indexes-for-full-text-search/), which are used to map information from user input to the database.
The dataset is based on the MovieLens dataset, which is also available as the `Recommendation` project in [Neo4j Sandbox](https://sandbox.neo4j.com/?usecase=recommendations).

## Contributions

Contributions are welcomed!