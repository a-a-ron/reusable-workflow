<!--
  <<< Author notes: Header of the course >>>
  Read <https://skills.github.com/quickstart> for more information about how to build courses using this template.
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses Creative Commons Attribution 4.0 International.
-->

# Reusable Workflows and Matrix Strategies

_Make a workflow reusable, call it in another workflow, and use a matrix strategy to run multiple versions_

<!--
  <<< Author notes: Start of the course >>>
  Include start button, a note about Actions minutes,
  and tell the learner why they should take the course.
  Each step should be wrapped in <details>/<summary>, with an `id` set.
  The start <details> should have `open` as well.
  Do not use quotes on the <details> tag attributes.
-->

<!--step0-->

TBD-welcome-paragraph

- **Who is this for**: TBD-audience.
- **What you'll learn**: TBD-objective.
- **What you'll build**: TBD-result.
- **Prerequisites**: TBD-prerequisites.
- **How long**: This course is TBD-step-count steps long and takes less than TBD-duration to complete.

## How to start this course

1. Above these instructions, right-click **Use this template** and open the link in a new tab.
   ![Use this template](https://user-images.githubusercontent.com/1221423/169618716-fb17528d-f332-4fc5-a11a-eaa23562665e.png)
2. In the new tab, follow the prompts to create a new repository.
   - For owner, choose your personal account or an organization to host the repository.
   - We recommend creating a public repository—private repositories will [use Actions minutes](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions).
   ![Create a new repository](https://user-images.githubusercontent.com/1221423/169618722-406dc508-add4-4074-83f0-c7a7ad87f6f3.png)
3. After your new repository is created, wait about 20 seconds, then refresh the page. Follow the step-by-step instructions in the new repository's README.

<!--endstep0-->

<!--
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
  TBD-step-1-notes.
-->

<details id=1>
<summary><h2>Step 1: Make a workflow reusable</h2></summary>

_Welcome to "TBD-course-name"! :wave:_

TBD-step-1-information

**What is _TBD-term-1_**: TBD-definition-1

### :keyboard: Update the workflow file with the resuable workflow event trigger

1. Open a new browser tab, and navigate to this same repository. Then, work on the steps in your second tab while you read the instructions in this tab.
1. Navigate to the **Code** tab.
1. From the **main** branch dropdown, click on the **reusable-workflow** branch.
1. Navigate to the `.github/workflows/` folder, then select the **reusable-workflow.yml** file.
1. Replace the `workflow_dispatch` event trigger with the `workflow_call` event trigger. It should look like the following:
   
   ```yaml
      name: Reusable Workflow

      on:
        workflow_call:
          inputs:
            node:
              required: true
              type: string
   ```
1. To commit your changes, click **Start commit**, and then **Commit changes**.
1. Wait about 20 seconds for actions to run, then refresh this page (the one you're following instructions from) and an action will automatically close this step and open the next one.

</details>

<!--
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-2-notes.
-->

<details id=2>
<summary><h2>Step 2: Add a job to call the reusable workflow</h2></summary>

_You did TBD-step-1-name! :tada:_

TBD-step-2-information

**What is _TBD-term-2_**: TBD-definition-2

### :keyboard: Activity: Add a job to your workflow to call the reusable workflow

1. Navigate to the `.github/workflows/` folder and open the `my-starter-workflow.yml` file.
1. Add a new job to the workflow called `call-reusable-workflow`.
1. Add a `uses` command and path the command to the `reusable-workflow.yml` file.
1. Add a `with` command to pass in a `node` paramater and set the value to `14`. 

   ```yaml
   call-reusable-workflow:
     uses: ./.github/workflows/reusable-workflow.yml
     with:
       node: 14   
   ```
1. To commit your changes, click **Start commit**, and then **Commit changes**.
1. Wait about 20 seconds for actions to run, then refresh this page (the one you're following instructions from) and an action will automatically close this step and open the next one.

</details>

<!--
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-3-notes.
-->

<details id=3>
<summary><h2>Step 3: Add a matrix strategy to your workflow</h2></summary>

_Nice work finishing TBD-step-2-name :sparkles:_

TBD-step-3-information

**What is _TBD-term-3_**: TBD-definition-3

### :keyboard: Use a matrix strategy to run multiple versions

1. In the same `my-starter-workflow.yml` file, add a `strategy` keyword under the `call-reusable-workflow` job.
1. Under `strategy`, add a `matrix` keyword.
1. Define the `nodeversion` variable to run over the following versions of node `[14, 16, 18, 20]`.
1. Replace the hard-coded `node` paramter of 14 used in the `with` command, and call the `nodeversion` in the matrix by using the following syntax `${{ matrix.nodeversion }}.  

   ```yaml
   call-reusable-workflow:
     strategy:
       matrix:
         nodeversion: [14, 16, 18, 20]
     uses: ./.github/workflows/reusable-workflow.yml
     with:
       node: ${{ matrix.nodeversion }}   
   ```
1. To commit your changes, click **Start commit**, and then **Commit changes**.
1. Wait about 20 seconds for actions to run, then refresh this page (the one you're following instructions from) and an action will automatically close this step and open the next one.

</details>

<!--
  <<< Author notes: Step 4 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-4-notes.
-->

<details id=4>
<summary><h2>Step 4: Merge your changes</h2></summary>

_Nicely done TBD-step-3-name! :partying_face:_

TBD-step-4-information

You can now [merge](https://docs.github.com/en/get-started/quickstart/github-glossary#merge) your pull request!

### :keyboard: Activity 1 : Create and merge your pull request

1. In your repo, click on the **Pull requests** tab.
1. Click on the **Post welcome comment workflow** pull request.
1. Click **Merge pull request**, then click **Confirm merge**.
1. Optionally, click **Delete branch** to delete your `reusable-workflow` branch.
1. Wait about 20 seconds for actions to run, then refresh this page (the one you're following instructions from) and an action will automatically close this step and open the next one.


</details>

<!--
  <<< Author notes: Step 5 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-5-notes.
-->

<details id=5>
<summary><h2>Step 5: Trigger your workflow and view the Actions logs</h2></summary>

_Almost there TBD-step-4-name! :heart:_

### :keyboard: Activity 2 : Run the My Starter Workflow

1. Navigate to the **Actions** tab in your repo.
1. Choose the **My Starter Workflow** workflow from the left, and select the **Run workflow** button and run the workflow on the **Main** branch.
1. Refresh the page and then select the **My Starter Workflow** from the workflow runs queue.

Notice the list of build jobs on the left. One for the `build` job and four for the different node versions (14, 16, 18, 20) that you are running from your matrix. When one of the node version jobs complete, you can select that job and view the Actions logs for the **Output the input value**. This will print out the message from the reusable workflow file.

</details>

<!--
  <<< Author notes: Finish >>>
  Review what we learned, ask for feedback, provide next steps.
-->

<details id=X>
<summary><h2>Finish</h2></summary>

_Congratulations friend, you've completed this course!_

<img src=TBD-celebrate-image alt=celebrate width=300 align=right>

Here's a recap of all the tasks you've accomplished in your repository:

- Steps to share your workflows with your organization

### What's next?

- TBD-continue.
- [We'd love to hear what you thought of this course](TBD-feedback-link).
- [Take another TBD-organization Course](https://github.com/TBD-organization).
- [Read the GitHub Getting Started docs](https://docs.github.com/en/get-started).
- To find projects to contribute to, check out [GitHub Explore](https://github.com/explore).

</details>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Get help: [TBD-support](TBD-support-link) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2022 TBD-copyright-holder &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [CC-BY-4.0 License](https://creativecommons.org/licenses/by/4.0/legalcode)
