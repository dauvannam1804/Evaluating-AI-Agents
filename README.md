# Evaluating AI Agents - Course Summary

This repository contains the labs for the "Evaluating AI Agents" course. The course teaches how to build, trace, and systematically evaluate an AI agent designed to assist store owners with sales data analysis.

## Course Overview

The project builds an agent equipped with a **Router** and three specific **Tools**:
1.  **Database Lookup**: Converts natural language to SQL to query a local database.
2.  **Data Analysis**: Analyzes retrieved data to extract insights.
3.  **Data Visualization**: Generates Python code to create charts and graphs.

The course progresses from building the agent to implementing comprehensive evaluation strategies using **Phoenix** (an AI observability platform).

## Lab Summaries

### [Lab 1: Building your Agent](Lab1.ipynb)
**Goal:** Build the core functional agent.
- Defined the three tools:
    - `lookup_sales_data`: SQL generation and execution.
    - `analyze_sales_data`: LLM-based insight extraction.
    - `generate_visualization`: Python code generation for plotting.
- Implemented the **Router** using OpenAI function calling to orchestrate tool usage.
- Created the main agent loop to handle user queries and tool outputs.

### [Lab 2: Tracing your Agent](Lab2.ipynb)
**Goal:** Add observability to understand agent execution.
- Integrated **Phoenix** for tracing.
- Used `OpenAIInstrumentor` for automatic tracing of LLM calls.
- Added manual instrumentation (Spans) for Tools and Chains to visualize the full execution flow.
- Learned to inspect traces in the Phoenix UI to debug and understand agent behavior.

### [Lab 3: Adding Router & Skill Evaluations](Lab3.ipynb)
**Goal:** Evaluate individual components (Unit Testing).
- **Router Eval**: Used "LLM-as-a-judge" to verify if the router selects the correct tool and extracts correct parameters.
- **SQL Eval**: Evaluated the correctness of generated SQL queries.
- **Analysis Eval**: Assessed the clarity of the generated text analysis.
- **Code Eval**: Verified if the generated visualization code is runnable.

### [Lab 4: Adding Trajectory Evaluations](Lab4.ipynb)
**Goal:** Evaluate the efficiency of the agent's execution path.
- Introduced **Convergence Score** to measure path efficiency.
- Created a dataset with variations of questions to test robustness.
- Ran experiments to track the "Path Length" (number of steps) and compared it to the optimal path.

### [Lab 5: Adding Structure to your Evaluations](Lab5.ipynb)
**Goal:** Run comprehensive, structured experiments.
- Combined all evaluators into a unified **Phoenix Experiment**.
- Ran the agent against a larger dataset of test questions.
- Applied multiple metrics simultaneously: Function Calling Accuracy, SQL Correctness, Response Clarity, Entity Correctness, and Code Runnability.
- Demonstrated an iteration loop: Modifying the prompt (e.g., for SQL generation) and re-running experiments to measure improvement.
