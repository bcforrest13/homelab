# Homelab Portfolio

> A self-documenting home lab built on Oracle Cloud Infrastructure (OCI),
> used to sharpen Linux/Cloud/DevOps skills, build demonstrable artifacts,
> and support a return to senior Linux/Cloud engineering work.

## What this is
This repository is the public face of a home lab running on an Oracle Linux 9
(ARM64) VM in OCI. Each subproject below is a real, working thing — not a
tutorial. The goal is hands-on evidence of current tooling: containers,
infrastructure-as-code, automation, observability, and CI/CD.

## Why
- ~30 years in IT (Macintosh/networking hardware -> Linux SA III, finance -> NASA)
- Re-entering the job market; this repo is résumé evidence, not a study log
- Practical, objective-driven learning (build first, read later)

## Lab environment
| Item            | Value                                  |
|-----------------|----------------------------------------|
| Cloud           | Oracle Cloud Infrastructure (OCI)      |
| OS              | Oracle Linux Server 9.8 (ARM64/aarch64)|
| Kernel          | UEK 6.12                               |
| Shape           | Ampere A1 (1 OCU, 6 GB) — Always Free  |
| Agent           | Hermes AI assistant, local install     |

## Project roadmap
| # | Project                          | Skill demonstrated        | Status   |
|---|----------------------------------|---------------------------|----------|
| 1 | Git + GitHub portfolio           | Version control, docs     | IN PROGRESS |
| 2 | Containers with Podman           | Containerization          | planned  |
| 3 | Ansible / IaC                    | Configuration automation  | planned  |
| 4 | OCI done right                   | Cloud (resume gold)       | planned  |
| 5 | Python automation scripts        | Glue/automation           | planned  |
| 6 | Observability (metrics + logs)   | Operations                | planned  |
| 7 | CI/CD with GitHub Actions        | Delivery pipelines        | planned  |

## How to use this repo
Clone, read the README in each subfolder, and reproduce. Everything is
intended to be runnable on a similar OCI Always-Free shape.

---
*Maintained by [your-name-here]. Built publicly as a learning + job-search artifact.*
