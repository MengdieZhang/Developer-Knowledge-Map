# Version Control: Git, Branching, Pair Programming

## Concept Overview

* **Git**: A distributed version control system that tracks code changes and allows multiple developers to collaborate on a shared codebase.
* **Branching**: Creating isolated copies of code to develop features, fix bugs, or experiment, without affecting the main codebase.
* **Pair Programming**: A technique where two developers work together at one workstation. One writes code (driver), while the other reviews it (navigator).

## Real-World Use

* Teams use **feature branches** for developing new functionalities, and **hotfix branches** for urgent fixes.
* **Git** is used for code versioning, collaboration, and change history.
* **Pair programming** is often used in high-stakes modules, onboarding, or knowledge sharing.

## Common Pitfalls & Tips

* **Long-lived branches** can cause major merge conflicts.
* Always **pull and rebase** before opening a PR to ensure you're working on the latest version.
* In pair programming:

    * Keep roles (driver/navigator) clear.
    * Switch roles regularly.
    * Communicate intentions openly.

## Interview Insights

* Be ready to describe:

    * Your team’s **branching strategy** (e.g., GitFlow, trunk-based).
    * How you **resolve merge conflicts**.
    * Scenarios where **pair programming** helped ship better code.
* Typical questions:

    * "What do you do before merging a feature branch?"
    * "Have you ever worked in a pair programming setting? How did it go?"

## Mini Scenario

> "You’re working on a critical bug fix and your teammate is out sick. The fix is on a stale feature branch. What’s your next step?"
>
> 🔍 You should:
>
> * Pull the latest main branch.
> * Rebase your stale branch.
> * Test thoroughly.
> * Open a detailed PR explaining urgency and changes.

## Hands-on Prompt

> * Simulate creating a feature branch off `main`.
> * Make a small code change (e.g., edit `README.md`).
> * Rebase it with `main` if any changes occurred.
> * Resolve a simple conflict.
> * Push and create a PR with a clear title and description.

---

