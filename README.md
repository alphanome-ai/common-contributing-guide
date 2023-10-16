# Alphanome.AI Common Contribution Guide

Welcome to the unified contribution guide for select Alphanome-AI projects. This document serves as a comprehensive resource for developers, detailing everything you need to contribute effectively. It covers environment setup, coding standards, and contribution workflows.

This guide is specifically referenced in the `CONTRIBUTING.md` files for the projects [sec-parser](https://github.com/alphanome-ai/sec-parser/blob/main/CONTRIBUTING.md) and [sec-ai](https://github.com/alphanome-ai/sec-ai/blob/main/CONTRIBUTING.md).

## Table of Contents
- [Quick Start Guide](#quick-start-guide)
- [Contribution Workflow](#contribution-workflow)
- [Setting Up Your Development Environment](#setting-up-your-development-environment)
- [Adhering to Coding Standards](#adhering-to-coding-standards)
- [Working with Complex Data: Unit Testing Approach](#working-with-complex-data-unit-testing-approach)
- [Seeking Assistance and Asking Questions](#seeking-assistance-and-asking-questions)

## Quick Start Guide

We understand that you're eager to start contributing to our projects. So, we've prepared a brief guide to get you up and running as quickly as possible. Let's dive right in!

1. **Setting up Poetry**: We prefer Poetry over pip for managing dependencies. It's easy to install on your system. Just follow the instructions provided [here](https://python-poetry.org/). Or, you can use the command below:

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

2. **Installing Project Dependencies**: Once you've got Poetry installed, it's time to get the project dependencies. Navigate to the project directory and use the following command:

```bash
poetry install
```

3. **Getting Task Ready**: Task is our go-to tool for task management. It's a simple and efficient alternative to Make, written in Go. You can install it by following the instructions [here](https://taskfile.dev/#/installation).

4. **Exploring Common Operations**: We've made several common operations available as tasks for your convenience. You can view the most commonly used ones with the command below:

```bash
task --list
```

**Congratulations!** You're now ready to start contributing. We're excited to have you join us and look forward to the valuable contributions you'll make.

For a more comprehensive understanding of our contribution workflow and development environment setup, continue reading.

## Contribution Workflow

We're thrilled that you're considering contributing to our project! To facilitate your journey, we've structured a recommended workflow. However, we encourage you to adapt this process to fit your preferred style.

### Identifying a Contribution

1. **Explore Existing Issues**: If you're interested in contributing to our projects, a convenient starting point is to browse the existing GitHub issues. For example, you can check out the [sec-parser Issues](https://github.com/alphanome-ai/sec-parser/issues). Look for issues labeled `contributions-welcome`, as these usually align with our overarching [roadmap](https://github.com/orgs/alphanome-ai/discussions/categories/roadmap-future-plans). For those new to the project, consider starting with issues tagged `good-first-issue`.

2. **Consult the Short-Term Roadmap**: To gain a broader perspective on our upcoming projects and focus areas, you can visit our [short-term roadmap](https://github.com/orgs/alphanome-ai/discussions/21). This will help you find contributions that are in sync with our overall objectives.

3. **Propose New Contributions**: Should you come across a bug that's not already on our radar, or if you have a fresh idea for an improvement, we are open to new contributions. For such initiatives, it's beneficial to start a discussion in the [Discussions](https://github.com/alphanome-ai/sec-parser/discussions) section. This not only gauges community interest but also ensures that your efforts align with the project's goals.

These three pathways offer a rounded view of how you can make meaningful contributions to our projects, including `sec-parser`.

### Preparing for Contribution

1. **Fork the Project:** Create your own copy of the project where you can make changes by forking it.

2. **Discuss Your Approach:** Although optional, we highly recommend discussing your approach to the issue in the issue thread. This is a great place to ask questions or seek help, and it also helps avoid duplicate efforts. Remember, we're a community and we're here to support each other!

3. **Clone and Update Your Fork:** Clone your forked project to your local machine. We strongly recommend that you regularly push your code to a draft PR. This allows others to see your progress and offer assistance if necessary. To ensure that you're working with the most recent changes from the main branch, follow the instructions provided in this [GitHub guide](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork#syncing-a-fork-branch-with-the-github-cli).

### Making the Contribution

1. **Create a Pull Request:** Once you're ready with your changes, create a pull request on the original repository. Make sure to provide a clear and comprehensive description of the changes you've made.

2. **Check CI/CD Output:** Our CI/CD pipeline will automatically run `task ci-checks` every time you push to your PR, notifying you of any issues. You can also run `task ci-checks` locally before pushing to catch any potential problems early.

## Setting Up Your Development Environment

### Supported Operating Systems

Our development environment is optimized for Linux and macOS. If you're using these operating systems, the setup should be straightforward. For Windows users, we recommend setting up the Windows Subsystem for Linux (WSL) and using the "Opening a WSL 2 folder in a container" method as outlined in the [VS Code documentation](https://code.visualstudio.com/docs/remote/wsl). Please be aware that we officially support only Linux and macOS. Windows users may need to troubleshoot independently.

### Installing Poetry

For managing dependencies in our projects, we prefer using Poetry over pip. Poetry is a robust tool for package management in Python applications. It allows you to declare the libraries your project relies on, and it takes care of installing and updating them for you. You can read more about Poetry [here](https://python-poetry.org/).

To get started with Poetry, you first need to install it. You can do this by running the following command:

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

Once you've installed Poetry, you can confirm that the installation was successful by checking its version. Run the following command to do this:

```bash
poetry --version
```

Now that you have Poetry installed, you can use it to install the dependencies for this project. Navigate to the project directory and run the following command:

```bash
poetry install
```

This command will install all the necessary dependencies for the project.

> **Note**
To execute a command within the context of the project, use `poetry run`. This ensures that the command is executed with the virtual environment activated and with all the dependencies available. For instance, if you want to run a Python script in the project, you would use the following command: `poetry run python your_script.py`. This command will execute `your_script.py` using the Python interpreter in the project's virtual environment.


### Installing Task

In our projects, we utilize `Task` for task management. `Task` is a flexible and straightforward tool that allows us to define and run the tasks with ease. You can learn more about `Task` [here](https://taskfile.dev/).

To start using Task, you first need to install it. You can do this by following the instructions provided on the [Task installation page](https://taskfile.dev/installation/).


### Confirming Installation of Poetry and Task

Once you have `Task` installed, you can confirm that both `Task` and Poetry are functioning correctly by running the project's unit tests. To do this, navigate to the project directory and execute the following command:

```bash
task unit-tests
```

This command will initiate the unit tests for the project. If all tests pass successfully, it indicates that both `Task` and Poetry are properly set up.

### Managing Tasks with Task

To view the most commonly used tasks that you can execute with Task, navigate to the project directory and execute the following command:

```bash
task --list
```

This command will display a list of the most commonly used tasks. Here's an example of what you might see:

```text
$ task --list
task: Available tasks for this project:
* ci-checks:                    Execute all CI/CD checks for debugging a failing CI/CD pipeline.
* e2e-generate-dataset:         Create end-to-end dataset snapshots using the latest parser outputs.
* e2e-verify-dataset:           Validate the end-to-end dataset snapshots against the latest parser outputs.
* launch-debug-dashboard:       Start a local debugging dashboard in the browser.
* launch-docs:                  Start a local server to preview and automatically rebuild documentation upon file modification.
* monitor-unit-tests:           Run unit tests and rerun them immediately upon file modification.
* pre-commit-checks:            Execute all pre-commit checks before committing code.
* pre-push-checks:              Execute all pre-push checks before pushing code or creating a PR.
```

To view all the tasks and their descriptions that you can execute with Task, you can open the `Taskfile.yml file located at the root of the project.

### Recommended IDE

In order to maximize your productivity and efficiency when contributing to our codebase, we highly recommend using Cursor as your Integrated Development Environment (IDE). Cursor is a powerful, AI-enhanced fork of VSCode that is designed to streamline the coding process. It's not just about writing code, but writing it well and quickly.

Our codebase is rich with docstrings, type hints, and has a high unit test coverage. These features are leveraged by Cursor's AI capabilities (with ChatGPT), to provide intelligent code completions, error detection, and other helpful suggestions. This means you can write code faster, with fewer errors, and spend less time debugging.

Cursor is free to use and retains all the features you love about VSCode, but with the added benefit of AI integration. This makes it an ideal choice for working on our projects. You can read more about Cursor and download it from [here](https://cursor.sh/).

> **Note**
For optimal performance, we recommend using OpenAI's GPT-4 model.

> **Note**
Cursor Free allows you to use unlimited AI features at no cost when you provide your own API key. You can generate your own API key at [OpenAI's API key page](https://platform.openai.com/account/api-keys) and add it to your Cursor settings for optimal performance.

### Using Pre-commit (Optional)

Pre-commit is a tool that integrates with Git to automatically run various code checks, including unit tests, before each commit. This ensures that all modifications are validated before they are committed.

This tool is already installed as a package dependency during the `poetry install` command. To activate it for your project, run the following command:

```bash
pre-commit install
```

Once you turn on pre-commit, it will check your code automatically every time you try to make a commit. If it finds any problems, you'll need to fix them before you can go ahead and commit your changes. Some issues will be fixed for you, while for others, you'll get a warning to let you know something needs attention.

## Adhering to Coding Standards

The pre-commit tool you've installed is designed to perform a series of checks with each commit you make. These checks are mirrored in our CI/CD pipeline and must pass before any PR can be merged. This process ensures the quality and consistency of our code across the entire project. Remember, you have the flexibility to run these checks individually or all at once using `Task`.

### Code Formatting

We use `Ruff` for Python linting due to its speed and extensive rule set. It consolidates the functionality of multiple tools, supports automatic error correction, and is trusted by major open-source projects. For more details, refer to the [Ruff Documentation](https://ruff.dev/docs).

> **Note**
[Cursor](https://cursor.sh/) AI could be a helpful resource in addressing lint issues. However, it's important to review and confirm the AI's recommendations to ensure they are suitable and meet the intended purpose, rather than blindly applying them.

### Type Hints

We use type hints in our code to make it more readable and maintainable. They help catch certain types of errors early and allow IDEs to provide better code completion. For a quick introduction and further reading, visit [Real Python's guide on type hinting](https://realpython.com/lessons/type-hinting/).

> **Note**
[Cursor](https://cursor.sh/) AI can assist in transforming untyped code into typed code within your project. However, it's crucial to review and verify the AI's output for accuracy, rather than applying it blindly.

### Unit Tests

Unit tests are essential for verifying the functionality of code under various inputs and conditions. They aid in early bug detection and ensure safer refactoring. While writing tests, the focus is on functionality rather than cleanliness, hence code quality checks are not enforced on test code. This approach enhances productivity. For more information on Python testing, refer to [Real Python's guide](https://realpython.com/python-testing/).

> **Note**
Consider using [Cursor](https://cursor.sh/) AI to facilitate your unit test writing process. However, remember that the purpose of unit tests is not just to "cover" your code. Unit tests establish a specification of the expected behavior of correctly written code under a variety of circumstances, isolated from other pieces of code.

> **Note**
We suggest using the [Coverage Gutters](https://marketplace.visualstudio.com/items?itemName=ryanluker.vscode-coverage-gutters) extension if you're a VSCode or Cursor user. This tool seamlessly integrates with our projects to show line coverage. It visually highlights the lines of code that have been executed during unit testing. [Here's](https://github.com/alphanome-ai/common-contributing-guide/blob/main/assets/274829189-531511ff-3ac9-42fc-a483-79adea039eda.png) how Coverage Gutters displays this information when [activated](https://github.com/alphanome-ai/common-contributing-guide/blob/main/assets/274829200-70aa5d5e-50ba-46fc-a9aa-ca0d176fc1f9.png).

### Conventional Commits (Optional)

We encourage the use of conventional commits for your contributions. Conventional commits provide a structured format for commit messages, making them more readable and easy to automate. For more details, refer to the [Conventional Commits specification](https://www.conventionalcommits.org/).

> **Note**
[Cursor](https://cursor.sh/) AI can assist in structuring your commit messages. However, remember that the purpose of commits is to state **why** you're making a change, not what the change is. For example, a commit message like "Refactor serialization logic to improve performance" is much more informative than just "Update serialization".

## Working with Complex Data: Unit Testing Approach

When dealing with complex data, a common and effective strategy is to encapsulate the complexity within a unit test. This approach involves defining the various scenarios you anticipate and then focusing on testing these scenarios rather than the entire document or using extensive debugging tools.

This method significantly reduces the time required to verify if your modifications are working as expected. Here's how you can do it:

1. **Isolate the complexity:** Identify the complex part of your data and isolate it as a unit test. This could be a function, a class, or any other component that you find complex.

2. **Define the scenarios:** Determine what you want to happen for different inputs or states of your program. These scenarios will form the basis of your unit tests.

3. **Work with the unit test:** Once you have your unit test set up, you can make changes and run the test to see if your changes are working as expected. This is much quicker and more efficient than working with the full document or using full debugging tools.

Remember, the goal here is to make your testing process more efficient and manageable. By isolating complexity and focusing on unit tests, you can achieve this goal and ensure your changes work as intended.

## Seeking Assistance and Asking Questions
Should you have any questions, concerns, or need further clarification, please post them to our [Discussions](https://github.com/orgs/alphanome-ai/discussions) page unless they are specific to a GitHub issue or a GitHub pull request. This centralized area allows for easier tracking of community inquiries and ensures that you get a timely response.

## Conclusion
Thank you for your interest in contributing to our projects! We're thrilled to have you on board. Your contributions help make our projects better, and we sincerely appreciate your time and effort.

Happy coding!
