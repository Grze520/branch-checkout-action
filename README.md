# Branch Checkout Action

This repository demonstrates a GitHub Actions workflow that checks out a specific branch from an external repository 
and performs actions based on its contents. The project serves as an example of how to automate tasks with GitHub 
Actions, specifically by checking out and working with a designated branch from an external repository.

## Overview

The workflow completes the following tasks:
1. **Checkout an external repository**: The workflow clones an external GitHub repository and checks out a specific branch.
2. **Process files in the repository**: After checking out the repository, the workflow reads and outputs the content 
3. of a specific file (`greetings.txt`).

## Workflow Steps

1. **Trigger**: The workflow is triggered by a `push` event.
2. **Checkout external repository**: The workflow uses the [actions/checkout](https://github.com/actions/checkout) 
   action to checkout the repository `abystoma/external-workflow` on the branch named `branch`.
3. **Display the content of `greetings.txt`**: The workflow outputs the content of the `greetings.txt` file found in 
   the checked-out branch.

### YAML Workflow Example

```yaml
name: branch_checkout

on: [push]

jobs:
  external-workflow:
    runs-on: ubuntu-latest

    steps:
      # Step 1: Perform checkout from the repository and branch named 'branch'
      - name: Checkout external repository
        uses: actions/checkout@v3
        with:
          repository: abystoma/external-workflow
          ref: branch    # branch named 'branch'

      # Step 2: Display the contents of the greetings.txt file
      - name: Greetings
        run: echo "$(<greetings.txt)"


How to Use

1. Clone the repository:

   git clone https://github.com/Grze520/branch-checkout-action.git

2. Customize the workflow: You can modify the workflow to checkout other repositories or branches by updating 
   the repository and ref fields in the YAML workflow.

3. Run the workflow: Push changes to your GitHub repository, and check the workflow execution in the "Actions" tab 
   on GitHub.

Output

When the workflow runs, it will checkout the specified branch from the external repository. If the greetings.txt file 
exists in that branch, its contents will be printed as part of the job's output.

Technologies Used

 * GitHub Actions: Automating workflows and tasks.
 * Bash: Shell commands used in the workflow to process files.
 * YAML: Used to define GitHub Actions workflows.

License

This project is licensed under the MIT License. 
See the [LICENSE](./LICENSE) file for more details.

