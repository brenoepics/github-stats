# [GitHub Stats Visualization](https://github.com/R055A/GitStats)

Generate daily updated visualizations of user and repository statistics from the GitHub [GraphQL](https://docs.github.com/en/graphql) and [REST](https://docs.github.com/en/rest) APIs using GitHub [Actions](https://docs.github.com/en/actions) and [Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets) for any combination of private and public repositories - dark mode supported.

![GitStats Overview - Light](https://raw.githubusercontent.com/R055A/GitStats/actions_branch/generated_images/overviewLightMode.svg#gh-light-mode-only)![GitStats Overview - Dark](https://raw.githubusercontent.com/R055A/GitStats/actions_branch/generated_images/overviewDarkMode.svg#gh-dark-mode-only)![GitStats Languages - Light](https://raw.githubusercontent.com/R055A/GitStats/actions_branch/generated_images/languagesLightMode.svg#gh-light-mode-only)![GitStats Languages - Dark](https://raw.githubusercontent.com/R055A/GitStats/actions_branch/generated_images/languagesDarkMode.svg#gh-dark-mode-only)

> This is a modification of [`jstrieb/github-stats`](https://github.com/jstrieb/github-stats) with many additional statistics, options and dark mode support

By default, statistical data for GitHub repositories an authenticated user either owns, has collaborative access to, or has 
otherwise contributed to are fetched from the GitHub API for visualization. 

Forked repositories are excluded by default. However, there are many options provided for including or excluding any 
repository and more using: [Statistics Options](#statistics-options).

Regardless of which repositories are included, the generated `All-time GitHub contributions given` statistic 
will always represent **all** GitHub contributions by the user.

It seems that view and clone statistical data for repositories that an authenticated user neither owns nor has 
collaborative access to are not included in the generated statistics being visualized.

It also seems that statistics for contributions to GitHub repositories that an authenticated user neither owns nor has collaborative access to possibly only includes repositories that exist on GitHub before the contributions do. Contribution statistics for repositories uploaded to GitHub after the contributions are made, so long that the configured commit email is associated with the user's GitHub account, can be included in the statistic visualizations by manually including the repository using the MORE_REPOS secret option in [Statistics Options](#statistics-options).

## Instructions

<details>
<summary>Click to view step-by-step instructions for generating your own GitHub statistics visualizations
</summary>

### Copy Repository

1. Click either link to start generating your own GitHub statistic visualizations: 
   1. [Generate your own copy of this repository without the commit history](https://github.com/R055A/GitStats/generate)
      * *Note: the first GitHub Actions workflow initiated at creation of the copied repository is expected to fail*
   2. [Fork a copy of this repository with the commit history configured to sync changes](https://github.com/R055A/GitStats/fork)
      * *Note: this copies all branches including the `action_branch` with statistics, but this can be overwritten*

### Generate a New Personal Access Token

2. Generate a personal access token by following these steps:
   1. If you are logged in, click this link to: [generate a new token](https://github.com/settings/tokens/new)
      * *Otherwise, to learn how to generate a personal access token: [read these instructions](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)*
   2. Name the token
   3. Select your preferred '***Expiration***' date
   4. Select `repo` for '<u>**Full control of private repositories**</u>'
   5. Select `read:user` to '<u>**Read ALL user profile data**</u>'
   6. Click the '***Generate token***' button
   7. Copy the generated token - there is only one opportunity provided for this

### Create ACCESS_TOKEN Secret

3. Create a repository secret for the personal access token by following these steps:
   1. If this is your copy of the repository, click this link to: [create a new secret](../../settings/secrets/actions/new)
      * *Otherwise, go to repository **Settings**, click the **Secrets** option, then click **New repository secret***
   2. Name the new secret: `ACCESS_TOKEN`
   3. Enter the generated **[personal access token](#generate-a-new-personal-access-token)** as the '*Value*'

### Run GitHub Actions Workflow

4. Manually generate GitHub statistics visualizations:
   1. This can be done using any of the following two GitHub Actions workflows:
      1. For the **first time**, or to **reset stored statistics** (although this is done with every push to master):
         * Click the link to: [go to the **Generate Git Stats Images** GitHub Actions workflow](../../actions/workflows/non_auto_generate_stat_images.yml)
         > *This is required if the `actions_branch` branch is not created, as it is created when run*
      2. Otherwise, for **updating** generated statistics visualizations (although this is automatically done daily):
         * Click the link to: [go to the **Auto Update Stats Images** GitHub Actions workflow](../../actions/workflows/auto_update_stat_images.yml)
         > *This requires the `actions_branch` branch to first be created with generated statistics visualizations*
   2. With the GitHub Actions page open, click the '***Run workflow***' dropdown menu button
   3. Select `Branch: master` from the '***Use workflow from***' dropdown list
   4. Click the '***Run workflow***' button

### View Generated Statistics

5. Following the successful completion of a workflow, generated statistics visualizations can be viewed:
   1. In the `generated_images` directory in the `actions_branch` branch with the following image links:
      1. [Language statistics using @media prefers-color-scheme for dark and light mode - not tested](../../blob/actions_branch/generated_images/languages.svg)
      2. [Language statistics in *light* mode only](../../blob/actions_branch/generated_images/languagesLightMode.svg) 
      3. [Language statistics in **dark** mode only](../../blob/actions_branch/generated_images/languagesDarkMode.svg)
      4. [Overview statistics using @media prefers-color-scheme for dark and light mode - not tested](../../blob/actions_branch/generated_images/overview.svg)
      5. [Overview statistics in *light* mode only](../../blob/actions_branch/generated_images/overviewLightMode.svg)
      6. [Overview statistics in **dark** mode only](../../blob/actions_branch/generated_images/overviewDarkMode.svg)

### Display Generated Statistics

6. To display the generated statistics, constant URLs can be used for images that are updated daily:
   1. For a GitHub profile README.md, attach `#gh-light-mode-only` and `#gh-dark-mode-only` to light and dark raw image links, respectively, such as:
      1. For generated language statistics visualizations (replacing `<username>` with your GitHub username):
      ```md
      ![](https://raw.githubusercontent.com/<username>/GitStats/actions_branch/generated_images/languagesLightMode.svg#gh-light-mode-only)![](https://raw.githubusercontent.com/<username>/GitStats/actions_branch/generated_images/languagesDarkMode.svg#gh-dark-mode-only)
      ```
      2. For generated overview statistic visualizations (replacing `<username>` with your GitHub username):
      ```md
      ![](https://raw.githubusercontent.com/<username>/GitStats/actions_branch/generated_images/overviewLightMode.svg#gh-light-mode-only)![](https://raw.githubusercontent.com/<username>/GitStats/actions_branch/generated_images/overviewDarkMode.svg#gh-dark-mode-only)
      ```
   2. For websites, use the **raw** image URLs for any suitable image from the above [View Generated Statistics](#view-generated-statistics) links.
      > Note: I have not used the images on any website other than the following GitHub pages:
      > > [https://r055a.github.io/profile/statistics/](https://r055a.github.io/profile/statistics/)
      > 
      > > [https://r055a.github.io/university-projects/statistics/](https://r055a.github.io/university-projects/statistics/)
    
</details>

## Statistics Options

<details>
<summary>Click to view Repository Secrets for customizing GitHub statistic visualizations
</summary>

* Secret *Name*: `EXCLUDED`
  * for excluding listed repositories from being included in the generated statistic visualizations
  * enter *Value* in the following format (separated by commas):
    * `[owner/repo],[owner/repo],...,[owner/repo]`
  * example:
    * `jstrieb/github-stats,rahul-jha98/github-stats-transparent,idiotWu/stats`
* Secret *Name*: `ONLY_INCLUDED`
  * for **ONLY** including listed repositories in the generated statistic visualizations
  * enter *Value* in the following format (separated by commas):
    * `[owner/repo],[owner/repo],...,[owner/repo]`
  * example:
    * `R055A/GitStats,R055A/R055A`
* Secret *Name* `EXCLUDED_LANGS`
  * for excluding listed languages from being included in the generated statistic visualizations
  * enter *Value* in the following format (separated by commas):
    * `[language],[language],...,[language]`
  * example:
    * `HTML,Jupyter Notebook,Makefile,Dockerfile`
* Secret *Name* `INCLUDE_FORKED_REPOS`
  * for including forked repositories in the generated statistic visualizations
    - `false` by default
  * enter *Value* in the following format:
    * `<boolean>`
  * examples:
    * `true`
* Secret *Name* `EXCLUDE_CONTRIB_REPOS`
  * for excluding repositories (pull request) contributed to in the generated statistic visualizations
    - `false` by default
  * enter *Value* in the following format:
    * `<boolean>`
  * examples:
    * `true`
* Secret *Name* `EXCLUDE_ARCHIVE_REPOS`
  * for excluding archived repositories in the generated statistic visualizations
    - `false` by default
  * enter *Value* in the following format:
    * `<boolean>`
  * examples:
    * `true`
* Secret *Name* `EXCLUDE_PRIVATE_REPOS`
  * for excluding private repositories in the generated statistic visualizations
    - `false` by default
  * enter *Value* in the following format:
    * `<boolean>`
  * examples:
    * `true`
* Secret *Name* `EXCLUDE_PUBLIC_REPOS`
  * for excluding public repositories in the generated statistic visualizations
    - `false` by default
  * enter *Value* in the following format:
    * `<boolean>`
  * examples:
    * `true`
* Secret *Name* `MORE_REPOS`
  * for including repositories that are otherwise not included in the generated statistic visualizations
    - such as imported repositories with contributions
  * enter *Value* in the following format (separated by commas):
    * `[owner/repo],[owner/repo],...,[owner/repo]`
  * example:
    * `R055A/GitStats,R055A/R055A`
* Secret *Name* `MORE_COLLABS`
  * for adding a constant value to the generated repository collaborators statistic
    - such as for collaborators that are otherwise not represented
  * enter *Value* in the following format:
    * `<int>`
  * example:
    * `4`
* Secret *Name* `STORE_REPO_CLONES`
  * for storing generated repository clone statistic visualization data beyond the 14 day-limit GitHub API allows 
    - `true` by default
  * enter *Value* in the following format:
    * `<boolean>`
  * examples:
    * `false`
* Secret *Name* `STORE_REPO_VIEWS`
  * for storing generated repository view statistic visualization data beyond the 14 day-limit GitHub API allows 
    - `true` by default
  * enter *Value* in the following format:
    * `<boolean>`
  * examples:
    * `false`
* Secret *Name* `REPO_VIEWS`
  * for adding a constant value to the generated repository view statistics
    - such as for when the stored data is reset or when importing stat data from elsewhere
    - requires being removed within 14 days after the first workflow is run (with `LAST_VIEWED`)
    - requires corresponding `LAST_VIEWED` and `FIRST_VIEWED` Secrets
  * enter *Value* in the following format:
    * `<int>`
  * example:
    * `5000`
* Secret *Name* `LAST_VIEWED`
  * for updating the date the generated repository view statistics data is added to storage from
    - such as for when the stored data is reset or when importing stat data from elsewhere
    - requires being removed within 14 days after the first workflow is run (with `REPO_VIEWS`)
    - may require corresponding `REPO_VIEWS` and `FIRST_VIEWED` Secrets
  * enter *Value* in the following format:
    * `YYYY-MM-DD`
  * example:
    * `2020-10-01`
* Secret *Name* `FIRST_VIEWED`
  * for updating the '*as of*' date the generated repository view statistics data is stored from
    - such as for when the stored data is reset or when importing stat data from elsewhere
    - may require corresponding `REPO_VIEWS` and `LAST_VIEWED` Secrets
  * enter *Value* in the following format:
    * `YYYY-MM-DD`
  * example:
    * `2021-03-31`
* Secret *Name* `REPO_CLONES`
  * for adding a constant value to the generated repository clone statistics
    - such as for when the stored data is reset or when importing stat data from elsewhere
    - requires being removed within 14 days after the first workflow is run (with `LAST_CLONED`)
    - requires corresponding `LAST_CLONED` and `FIRST_CLONED` Secrets
  * enter *Value* in the following format:
    * `<int>`
  * example:
    * `2500`
* Secret *Name* `LAST_CLONED`
  * for updating the date the generated repository clone statistics data is added to storage from
    - such as for when the stored data is reset or when importing stat data from elsewhere
    - requires being removed within 14 days after the first workflow is run (with `REPO_CLONES`)
    - may require corresponding `REPO_CLONES` and `FIRST_CLONED` Secrets
  * enter *Value* in the following format:
    * `YYYY-MM-DD`
  * example:
    * `2020-10-01`
* Secret *Name* `FIRST_CLONED`
  * for updating the '*as of*' date the generated repository clone statistics data is stored from
    - such as for when the stored data is reset or when importing stat data from elsewhere
    - may require corresponding `REPO_CLONES` and `LAST_CLONED` Secrets
  * enter *Value* in the following format:
    * `YYYY-MM-DD`
  * example:
    * `2021-04-01`
</details>

## Support the Project

There are a few things you can do to support the project:

- Star the repository (and follow me and/or [`jstrieb`](https://github.com/jstrieb) on GitHub for more)
- Share and upvote on sites
- Report any bugs, glitches, or errors that you find
- Spare a donation to a worthy cause

## Related Projects
 - The repository this modifies is also inspired by a desire to improve upon
  [anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
 - More influencing repositories, also modifications of [`jstrieb/github-stats`](https://github.com/jstrieb/github-stats) are:
   - [rahul-jha98/github-stats-transparent](https://github.com/rahul-jha98/github-stats-transparent)
   - [idiotWu/stats](https://github.com/idiotWu/stats)
 - Makes use of [GitHub Octicons](https://primer.style/octicons/) to precisely
   match the GitHub UI
