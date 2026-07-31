# Python Virtual Environment (.venv)

## What is a Virtual Environment?

A virtual environment (venv) is an isolated Python environment created specifically for one project.

Instead of using the global Python installation and libraries, every project gets its own Python interpreter and installed packages.

---

## Why do we need it?

Without virtual environments:

Project A
- FastAPI 0.115

Project B
- FastAPI 0.95

Both projects share the same Python installation.

→ Version conflicts.
→ Updating one project may break another.

Using virtual environments:
```
Project A
├── .venv
│   ├── Python
│   ├── FastAPI 0.115
│   └── ...

Project B
├── .venv
│   ├── Python
│   ├── FastAPI 0.95
│   └── ...
```
Projects are completely isolated.

---

## The idea of Isolation

Virtual environments are the first example of **Isolation** in software engineering.

Isolation prevents different systems from affecting each other.

This same concept appears later in:

- Docker
- Virtual Machines
- Kubernetes
- Database Transactions

---

## How Virtual Environment Works

### Step 1

Create a virtual environment.

```bash
py -m venv .venv
```

This creates a miniature Python installation inside the project.

---

### Step 2

Activate it.

CMD

```bash
.venv\Scripts\activate
```

PowerShell

```powershell
.\.venv\Scripts\Activate.ps1
```

After activation:

```
(.venv)
```

appears in the terminal.

This means the terminal is now using the project's Python instead of the global Python.

---

### Step 3

Install packages.

```bash
py -m pip install fastapi sqlalchemy uvicorn pydantic
```

Packages are installed only inside `.venv`.

Global Python remains unchanged.

---

## Folder Structure

```
EcoScan/

├── backend/
│   ├── .venv/
│   ├── main.py
│   └── requirements.txt
```

The `.venv` folder contains:

- Python executable
- pip
- installed packages
- configuration

---

## requirements.txt

Generate:

```bash
pip freeze > requirements.txt
```

Purpose:

Save every installed dependency and version.

Example:

```
fastapi==0.117.1
sqlalchemy==2.0.44
uvicorn==0.37.0
```

Another developer can recreate the exact same environment using:

```bash
pip install -r requirements.txt
```

---

## Why not upload .venv to GitHub?

Because:

- Very large
- Machine-specific
- Can always be recreated

Instead, commit only:

- requirements.txt

Ignore:

```
.venv/
```

using `.gitignore`.

---

## Understanding PATH

Normally:

```
Terminal
    ↓
Global Python
```

After activating `.venv`:

```
Terminal
    ↓
EcoScan/.venv/python.exe
    ↓
Global Python
```

The virtual environment simply places itself at the beginning of the PATH variable.

It does NOT replace or modify the global Python installation.

---

## Common Commands

Create environment

```bash
py -m venv .venv
```

Activate (CMD)

```bash
.venv\Scripts\activate
```

Deactivate

```bash
deactivate
```

Install package

```bash
py -m pip install package_name
```

Export dependencies

```bash
pip freeze > requirements.txt
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## Best Practices

✓ Create one virtual environment per project.

✓ Always activate `.venv` before coding.

✓ Commit `requirements.txt`.

✓ Never commit `.venv`.

✓ Prefer using

```bash
py -m pip
```

instead of just `pip` to ensure the correct Python interpreter is used.

---

## Key Takeaways

Virtual Environment is NOT just a folder.

It is a complete, isolated Python environment dedicated to one project.

Its goal is reproducibility, dependency isolation, and preventing version conflicts.
