## Enablement Recommendations: Foundational Topics

## Foundational Goals and Why They Matter

The goal of this foundational document is to build the core toolset and mindset required for an Infrastructure Engineers. Before writing your frist Infrastructure as Code manifest and deploying it, you must be comfortable with the tools and concepts that Openshift and Openshift GitOps are built around.

The learning path below explains *what* each foundational skill is and *why* it is critical for automation.

```mermaid
graph LR
    A[Introduce Concepts] --> B[Use YAML Syntax];
    B --> C[Configure Your IDE];
    C --> D[Use Version Control];
    D --> E[Practice - Tie it all together];
```

* **Introduce Concepts:** Grasp the high-level ideas of IaC (Infrastructure as Code) and DevOps. These are the core "why" philosophies, and Openshift GitOps is the tool designed to implement them. Understanding this gives your work context.
* **Use YAML Syntax:** Write YAML syntax and use a linter to verify it. YAML is one of the languages of Openshift; everything you write (manifest, values files, etc.) is in YAML. Mastering its syntax is like learning the alphabet before writing a novel.
* **Configure Your IDE:** Set up VSCode as a professional automation editor. VSCode is your workshop. With the right extensions (like the Red Hat YAML linter), it catches your YAML syntax errors before you commit them to Git, saving you hours of troubleshooting.
* **Use Version Control:** Experiment with basic git commands and workflows. Git is the "source of truth" for Openshift GitOps. Your code (Manifests) must be stored in Git, as Openshift GitOps pulls code directly from it to configure your Infrastructure. A basic workflow (clone, branch, commit, push) is a daily requirement.

## Independent Learning Path Recommendations

Build your toolset - learn some yaml, vscode, and git.  Then integrate the tools.

### Introduce Concepts

* [What is Infrastructure as Code (**IaC**)?](https://www.redhat.com/en/topics/automation/what-is-infrastructure-as-code-iac)
* [What is **DevOps**?](https://www.redhat.com/en/topics/devops/what-is-devops)
* [What is **Openshift GitOps**?](https://www.redhat.com/en/blog/announcing-openshift-gitops)

### YAML Essentials

* [What is YAML?](https://www.redhat.com/en/topics/automation/what-is-yaml)
* [YAML for beginners](https://www.redhat.com/en/blog/yaml-beginners)

### Git Essentials

* [A Beginner's Guide to Git](https://developers.redhat.com/articles/2023/08/02/beginners-guide-git-version-control#)
* [Learn **Git** (References to book, videos...)](https://git-scm.com/learn)
* [Git best practices: Workflows for GitOps deployments](https://developers.redhat.com/articles/2022/07/20/git-workflows-best-practices-gitops-deployments#)
* [A beginner's guide to Git version control](https://developers.redhat.com/articles/2023/08/02/beginners-guide-git-version-control#)
* [Introduction to Git and GitHub (lab)](https://developers.redhat.com/learning/learn:ansible:foundations-ansible/resource/resources:introduction-git-and-github)

### VsCode Essentials

* [Visual Studio Code](https://code.visualstudio.com/docs) download, tutorials and setup!

### Bring yaml, vscode and git together with extensions

* [YAML Language Support by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)
  * **Note:** This extension provides the **YAML linting** (real-time error checking) mentioned in our goals.
* [GitLens — Git supercharged](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
* [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)

---

## Sanity Check

Some extra notes:

* [Yaml 101](./yaml-101.md)
* [Git 101](./git-101.md)

### Key Git Commands to Know

While the guides provide full details, focus on understanding this core set of commands first. This is the basic workflow you will use every day.

| Command | What it does | Example / Note |
| :--- | :--- | :--- |
| `git clone [url]` | Creates a local copy of a remote repository on your computer. | `git clone https://github.com/user/repo.git` |
| `git branch [name]` | Creates a new branch for you to work on. | `git branch feature/new-playbook` |
| `git switch [name]` | Switches your active working directory to the specified branch. | `git switch feature/new-playbook` (Replaces older `checkout` command) |
| `git status` | Shows you the current state of your repository (changed files, etc.). | You will use this constantly. |
| `git add [file]` | Stages a file, telling Git you want to include it in the next commit. | `git add .` (Stages all changed files) |
| `git commit -m "..."` | Saves a "snapshot" of your staged changes to the repository's history. | `git commit -m "Add new inventory file"` |
| `git pull` | Fetches the latest changes from the remote repository and merges them. | Keeps your local branch up-to-date. |
| `git push` | Uploads your local commits to the remote repository. | Shares your work with the team and Openshift GitOps. |

### Hands-On Practice: Tying It All Together

This simple exercise will confirm you have successfully set up your environment by combining all the foundational topics.

* **Prerequisite:** [Intro to Git in VS Code](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git)

Your goal is to:

1. Create a new folder (e.g., `my-iac-project`).
2. Open this folder in **VSCode**.
3. Create a new file named `agent-config.yaml`.
4. Write a simple **YAML** structure in this file. Use the Red Hat YAML extension to check for errors in real-time.
    > **Example `agent-config.yaml`:**
    >
    > ```yaml
    > ---
    > apiVersion: v1beta1
    > kind: AgentConfig
    > metadata:
    >   name: example.lab
    > rendezvousIP: 192.168.122.10
    > hosts:
    > - hostname: sno
    >   rootDeviceHints:
    >     deviceName: "/dev/sda" 
    >   interfaces:
    >     - name: ens3
    >       macAddress: 52:54:00:d2:2a:66 
    >   networkConfig:
    >     dns-resolver:
    >       config:
    >         server:
    >           - 192.168.122.254
    > ```
    >
5. Use the **Git** integration in VSCode (or the command line) to:
    * Initialize a new Git repository (`git init`).
    * Add the `agent-config.yaml` file to staging.
    * Make your first commit (e.g., `git commit -m "Initial Openshfitt cluster setup"`).
