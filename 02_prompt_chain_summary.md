# File: `02_prompt_chain_summary.md`

```md
# Execution Chain Meta-Prompt (Python Edition) - Summary

**Purpose**:  
Transform the comprehensive plan from `01_planning_output.md` into a series of self-contained coding prompts (and corresponding review prompts) for each task in a Python project.  

**Key Points**:  
1. **One Task at a Time**: Only one task is active (`currently_doing`).  
2. **Execution Prompt**: Tells a separate “coding instance” exactly how to implement the assigned task (setup, context, references, acceptance criteria).  
3. **Review Prompt**: Tells a separate “review instance” or the next step exactly how to review the code just produced (check code quality, tests, coverage).  
4. **Dependencies**: Task must wait for all dependencies to appear in `done`.  
5. **Goal**: Keep the entire coding or review context in a single self-contained prompt, to minimize confusion and ensure thorough coverage.