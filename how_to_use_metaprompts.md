# How to Use These Meta-Prompts (Python Edition)

## Overview

You have a collection of **meta-prompts** designed to guide a Large Language Model (LLM)—or a set of LLMs—through:

1. **Planning a Python Project** (`01_planning.md`).
2. **Generating a Detailed Plan** (see `01_planning_output.md` for an example of the final plan).
3. **Breaking the Plan into Actionable Tasks** (`02_prompt_chain.md`).
4. **Selecting and Queuing Tasks** (`03_task_selection_alt.md`, if you want an advanced approach).
5. **Generating Coding Prompts** and **Review Prompts** to be executed in separate LLM sessions (or “instances”).

---

## Step-by-Step Instructions

1. **Start with `01_planning.md`.**  
   - Copy its content into your LLM (we’ll call this the “META INSTANCE”).  
   - Insert or describe your **User Input** about the Python project you want to build.  
   - The LLM will produce a detailed plan similar to `01_planning_output.md`.

2. **Review the Plan.**  
   - If changes are needed, keep iterating in the META INSTANCE.  
   - Ensure all components, tasks, constraints, and acceptance criteria are correct and thorough.

3. **Add `02_prompt_chain.md`.**  
   - This meta-prompt tells the LLM how to convert your finalized plan into “execution prompts” and “review prompts.”  
   - The LLM’s output will look something like `02_prompt_chain_output.md`, showing a YAML structure of tasks to do.

4. **Open a Fresh LLM Session (the CODING INSTANCE).**  
   - Copy the **execution prompt** from the YAML (generated in step 3) and paste it into this new CODING INSTANCE.  
   - Because the coding prompt is fully self-contained, the new LLM (or coding environment) doesn’t need the entire plan’s context, just the prompt.  
   - Let the CODING INSTANCE proceed with implementation details, generate code, discuss improvements, etc.

5. **Implement & Review.**  
   - When the code is done (by the LLM or by you), produce a quick summary or final output.  
   - Go back to the META INSTANCE, mark the task as “done,” and generate the **review prompt**.  
   - If the review passes, move on to the next task. If not, iterate until it meets acceptance criteria.

6. **Task Selection (Optional Advanced).**  
   - If you want to dynamically pick tasks rather than going in a fixed order, you can use `03_task_selection_alt.md`.  
   - This meta-prompt looks at your project’s current state, sees which tasks are done or blocked, and picks the next best task automatically.

7. **Repeat Until Done.**  
   - Continue this cycle—generate coding prompt, implement, review—until all tasks from `01_planning.md` are finished.  
   - That’s when you’ll have a working Python project.

---

## FAQ

**Q: Do I need all these files for a simple project?**  
A: No, you can remove or merge them. They’re mainly for larger or more structured projects.

**Q: Why separate the “META INSTANCE” from the “CODING INSTANCE”?**  
A: Coding LLMs often have limited context windows or get “bogged down” with big instructions. By isolating each coding prompt into a self-contained block, you keep the process clear and reduce confusion. The META INSTANCE retains the high-level plan, while the CODING INSTANCE focuses on one task at a time.

**Q: What if the LLM makes mistakes regarding library versions or Python commands?**  
A: Communicate and correct them. In real software projects, changes and fixes happen constantly. LLMs speed up coding but aren’t omniscient. Iterate until the code meets your standards.

---

## Final Note

These meta-prompts are flexible guidelines. Adapt them to your favorite Python workflow—whether that’s Poetry, pipenv, or standard pip; Click, Typer, or argparse; library, CLI, or web service. The fundamental idea remains:

1. **Plan thoroughly**  
2. **Break tasks down**  
3. **Generate self-contained coding prompts**  
4. **Review systematically**  

This ensures a smoother, more maintainable development cycle for your Python projects.
