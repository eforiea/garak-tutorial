# Garak LLM Security Testing Tutorial

This repository contains my hands-on experiments with **[Garak](https://github.com/NVIDIA/garak)**, an LLM vulnerability scanner developed by NVIDIA.

The goal of this project is to learn how to test LLM-based systems for security weaknesses and understand what automated security tools can and cannot prove.

## What is Garak?

Garak is an **LLM vulnerability scanner**.

It uses different:

* **Probes** to test specific types of attacks or unwanted behavior.
* **Detectors** to evaluate the model's responses.
* **Targets** to define the LLM or system being tested.

A simple mental model:

```text
Garak
  ↓
Probe
  ↓
Target LLM
  ↓
Response
  ↓
Detector
  ↓
Result
```

Garak can test areas such as:

* Prompt Injection
* Jailbreaks
* Data Leakage
* Hallucination
* Toxicity
* Misinformation
* Other LLM weaknesses

## Project Goals

This repository is part of my AI Security learning path.

The main goals are:

1. Learn how Garak works.
2. Understand probes and detectors.
3. Run controlled LLM security tests.
4. Analyze Garak results manually.
5. Distinguish scanner results from confirmed vulnerabilities.
6. Map security findings to a broader LLM security model.
7. Document experiments and security findings.

## Environment

The project is developed and tested with:

```text
Python 3.11+
Garak v0.16.0
Linux / Windows
LM Studio v 0.4.19
Model: google/gemma-4-e2b

```

The current Garak project recommends Python versions from **3.11 to 3.13** for source installation.

## Installation

It is recommended to use a virtual environment.

### 1. Create a virtual environment

Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 2. Install Garak

```bash
python -m pip install -U garak
```

### 3. Verify the installation

```bash
garak --help
```

You can also check the available probes:

```bash
garak --list_probes
```

If these commands work, Garak is installed correctly.

## Basic Usage

The general Garak workflow is:

```text
Choose Target
     ↓
Choose Probe
     ↓
Run Test
     ↓
Inspect Response
     ↓
Analyze Detector Result
```

A basic command follows this structure:

```bash
garak --target_type <target_type> --target_name <target_name>
```

To run a specific probe:

```bash
garak --target_type <target_type> \
      --target_name <target_name> \
      --spec <probe>
```

For example:

```bash
garak --target_type huggingface \
      --target_name gpt2 \
      --spec probes.dan.Dan_11_0
```

The exact target and probe depend on the model and experiment being performed.

## Important Security Principle

A Garak detection should **not automatically be treated as a confirmed vulnerability**.

For example:

```text
Probe
  ↓
Model Response
  ↓
Detector Match
```

does not automatically mean:

```text
Confirmed Vulnerability
```

A proper assessment should continue with:

```text
Detection
   ↓
Manual Verification
   ↓
Evidence
   ↓
Security Impact
   ↓
Risk Assessment
```

This repository therefore focuses not only on running Garak, but also on **understanding and validating its results**.

## Repository Structure

The repository will gradually evolve as experiments are added.

```text
garak-tutorial/
│
├── images/
│
├── cheat-sheet.md
│
├── how-to-use.md
│
├── notes.md
│
├── images/
│
├── README.md
│
└── .gitignore
```

## Disclaimer

This repository is intended for **educational and authorized security testing**.

Only test models, applications, and systems that you are authorized to assess.
