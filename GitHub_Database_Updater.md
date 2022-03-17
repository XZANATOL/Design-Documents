# GitHub Database Updater

## Overview

A custom made Python project made during GirlScript Summer of Code OpenSource contest **GSSoC'21** that updates a JSON database file of a repository using GitHub API which runs through a GitHub Action flow.

It was a comprehensive project through a complete open source [repository](https://github.com/avinashkranjan/Amazing-Python-Scripts/) that had over 500 contributions. I was responsible for building the database, and the update script.

- [Workflow](https://github.com/avinashkranjan/Amazing-Python-Scripts/blob/master/.github/workflows/database_auto_updater.yml)
- [Updater Script](https://github.com/avinashkranjan/Amazing-Python-Scripts/blob/master/.github/scripts/Update_Database.py)
- [Database](https://github.com/avinashkranjan/Amazing-Python-Scripts/tree/master/Master%20Script)

<hr>

## Tech Stack Choices

### 1) GitHub Actions

We choosed this feature to automatically run the workflow on `closed && merged` pull requests.

### 2) PyGithub Module

We choosed this module to:
	* Interact with GitHub API v3.
	* Get access to the PR body and extract relevant info.
	* Get access to the database file in order to update it.

### 3) Regular Expressions **Regex**

It was used to extract relevant info from the provided PR body.

<hr>

## Workflow

>	Workflow will only run on `closed && merged` PRs.

1) Workflow provides the PR body & Authentication token to the update script.
2) Script extracts relevant info required to update the database with the help of Regex.
3) Script uses the token to authenticate through GitHub API and get read/write access to the database file.
4) Database is read and updated with the new data.
5) Scripts commit the new database file to the repository.

```mermaid
graph TD
    GitHub_Action -->|PR body<br>Authentication Token| Update_Script
    Update_Script -->|step_1: Read| Process["Extract Relevant info from PR body"]
    Update_Script -->|step_2: Authenticate| Github_API
    Github_API -->|Authenticated| Update_Script
    Update_Script -->|step_3: update| Update_Database_File
````

<hr>

## Downsides

* Authentication depends on a GitHub token that must be registered in both the owner GitHub account and in the repository secrets.
* In order to GitHub Actions workflows to run, the `.yml` file should be commited to the repo and not get merged from a PR. `GitHub security policies`

<hr>

## How I Learned this stack

1) GitHub Actions & GitHub API

I spent most of the time reading the documentations and experimenting. I have this [repo](https://github.com/XZANATOL/Github-actions-test/) where I used to test alot in the capabilities of both technologies.
- [GitHub Actions Documentation](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)
- [PyGithub API Documentation](https://pygithub.readthedocs.io/en/latest/introduction.html)

2) Regex
I used to practice alot on HackerRank