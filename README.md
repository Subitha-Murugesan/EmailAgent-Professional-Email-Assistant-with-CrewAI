# EmailAgent-Professional-Email-Assistant-with-CrewAI
EmailAgent - Professional Email Assistant with CrewAI

EmailAgent is a Python project that leverages CrewAI to help users rewrite rough or informal emails into polished, professional versions. It uses an AI agent with a defined role, goal, and backstory to improve email clarity, tone, and formatting.

### Overview

The EmailAgent project demonstrates how to use CrewAI to create a task-specific agent workflow. In this case, the agent is designed to:

Take rough or informal emails as input.

Rewrite emails in a professional tone with proper formatting.

Expand abbreviations and correct casual language.

CrewAI enables this workflow by defining agents, tasks, and a crew that orchestrates their execution.

----

### Features

Automatically rewrites emails in a professional tone.

Expands abbreviations and improves grammar.

Uses CrewAI for structured AI workflow management.

Verbose logging to monitor agent steps.

----

## Usage

1. Import the required libraries and load environment variables:

```python
from dotenv import load_dotenv
load_dotenv()

from crewai import LLM, Agent, Task, Crew
```

2. Initialize an LLM:

```python
llm = LLM(
    model="gemini/gemini-2.0-flash",
    temperature=0.1
)
```

3. Create the **Email Assistant Agent**:

```python
email_assistant = Agent(
    role="Email Assistant Agent",
    goal="Improve emails and make them sound professional and clear",
    backstory="A highly experienced communication expert skilled in professional email writing",
    verbose=True,
    llm=llm
)
```

4. Define a task for rewriting emails:

```python
original_email = """
hey team, just wanted to tell u that the demo is kind of ready, but there's still stuff left.
Maybe we can show what we have and say rest is WIP.
Let me know what u think. thanks
"""

email_task = Task(
    description=f"""Take the following rough email and rewrite it into a professional and polished version.
    Expand abbreviations:
    '''{original_email}'''""",
    agent=email_assistant,
    expected_output="A professional written email with proper formatting and content."
)
```

5. Create a Crew and run the task:

```python
crew = Crew(
    agents=[email_assistant],
    tasks=[email_task],
    verbose=True
)

result = crew.kickoff()
print("Revised Email:\n", result)
```

---

## How It Works

1. **LLM Initialization** - Defines the AI model and its parameters.
2. **Agent Creation** – Specifies the role, goal, and backstory of the Email Assistant.
3. **Task Definition** – Provides the input email and expected output for the agent.
4. **Crew Execution** – Orchestrates the agent and task workflow using CrewAI.
5. **Result** – Outputs a professionally rewritten email.

This workflow can be extended for multiple agents or different communication tasks.

---

## Dependencies

* `crewai` – Framework for agentic AI workflows
* `python-dotenv` – Loads environment variables from .env files

---
## Output
<img width="1228" height="638" alt="image" src="https://github.com/user-attachments/assets/f2e8cea1-b002-464b-ac19-61198a67bf06" />
<img width="963" height="474" alt="image" src="https://github.com/user-attachments/assets/16401f88-0c50-4192-8836-8db38a3dc0ae" />
<img width="1108" height="528" alt="image" src="https://github.com/user-attachments/assets/c452f66e-a939-49d1-b0d5-d1d06f01d647" />
<img width="1150" height="679" alt="image" src="https://github.com/user-attachments/assets/d2194b5f-88fe-49c3-9cca-282a5b92bfb2" />





Easily adaptable for other communication or writing tasks.
