# Alphanome.AI Common Contribution Guide

Welcome to the unified contribution guide for select Alphanome-AI projects. This document serves as a comprehensive resource for developers, detailing everything you need to contribute effectively. It covers environment setup, coding standards, and contribution workflows.

This guide is specifically referenced in the `CONTRIBUTING.md` files for the projects [sec-parser](https://github.com/alphanome-ai/sec-parser/blob/main/CONTRIBUTING.md) and [sec-ai](https://github.com/alphanome-ai/sec-ai/blob/main/CONTRIBUTING.md).

## Table of Contents
- [Development Environment: Quick Start](#development-environment-quick-start)
- [Setting Up Your Development Environment](#setting-up-your-development-environment)
- [Adhering to Coding Standards](#adhering-to-coding-standards)
- [Working with Complex Data: Unit Testing Approach](#working-with-complex-data-unit-testing-approach)
- [Seeking Assistance and Asking Questions](#seeking-assistance-and-asking-questions)
- [Contribution Workflow](#contribution-workflow)

## Development Environment: Quick Start
Welcome! If you're eager to start contributing, you're in the right place. This quick guide will get you set up and ready to contribute as quickly as possible.

> **Note**
This Quick Start Guide is intended for those who are already experienced with development tools and environments. If you're new or need detailed instructions, please read the [Setting Up Your Development Environment](#setting-up-your-development-environment) section.

1. **Setting up Poetry**: We prefer using Poetry instead of pip for managing dependencies. To install Poetry, you can follow the instructions available [here](https://python-poetry.org/), or simply run the command below:

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

2. **Installing Project Dependencies**: After installing Poetry, you can get the project dependencies. Navigate to the project directory and run:

```bash
poetry install
```

3. **Getting Task Ready**: Task is an extremely straightforward tool and we use it solely on running predefined commands. Installation instructions can be found [here](https://taskfile.dev/#/installation). Let's give a quick example. Say, we have `Taskfile.yml`:

```
tasks:
  one:
    cmds:
      - echo Hello
      - task: two
      - echo !!!
  two:
    cmds:
      - echo World
```

Running `task one` will print "Hello World !!!", and running `task two` will print "World".

4. **Exploring Common Operations**: We've set up tasks for common operations. To see a list of the most commonly used ones, run:

```bash
task --list
```

**Congratulations!** You're now prepared to contribute. We're thrilled to have you and can't wait to see your contributions.

For a more in-depth understanding of our contribution workflow, coding standards, and development environment, please continue reading the sections that follow.

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

### Choosing an IDE

While we understand and respect that developers have their own preferred tools and setups, you might find Cursor to be a highly effective option for contributing to this project. Cursor is a powerful, AI-augmented version of VSCode, equipped to make the coding process smoother and more efficient.

Our codebase is enriched with docstrings, type hints, and a high level of unit test coverage. If you choose to use Cursor, its AI capabilities can leverage these features for smarter code completions, effective error detection, and various other useful suggestions. This can help you write clean, error-free code more rapidly, reducing debugging time.

However, please note that the use of Cursor is completely optional. Our primary concern is the quality of your contributions, not the tools you use to produce them.

For those interested in trying out Cursor, it is free and includes all the functionalities you appreciate in VSCode, along with AI-enhanced features. You can learn more and download it from [here](https://cursor.sh/).

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

## Contribution Workflow

We're thrilled you're considering contributing to our projects! We've crafted this guide to make your journey smooth and enjoyable. Of course, you're free to follow your own workflow if you prefer.

### Step 1: Pick What to Work On

1. **Look at Open Issues**:
  - **Option 1**: Navigate to our [Request For Contributions](https://github.com/orgs/alphanome-ai/projects/7) board. This board contains tasks that are ready for contributions.
  - **Option 2**: Browse the GitHub Issues page of the specific project that interests you. For example, visit the [`sec-parser` Issues](https://github.com/alphanome-ai/sec-parser/issues) or [`sec-ai` Issues](https://github.com/alphanome-ai/sec-ai/issues).
  - **Tips**:
    - Search for tasks labeled `contributions-welcome`. These tasks align with our goals.
    - If you're new to the project, look for tasks labeled `good-first-issue`.

2. **Read Our Plans**:
  - Examine our [Short-Term Roadmap](https://github.com/orgs/alphanome-ai/discussions/21) to understand our upcoming projects and focus areas.

3. **Suggest Your Own Task**:
  - If you discover an issue or have a novel idea, feel free to propose it. Initiate a conversation either in the [Discussions](https://github.com/orgs/alphanome-ai/discussions) forum or on our [Discord](https://discord.gg/2MC3uJhBxs) server.

### Step 2: Get Ready to Work

1. **Consult the Project's CONTRIBUTING.md**:
  - Before you start, make sure to read the `CONTRIBUTING.md` file of the project you've chosen. This file will guide you on setting up the development environment, following coding standards, and understanding the codebase and domain context.

2. **Fork the Project**: 
  - Create your own copy of the project by 'forking' it on GitHub.

3. **Discuss Your Plan**: 
  - Although optional, we recommend commenting on the issue you're tackling. Use this space to clarify your approach, ask questions, or seek guidance.

4. **Clone and Update Your Fork**: 
  - Download your forked project to your local machine and keep it updated. Refer to this [GitHub Guide](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork#syncing-a-fork-branch-with-the-github-cli) for instructions on how to sync your fork.

### Step 3: Do the Work

1. **Create a Pull Request**: 
  - Once you've made your changes, submit them for review by creating a 'pull request'. Provide a clear and comprehensive explanation of what you've done.

2. **Check for Errors**: 
  - After you've submitted your pull request, our automated system will run checks. If it finds issues, you'll be notified. To preemptively catch any potential issues, you can also run these checks locally on your machine.

Thank you for considering contributing to our project. Your help is invaluable to us!

## Seeking Assistance and Asking Questions
Should you have any questions, or concerns, or need further clarification, please post them to our [Discussions](https://github.com/orgs/alphanome-ai/discussions) page or [Discord](https://discord.gg/9zePQH7D) unless they are specific to a GitHub issue or a GitHub pull request. This centralized area allows for easier tracking of community inquiries and ensures that you get a timely response.

## Conclusion
Thank you for your interest in contributing to our projects! We're thrilled to have you on board. Your contributions help make our projects better, and we sincerely appreciate your time and effort.

Happy coding!
