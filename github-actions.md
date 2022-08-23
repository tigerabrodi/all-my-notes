# Chapter 2

Core components and concepts of Github Actions:

- Events
- Jobs
- Steps
- Actions
- Runners

## Events

Github actions are event-driven. Events are activities that trigger workflows.

### Scheduled Events

Run at a specified time, they used the POSIX cron syntax.

### Manual Events

You can run Github actions manually via two types of events: **workflow_dispatch** and **repository_dispatch**.

### Webhook Events

Workflow that gets triggered when Github webhook events are run, when a specific activity has happened on Github or in your repository, such as issue and pull request open, and so on.

## Jobs

A job is a set of steps that run on the same runner.

## Steps

Steps are individual tasks that can run commands, such as shell commands or an action, in a job within a workflow. Steps can share data, because within their job they run in the same runner.

## Actions

Actions are standalone commands that can be portable. They are used within steps to create a job. They can be created by the community.

## Runners

A runner is a server application, that runs on a job from a Github Actions workflow. In general, a runner runs one job at a time and reports its progress to Github.

## Basics of workflows

Github Actions must live in the `.github/workflows` directory and must have either `.yml` or `.yaml` file extension.

## Basics of workflow file syntax

**name:** Represents the name of the workflow.

**on:** Specifies which event or events will trigger the workflow.

**jobs:** Workflow runs can have one or more jobs.

---

You can also set up CI in the actions tab in your repo.

# Chapter 3
