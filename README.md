# Multi-Agent Decision System

A professional multi-agent AI application that analyzes real-life conflict scenarios using multiple reasoning frameworks, then synthesizes them into one balanced and actionable recommendation.

The system is built with **Groq API**, **LLaMA 3.3 70B**, and **Gradio**. It demonstrates how multiple specialized AI agents can collaborate to provide deeper, less biased, and more practical decision support than a single-agent response.

---

## Overview

This project implements a **Multi-Agent AI Decision Support System** where several AI agents analyze the same human conflict scenario from different perspectives.

Each agent is inspired by a well-known book and represents a distinct reasoning style:

1. **The Art of Thinking Clearly** — detects cognitive biases and logical fallacies.
2. **Crucial Conversations** — provides communication strategies for high-stakes conversations.
3. **Man's Search for Meaning** — explores values, responsibility, and personal meaning.

After the agents complete their independent analyses, a **Synthesizer Agent** combines their outputs into a unified final recommendation.

---

## Key Features

- Multi-agent reasoning pipeline
- Three book-inspired expert agents
- Final synthesis stage for balanced recommendations
- Single-agent vs multi-agent comparison
- Built-in real-life conflict scenarios
- Custom scenario input support
- Interactive Gradio web interface
- Groq API integration using `llama-3.3-70b-versatile`
- Retry handling for API rate limits
- Clear, structured output for easier interpretation

---

## System Architecture

```text
User Scenario
      |
      |---> Agent 1: Logical Fallacy Detective
      |---> Agent 2: High-Stakes Dialogue Coach
      |---> Agent 3: Existential Perspective Guide
                     |
                     v
              Synthesizer Agent
                     |
                     v
          Final Recommendation
```

The architecture follows an **independent processing + synthesis** pattern:

1. The same scenario is sent to all agents.
2. Each agent responds using its own reasoning framework.
3. The synthesizer reads all responses.
4. The synthesizer produces a practical final recommendation.

---

## Agent Design

| Agent | Inspired By | Persona | Main Purpose |
|---|---|---|---|
| Agent 1 | *The Art of Thinking Clearly* by Rolf Dobelli | Logical Fallacy Detective | Identifies thinking errors, cognitive biases, and distorted assumptions. |
| Agent 2 | *Crucial Conversations* by Patterson, Grenny, McMillan, and Switzler | High-Stakes Dialogue Coach | Helps the user communicate effectively in emotionally sensitive situations. |
| Agent 3 | *Man's Search for Meaning* by Viktor Frankl | Existential Perspective Guide | Connects the decision to values, responsibility, and personal growth. |
| Synthesizer | Neutral reasoning layer | Wise Advisor | Combines all agent outputs into one clear recommendation. |

---

## How It Works

### 1. User Provides a Scenario

The user either selects a preset scenario or writes a custom one.

Example:

```text
My close friend feels ignored because I have been too busy to reply. I became defensive and now she stopped talking to me. What should I do?
```

### 2. Each Agent Analyzes the Scenario

The system sends the same scenario to each agent with a different system prompt.

Each agent produces a structured response based on its assigned reasoning style.

### 3. Synthesizer Combines the Responses

The synthesizer reviews all agent outputs and produces:

- Common themes
- Unique insights
- Resolved contradictions
- Final actionable recommendation

### 4. System Compares Single-Agent and Multi-Agent Outputs

The notebook also runs a single-agent baseline and compares it with the multi-agent result in terms of:

- Depth
- Bias
- Practicality
- Blind spots
- Overall verdict

---

## Project Structure

```text
Multi_Agent.ipynb
README.md
```

Main notebook sections:

```text
Step 1  - Install Dependencies
Step 2  - API Key Setup
Task 1  - Real-Life Scenarios
Task 2  - Book-Based Agent Definitions
Task 3  - Multi-Agent Pipeline
Task 4  - Experiment and Compare
Task 4  - Interactive Gradio App
```

---

## Requirements

The notebook requires the following Python packages:

```bash
pip install groq gradio
```

Main technologies:

- Python
- Google Colab
- Groq API
- LLaMA 3.3 70B Versatile
- Gradio

---

## Setup Instructions

### 1. Open the Notebook in Google Colab

Upload or open `Multi_Agent.ipynb` in Google Colab.

### 2. Add Your Groq API Key

In Google Colab:

1. Open the left sidebar.
2. Click the key icon.
3. Click **Add new secret**.
4. Set the secret name as:

```text
GROQ_API_KEY
```

5. Paste your Groq API key as the value.
6. Enable notebook access.

### 3. Install Dependencies

Run the dependency cell:

```python
!pip install groq gradio -q
```

### 4. Initialize the Groq Client

The notebook reads the API key using:

```python
from google.colab import userdata
from groq import Groq

api_key = userdata.get("GROQ_API_KEY")
client = Groq(api_key=api_key)
MODEL = "llama-3.3-70b-versatile"
```

---

## Running the Notebook

