# Code-Agent

A multi-agent AI system built with LangGraph and LangChain that intelligently routes coding tasks to specialized agents for explanation, problem-solving, and code review.

## Features

- **Router Agent**: Classifies user input into three categories:
  - `explain` - Explain programming concepts
  - `solve` - Solve coding problems
  - `review` - Review and fix code issues

- **Specialized Agents**:
  - **Explain Agent**: Provides simple explanations of programming concepts
  - **Solve Agent**: Generates solutions with explanations for coding problems
  - **Review Agent**: Analyzes code, identifies issues, and suggests fixes
  - **Final Combiner**: Aggregates outputs from all agents

- **LangGraph Integration**: Uses state-based graph workflow for seamless agent chaining

## Prerequisites

- Python 3.8+
- [Ollama](https://ollama.ai/) installed and running with the `llama3:latest` model
- Virtual environment (recommended)

## Installation

1. Clone or download this repository
2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Ensure Ollama is running with llama3:
   ```bash
   ollama run llama3:latest
   ```

## Usage

Open `code-agent.ipynb` in Jupyter and run the cells:

1. **Setup**: Initializes the LLM connection and defines the agent state
2. **Agents**: Defines individual agent functions (router, explain, solve, review)
3. **Build Graph**: Constructs the LangGraph workflow
4. **Run Example**: Execute the agent with sample input

### Example Input

```python
input_data = {
    "user_input": "Check this python code for errors : def add(a,b)  return a - b"
}
result = app.invoke(input_data)
print(result['final_output'])
```

## Project Structure

```
code-agent/
├── code-agent.ipynb      # Main Jupyter notebook with agent implementation
├── requirements.txt      # Python dependencies
├── README.md            # This file
└── .gitignore           # Git ignore patterns
```

## How It Works

1. **Input**: User provides code or a programming question
2. **Routing**: Router agent classifies the input type
3. **Processing**: Input is routed to appropriate agent(s)
4. **Chain**: Review → Solve → Final aggregation
5. **Output**: Final agent combines results and returns comprehensive response

## Dependencies

- `langchain` - LLM integration framework
- `langchain-core` - Core LangChain components
- `langchain-community` - Community integrations
- `langgraph` - State graph library for agent workflows
- `langchain-ollama` - Ollama LLM integration
- `jupyter` - For running the notebook (optional)

## Customization

- **Change LLM Model**: Update the `model` parameter in the LLM setup cell (e.g., `llama2:latest`)
- **Modify Prompts**: Edit the prompt templates in each agent function
- **Add New Agents**: Define new agent functions and add them to the graph
- **Adjust Routing Logic**: Modify the `route_from_router()` function

## Troubleshooting

- **Ollama Connection Error**: Ensure Ollama is running and accessible on localhost:11434
- **Model Not Found**: Download the required model using `ollama pull llama3:latest`
- **Package Errors**: Reinstall dependencies with `pip install --upgrade -r requirements.txt`

## License

This project is open source and available for personal and educational use.
