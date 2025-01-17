# File: `02_prompt_chain_output.md`

```md
```yaml
execution_state:
  done: []
  done_reviews: []

  currently_doing:
    task_id: "TASK-001"
    execution_prompt: |
      PROJECT SETUP:
      -------------
      1. Create a new folder “csvinsight” if not already present.
      2. Make sure you have Python 3.9+ and pip installed. Optionally create a virtualenv.
      3. Install dependencies:
         pip install pandas numpy --upgrade

      CONTEXT:
      --------
      We are implementing TASK-001: the CSVLoader component. It should handle reading CSV files, possibly in chunks, and return an iterator or list of DataFrames.

      TECHNICAL REQUIREMENTS:
      -----------------------
      - The function signature: load_csv(path: str, chunk_size: int = 10000) -> Iterator[pd.DataFrame]
      - Must handle large CSVs in chunks if chunk_size > 0
      - Raise an exception or handle errors for invalid files

      IMPLEMENTATION DETAILS:
      -----------------------
      1. Create a file csvinsight/csv_loader.py
      2. Define load_csv(...) inside it.
      3. Use pandas.read_csv with chunk_size (if chunk_size is set).
      4. Yield data frames from the iterator. If chunk_size is None or 0, read the entire file at once.

      QUALITY REQUIREMENTS:
      ---------------------
      - Write unit tests in tests/test_csv_loader.py
      - Ensure coverage for large and small CSV
      - Conform to PEP8 standards

      EXPECTED OUTPUT:
      ----------------
      - A csv_loader.py with a functioning load_csv function
      - Tests that pass for both small and large CSVs

      ACCEPTANCE CRITERIA:
      --------------------
      - The function can load small CSVs fully
      - The function can chunk large CSVs
      - Proper error handling if file not found or invalid
      - 80% or higher test coverage in test_csv_loader

  pending_review:
    task_id: "TASK-001"
    review_prompt: |
      CONTEXT:
      --------
      We’re reviewing TASK-001, which implemented csv_loader.py.

      REVIEW CRITERIA:
      ----------------
      1. Code Quality: PEP8 compliance, clarity, docstrings.
      2. Functionality: load_csv properly loads or chunks CSV files.
      3. Error Handling: invalid path, corrupt CSV, edge cases.
      4. Testing: do tests cover large/small files? Are all tests passing?
      5. Performance: chunking should handle large files in a memory-friendly way.

      EXPECTED REVIEW OUTPUT:
      -----------------------
      - Approval status: "APPROVED" or "REQUEST_CHANGES"
      - Detailed feedback on code, any improvements or bug findings
      - If changes are requested, specify steps to fix them

      ACCEPTANCE CRITERIA:
      --------------------
      - Code meets the above quality & testing standards
      - No major logic or performance issues
