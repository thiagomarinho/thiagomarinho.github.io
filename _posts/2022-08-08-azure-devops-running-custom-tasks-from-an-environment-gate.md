---
layout: post
title: "Azure Devops - Running custom tasks from an environment gate"
date: 2022-08-08 22:03:00 -0000
categories: azure-devops pipelines custom-extension
---

My team was exploring the option to create an [Azure Devops Custom Task](https://github.com/microsoft/azure-pipelines-tasks/blob/master/docs/authoring/servertaskauthoring.md) that should run in an [Environment Gate](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/approvals?view=azure-devops&tabs=check-pass).
Running some tests with our sample extension, we noticed that, for some reason, we never managed to see the custom task available to run from a gate. After a timely help from one of my team coworkers and his spetacular google skills, we found [the issue and how to fix it](https://developercommunity.visualstudio.com/t/custom-servergate-not-available-in-environment-che/1576665#T-N1599182):

> (...) Based on what I know so far, feature flag “Pipelines.Checks.EnableAllTaskChecks” need to be enable on ourside(Microsoft).

So, if you ever see yourself in the same situation, send a request to Microsoft support team so you can get this flag enabled :).
