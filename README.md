# MEMS Frequency Comb Modeling

Python simulations exploring the concepts and models presented in *Existence Conditions for Phononic Frequency Combs*.

## Notebooks

| Notebook | What it covers |
|---|---|
| `sample.ipynb` | Single oscillator built up step by step: simple harmonic motion → damping → external drive |
| `coupled_modes.ipynb` | Full two-mode model (Eqs. S1.1–S1.2): parametric resonance, the comb threshold, and spectra |

There are two ways to work on this repo. Pick one:

- **Option A: GitHub Codespaces in your browser.** Nothing to install, and you get the same environment every time.
- **Option B: Local setup on Windows.** Uses a Python virtual environment on your own machine.

---

## Option A: GitHub Codespaces (browser)

A codespace is a Linux machine in the cloud running VS Code in your browser. The repo's `.devcontainer/devcontainer.json` sets it up automatically with Python 3.11, the packages in `requirements.txt`, and the Python and Jupyter extensions.

### 1. Get access
You need to be a collaborator on the repo. If you can't see the **Code** button options described below, ask the repo owner to add you under **Settings → Collaborators**, then accept the invite at [github.com/notifications](https://github.com/notifications).

### 2. Create a codespace
1. Open the repo on GitHub.
2. Click the green **Code** button, then the **Codespaces** tab.
3. Click **Create codespace on main**.

The first build takes a few minutes while packages install. Later starts are much faster.

### 3. Run a notebook
1. Open a notebook (for example, `coupled_modes.ipynb`) from the Explorer sidebar.
2. Click **Select Kernel** (top right) → **Jupyter Kernel…** → **Python 3.11 (MEMS)**.
   If that option isn't listed, choose **Python Environments** → **Python 3.11** (`/usr/local/bin/python`).
3. Click **Run All**.

### 4. Save your work with git
Git is already signed in inside the codespace. Use a branch so you don't overwrite each other's work:

```bash
git checkout -b yourname/short-description
git add .
git commit -m "Describe the change"
git push -u origin yourname/short-description
```

Then open a pull request on GitHub. You can also use the **Source Control** panel (branch icon in the left sidebar) instead of the terminal.

To get your partner's latest changes:

```bash
git checkout main
git pull
```

### 5. Stop the codespace when you're done
Codespaces use your monthly free quota while they're running. They stop on their own after 30 minutes of inactivity, but it's better to stop them yourself:

- In the codespace: click **Codespaces** in the bottom-left corner → **Stop Current Codespace**, or
- Go to [github.com/codespaces](https://github.com/codespaces) → **⋯** next to the codespace → **Stop codespace**.

Stopping keeps your files and uncommitted changes. **Deleting** the codespace removes anything you haven't pushed. Check your usage at [github.com/settings/billing](https://github.com/settings/billing). Students can get a larger quota through the GitHub Student Developer Pack.

To reopen a stopped codespace, go to [github.com/codespaces](https://github.com/codespaces) and click its name.

### Optional: open the codespace in desktop VS Code
Install the **GitHub Codespaces** extension in VS Code. Then, in the browser codespace, click **☰** → **Open in VS Code Desktop**.

---

## Option B: Local setup (Windows)

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

### Running the project

Activate the virtual environment before working on the project:

```powershell
.venv\Scripts\Activate.ps1
```

Then open the Jupyter notebook in VS Code.

---

## Updating dependencies

If new packages are installed, update `requirements.txt` with:

```bash
pip freeze > requirements.txt
```

**Important:** `pip freeze` on Windows adds `pywinpty`, which can't be installed on Linux and will break the codespace build. After freezing, make sure that line reads:

```
pywinpty==3.0.5; sys_platform == "win32"
```

The version number may differ. Keep whatever version `pip freeze` writes and just add `; sys_platform == "win32"`.

After pushing a change to `requirements.txt` or `.devcontainer/`, rebuild your codespace to pick it up: Command Palette (`Ctrl+Shift+P`) → **Codespaces: Rebuild Container**.

---

## Troubleshooting (Codespaces)

**The kernel isn't listed in Select Kernel.**
Make sure the Python and Jupyter extensions show as installed in the Extensions panel. If they don't, click **Install in Codespace**. Then register the kernel and reload the window:

```bash
python -m ipykernel install --user --name mems --display-name "Python 3.11 (MEMS)"
```

Command Palette → **Developer: Reload Window**.

**`git push` fails with "This repository is configured for Git LFS but 'git-lfs' was not found".**
This repo doesn't use Git LFS. The error comes from a leftover hook, which you can delete:

```bash
rm .git/hooks/pre-push
```

This only affects your codespace.

**The codespace opens in a "recovery container".**
The dev container build failed, usually because a package in `requirements.txt` didn't install. Open the Command Palette → **Codespaces: View Creation Log** and look for the error. Check the `pywinpty` line first.
