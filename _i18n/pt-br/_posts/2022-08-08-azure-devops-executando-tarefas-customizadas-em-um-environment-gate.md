---
layout: post
title: "Azure Devops - Executando tarefas customizadas em um Environment Gate"
date: 2022-08-08 22:03:00 -0000
categories: azure-devops pipelines custom-extension portuguese
---

Meu time estava explorando a possibilidade de criar uma [tarefa customizada no Azure Devops](https://github.com/microsoft/azure-pipelines-tasks/blob/master/docs/authoring/servertaskauthoring.md) que seria executada em um [Environment Gate](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/approvals?view=azure-devops&tabs=check-pass).
Após alguns testes com uma extensão de exemplo que criamos, percebemos que, por algum motivo, nunca conseguimos ver nossa task customizada disponível para ser executada a partir do gate. Após uma ajuda extraordinária de um de nossos colegas do time com fascinantes skills googlísticas, descobrimos [qual era o problema e como corrigí-lo](https://developercommunity.visualstudio.com/t/custom-servergate-not-available-in-environment-che/1576665#T-N1599182):

> (...) Até onde sei, a feature flag “Pipelines.Checks.EnableAllTaskChecks” precisa ser habilitada por nós da Microsoft.

Então, se você eventualmente tiver um problema similar, abre um ticket pra o time de supporte da Microsoft pra que eles habilitem essa flag pra você :).
