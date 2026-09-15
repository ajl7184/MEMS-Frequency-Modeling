# MEMS Frequency Comb Modeling

Python simulations exploring the concepts and models presented in *Existence Conditions for Phononic Frequency Combs*.

## Setup

### 1. Create a virtual environment

From the project directory:

```bash
python -m venv .venv
```

### 2. Activate the virtual environment

**Windows PowerShell:**

```powershell
.venv\Scripts\Activate.ps1
```

You should see `(.venv)` in your terminal.

### 3. Install dependencies

With the virtual environment activated:

```bash
pip install -r requirements.txt
```

### 4. VS Code / Jupyter

Open the `.ipynb` notebook in VS Code and select the **`.venv` Python environment** as the notebook kernel.

## Updating dependencies

If new packages are installed, update `requirements.txt` with:

```bash
pip freeze > requirements.txt
```

## Running the Project

Activate the virtual environment before working on the project:

```powershell
.venv\Scripts\Activate.ps1
```

Then open the Jupyter notebook in VS Code.