Run the notebook cells in order:

1. Install dependencies.
2. Set up the Groq API client.
3. Load the predefined scenarios.
4. Define the agents.
5. Run the multi-agent pipeline.
6. Compare single-agent and multi-agent outputs.
7. Launch the Gradio app.

---

## Using the Gradio Interface

The notebook includes an interactive Gradio app.

Users can:

- Select a preset scenario.
- Type their own scenario.
- Run multi-agent analysis.
- View single-agent output.
- Compare both outputs.

To launch the app, run:

```python
app.launch(share=True)
```

Gradio will generate a public shareable link for testing and demonstration.

---

## Example Scenarios

The notebook includes three built-in scenarios:

1. **Fight with a Friend**  
   A conflict caused by poor communication, defensiveness, and emotional misunderstanding.

2. **Disagreement with a Professor**  
   A student wants to challenge unclear grading feedback without damaging the relationship.

3. **Misunderstanding with a Partner**  
   A couple struggles with household chores, fairness, appreciation, and repeated blame cycles.

Users can also enter their own custom scenario.

---

## Output Format

### Multi-Agent Output

The multi-agent output includes:

```text
Agent 1 Analysis
Agent 2 Analysis
Agent 3 Analysis
Synthesized Final Recommendation
```

### Synthesizer Output

The synthesizer follows this structure:

```text
COMMON THEMES:
- Shared insights across all agents

UNIQUE INSIGHTS:
- Special contribution from each agent

FINAL RECOMMENDATION:
- Clear, practical advice the user can follow immediately
```

---

## Single-Agent vs Multi-Agent Comparison

The notebook compares a single-agent baseline against the full multi-agent system.

The comparison focuses on:

| Criteria | Description |
|---|---|
| Depth | Whether the answer explores the problem from multiple layers. |
| Bias | Whether the answer avoids over-relying on one perspective. |
| Practicality | Whether the answer gives actions the user can apply. |
| Blind Spots | What the single-agent or multi-agent system may miss. |
| Verdict | Which approach gives the stronger decision-support output. |

The purpose of this comparison is to show that multi-agent systems can produce richer and more balanced answers than a single generalized response.

---

## Customization

You can customize the project by adding more agents, scenarios, or output formats.

### Add a New Agent

Add a new entry to the `AGENTS` dictionary:

```python
AGENTS["New Agent Name"] = {
    "persona": "Agent Persona",
    "reasoning_style": "Description of how this agent thinks.",
    "system_prompt": "Detailed instructions for the agent."
}
```

### Add a New Scenario

Add a new entry to the `SCENARIOS` dictionary:

```python
SCENARIOS["Scenario 4: New Scenario"] = """
Write the scenario here.
"""
```

### Change the Model

Update the model variable:

```python
MODEL = "llama-3.3-70b-versatile"
```

You can replace it with another Groq-supported model if needed.

---

## Troubleshooting

### API Key Not Found

Make sure the Colab secret is named exactly:

```text
GROQ_API_KEY
```

Also confirm that notebook access is enabled.

### Rate Limit Errors

The notebook includes retry logic for rate limits. If the API limit is reached, the system waits and retries automatically.

### Gradio Link Does Not Open

Try rerunning the Gradio launch cell:

```python
app.launch(share=True)
```

If the issue continues, restart the Colab runtime and run the notebook again.

### Empty Output

Check that:

- The Groq API key is valid.
- The selected scenario is not empty.
- The model name is correct.
- Internet access is available in the Colab runtime.

---

## Limitations

- The system depends on external API availability.
- Outputs may vary between runs because LLM responses are probabilistic.
- The agents provide decision-support guidance, not professional therapy, legal advice, or medical advice.
- The quality of the output depends heavily on the clarity of the input scenario.
- The book-inspired agents are simplified reasoning personas, not full replacements for reading the original books.

---

## Future Improvements

Possible future upgrades include:

- Add more expert agents from additional books or domains.
- Add memory across user sessions.
- Store analysis history in a database.
- Add scoring metrics for agent quality.
- Add user feedback to improve recommendations.
- Export results as PDF or Markdown.
- Deploy the app permanently using Hugging Face Spaces, Streamlit Cloud, or another hosting platform.

---

## Educational Value

This project is useful for learning:

- Multi-agent AI architecture
- Prompt engineering
- LLM-based reasoning systems
- AI decision-support design
- Human-centered AI applications
- Gradio-based interface development
- Comparative evaluation between single-agent and multi-agent outputs

---

## License

This project is intended for educational and research purposes. You may modify and extend it according to your own academic or development needs.

---

## Acknowledgements

This project is inspired by reasoning frameworks from:

- *The Art of Thinking Clearly* by Rolf Dobelli
- *Crucial Conversations* by Kerry Patterson, Joseph Grenny, Ron McMillan, and Al Switzler
- *Man's Search for Meaning* by Viktor Frankl

The implementation uses Groq API, LLaMA 3.3 70B, and Gradio.
