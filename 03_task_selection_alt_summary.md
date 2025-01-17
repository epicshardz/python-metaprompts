# File: `03_task_selection_alt_summary.md`

```md
# Task Selection Meta-Prompt (Python Edition) - Summary

**Purpose**:  
Analyze the current state of a Python project (tasks completed, reviews done, outstanding tasks) and **select** the most logical next task according to dependencies, priority, and context.

**Key Points**:  
- Input includes the entire project plan plus the current `execution_state`.  
- The meta-prompt decides which task to do next based on dependencies and priority.  
- Generates the usual “execution_prompt” and “review_prompt” for the chosen task.  
- Also tracks any context or environment continuity (libraries, data structures, big decisions) to carry forward.