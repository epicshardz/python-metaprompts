# Example Python Coding Prompt

Below is an example prompt you might give to a fresh “coding instance” (a separate LLM or environment) to implement a specific Python task.

---

PROJECT SETUP:
--------------
1. Create or navigate to the project directory (e.g., "csvinsight").
2. Ensure Python 3.9+ is installed. Optionally create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
Install required libraries:
bash
Copy
pip install pandas numpy openai typer
CONTEXT:
We are implementing a function to integrate AI-based summarization of CSV stats. The CSV profiling is already complete; we just need to feed that data to OpenAI’s API (or a mock function if no API key is provided).

TECHNICAL REQUIREMENTS:
A new module: csvinsight/ai_insights.py
A function: generate_insights(profile: dict) -> str
If OPENAI_API_KEY is set, call the OpenAI API; otherwise, return a mock string.
Handle large or complex summaries by chunking or summarizing top-level stats first.
IMPLEMENTATION DETAILS:
Create ai_insights.py with generate_insights(profile):
Load os.environ.get("OPENAI_API_KEY").
If absent, return a default string: "AI summary unavailable."
If present, build a prompt from the profile dict, call the OpenAI API, parse the response.
Write test_ai_insights.py in tests/ with at least two tests:
One with an empty/mocked API key (should get "AI summary unavailable.")
One with a fake or real key to ensure the function can be called (mock the response if needed).
QUALITY REQUIREMENTS:
Follow PEP8
Provide docstrings
80%+ coverage on new code
No external logs or secrets in code
EXPECTED OUTPUT:
csvinsight/ai_insights.py with a functioning generate_insights function
tests/test_ai_insights.py containing test cases
ACCEPTANCE CRITERIA:
Code runs without error
If OPENAI_API_KEY is missing, fallback message is returned
If OPENAI_API_KEY is present, a stub or real AI call is made
Tests pass (mock the AI call if real credentials aren’t available)
yaml
Copy

---

# File: `how_to_use_metaprompts.md`

```md
# How to Use These Meta-Prompts (Python Edition)

## Overview

You have a collection of **meta-prompts** designed to guide a Large Language Model (LLM) (or set of LLMs) through:

1. **Planning a Python Project** (`01_planning.md`).
2. **Generating a Detailed Plan** (`01_planning_output.md` is an example of the final plan).
3. **Breaking the Plan into Actionable Tasks** (`02_prompt_chain.md`).
4. **Selecting and Queuing Tasks** (`03_task_selection_alt.md`, optional advanced approach).
5. **Generating Coding Prompts** and **Review Prompts** to be executed in separate LLM sessions or “instances.”

---

## Step-by-Step Instructions

1. **Start with `01_planning.md`.**  
   - Copy its content into your LLM (we call this the “META INSTANCE”).
   - Paste or write your **User Input** about the Python project you want to build.  
   - The LLM will produce a detailed plan (like `01_planning_output.md`).

2. **Review the Plan.**  
   - If you have any changes, continue iterating in the META INSTANCE.  
   - Make sure you have all the components, tasks, and constraints you want.

3. **Add `02_prompt_chain.md`.**  
   - This meta-prompt tells the LLM how to convert the plan into “execution prompts” (coding tasks) and “review prompts.”  
   - The LLM may produce an output similar to `02_prompt_chain_output.md`.

4. **Open a Fresh LLM Session (CODING INSTANCE).**  
   - Take the **execution prompt** from step 3 and paste it into this new instance.  
   - Because these coding prompts are fully self-contained, the new LLM can implement the task without needing the entire plan context.

5. **Implement and Review.**  
   - Once the code is done (by you or the LLM), you can produce a short summary or report.  
   - Then you return to the META INSTANCE, mark the task as done, generate the next coding prompt and review prompt.  

6. **Task Selection (Optional Advanced).**  
   - If you need a more dynamic approach to picking the next task, use `03_task_selection_alt.md`.  
   - This meta-prompt looks at the project state, sees which tasks are done or blocked, and outputs the next best task.

7. **Iterate Until Complete.**  
   - Keep going until all tasks in the plan are done.  
   - Celebrate your completed Python project!

---

## FAQ

**Q: Do I need all these files for a simple Python script?**  
A: No, you can remove or merge them. They’re most useful for bigger projects.

**Q: Why use separate LLM instances?**  
A: “Coding Instances” often have limited context windows and can be “bogged down” by too much extraneous info. Using a separate “META INSTANCE” ensures the high-level plan remains intact, while each coding prompt includes just enough context to do the job.

**Q: What if the LLM makes a mistake about a library version or a Python command?**  
A: Communicate with it. Provide clarifications. Real projects always require iteration. LLMs are fast but not omniscient.

---

## Final Note

These meta-prompts are flexible guidelines. Adapt them for your own style, whether you prefer Poetry, pipenv, or raw pip; whether you want Typer, Click, or just Argparse; whether you’re building a pure library, a CLI, or a web service. The core idea remains: **plan thoroughly, break tasks down, generate self-contained coding prompts, and review systematically** for a successful Python project.