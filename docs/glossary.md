# Glossary – Terms Used in This Playbook

A plain-English reference for every technical term you'll encounter.

---

| Term | What It Means |
|------|--------------|
| **Ansible** | An automation tool that reads a "playbook" (a recipe) and executes each step on your behalf. Think of it like a checklist that runs itself. |
| **Playbook** | A YAML file that lists tasks for Ansible to perform, in order. Comparable to a cooking recipe — each task is one instruction. |
| **Task** | A single step inside a playbook (e.g., "create a namespace" or "install the Operator"). |
| **Handler** | A special task that only runs when *notified* by another task. Used here to wait for the Operator to be ready **only** when something actually changed. |
| **Variable (`vars`)** | A named setting you can change without editing the playbook — like a form field. Example: `namespace: "mariadb-operator"`. |
| **Ansible Vault** | Ansible's built-in encryption tool. It lets you store secrets (passwords, API keys) in encrypted files that only someone with the vault password can read. |
| **Kubernetes (K8s)** | A platform that runs and manages containerised applications across many servers. Think of it as an operating system for a data centre. |
| **Namespace** | A virtual folder inside Kubernetes. Resources in one namespace are isolated from resources in another — like separate departments in an office. |
| **Pod** | The smallest unit Kubernetes runs — usually one container (one running copy of an application). |
| **Deployment** | A Kubernetes object that ensures a specific number of pod copies are always running. If a pod crashes, the Deployment automatically restarts it. |
| **Replica** | One running copy of a pod. `replicas: 1` means "keep exactly one copy running at all times." |
| **Secret** | A Kubernetes object designed to hold sensitive data (passwords, tokens). Access is controlled by RBAC rules. |
| **RBAC** | *Role-Based Access Control* — rules that define who (or what) can read, write, or delete specific resources in the cluster. |
| **Helm** | A package manager for Kubernetes. Instead of writing dozens of YAML files by hand, you install a single "chart" (package) that contains everything. |
| **Helm Chart** | A pre-built package of Kubernetes manifests. Similar to a `.deb` or `.rpm` installer on Linux, or an app from an app store. |
| **Helm Release** | A specific, named installation of a chart on a cluster. You can have multiple releases of the same chart with different settings. |
| **Helm Repository** | A web address that hosts Helm charts — like an app store URL. |
| **Operator** | A program that runs inside Kubernetes and automates the management of a complex application (here: MariaDB). It watches for custom requests and handles them automatically. |
| **Custom Resource (CR)** | A user-defined object type in Kubernetes. The MariaDB Operator defines a `MariaDB` CR so you can say "I want a database with 1 GiB storage" and the Operator builds it. |
| **CRD** | *Custom Resource Definition* — the schema (blueprint) that tells Kubernetes what fields a Custom Resource can have. |
| **MariaDB** | An open-source relational database, forked from MySQL. Used to store structured data in tables with rows and columns. |
| **kubeconfig** | A configuration file (`~/.kube/config`) that stores cluster addresses, user credentials, and context settings so `kubectl` and Helm know which cluster to talk to. |
| **Idempotent** | A property meaning "running this multiple times produces the same result as running it once." Every task in this playbook is idempotent — safe to re-run. |
| **`state: present`** | Tells Ansible "make sure this thing exists." If it already exists, do nothing; if it's missing, create it. |
| **`state: absent`** | Tells Ansible "make sure this thing does NOT exist." If it exists, remove it; if it's already gone, do nothing. |
| **`wait: true`** | Tells the task to pause until the resource is fully ready, rather than returning immediately. Prevents the next task from starting too early. |
| **`stringData`** | A field on Kubernetes Secrets that accepts plain-text values. Kubernetes automatically base-64-encodes them before storing. Simpler than encoding manually. |
| **`gather_facts: no`** | Tells Ansible to skip collecting information about the local machine (CPU, memory, OS). Not needed here because we only talk to Kubernetes. |
