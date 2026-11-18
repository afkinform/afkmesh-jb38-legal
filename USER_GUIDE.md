# Notebook Repro Guard
Can your saved notebook reproduce its outputs in a fresh Python kernel? JB38 inspects local format-4 notebooks in a PyCharm tool window.
## Install and inspect
Install the distribution ZIP using Settings → Plugins → gear → Install Plugin from Disk. Open a project and choose View → Tool Windows → Notebook Repro Guard. Choose a notebook and a trusted Python executable with nbformat. Click Inspect notebook. Missing or non-increasing counts indicate cells to investigate.
## Clean replay
Activate a separate Notebook Repro Guard trial or Pro license in the JetBrains license manager. Choose a Python interpreter with nbformat, nbclient and ipykernel. Set the per-cell timeout. Leave the ignore field empty for exact comparison. To ignore volatile top-level JSON fields, enter their literal names separated by commas. Time, seed and numeric differences are preserved by default.
Review the working directory, output location and exact arguments before confirming. The kernel runs with your account permissions. Notebook code can read or change files and contact external services. Use trusted notebooks and environments. The worker launches the selected interpreter and clears code outputs on a separate in-memory copy before running cells in file order. The notebook's parent is the working directory.
## Review results
Each replay writes executed.ipynb and report.json to a unique folder under ~/NotebookReproGuard. Changed cells include the saved and reproduced values. The report records the Python version, local packages, cwd, input hash and declared inputs or seed. Undeclared dependencies and dynamic seeds can remain unknown. Cancel replay shuts down the kernel started for this run and saves partial progress.
Supported comparisons cover stdout/stderr, text/plain, application/json and application/vnd.dataresource+json tabular output. Printed tables compare as text. HTML, widgets and images appear as unsupported. A match applies only to the recorded run and covered output.
## Try the demo
Replay examples/seeded.ipynb for a fixed-seed match. Inspect examples/out-of-order.ipynb to see a correct replay despite nonmonotonic counts. Replay examples/hidden-state.ipynb for a saved result that fails from a fresh kernel. examples/variable-output.ipynb demonstrates a changed output.
