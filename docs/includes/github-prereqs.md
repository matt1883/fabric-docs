---
title: Include file for GitHub prereqs
description: Include file for the GitHub prereqs. This include file is referenced in this repo and also in an article in the Power BI repo.
author: maggiesMSFT
ms.author: maggies
ms.topic: include
ms.custom: 
ms.date: 12/20/2023
---

To integrate Git with your Microsoft Fabric workspace, you need to set up the following prerequisites for both Fabric and Git.

### Fabric prerequisites

To access the Git integration feature, you need one of the following:

- [Power BI Premium license](/power-bi/enterprise/service-premium-what-is). A Power BI premium license supports all Power BI items only.
- [Fabric capacity](/fabric/enterprise/licenses#capacity). A Fabric capacity is required to use all supported Fabric items. If you don't have one yet, [sign up for a free trial](/fabric/get-started/fabric-trial).

In addition, the following [tenant switches](/fabric/admin/about-tenant-settings) must be enabled from the Admin portal:

- [Users can create Fabric items](/fabric/admin/fabric-switch)
- [Users can synchronize workspace items with their Git repositories](/fabric/admin/git-integration-admin-settings#users-can-synchronize-workspace-items-with-their-git-repositories-preview)
- For GitHub users only: [Users can synchronize workspace items with GitHub repositories](/fabric/admin/git-integration-admin-settings#users-can-synchronize-workspace-items-with-github-repositories-preview)

These switches can be enabled by the tenant admin, capacity admin, or workspace admin, depending on your [organization's settings](/fabric/admin/delegate-settings).

### Git prerequisites

Git integration is currently supported for Azure DevOps and GitHub. To use Git integration with your Fabric workspace, you need the following in either Azure DevOps or GitHub:

### [Azure DevOps](#tab/azure-devops)

- An active Azure account registered to the same user that is using the Fabric workspace. <a href="https://azure.microsoft.com/products/devops/" target="_blank">Create a free account</a>.
- Access to an existing repository.

### [GitHub](#tab/github)

- An active GitHub account. <a href="https://github.com" target="_blank">Create a GitHub account</a>.
- *One* of the following <a href="https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens" target="_blank">personal access tokens</a>:

  - A <a href="https://github.com/settings/personal-access-tokens/new" target="_blank">fine-grained token</a> (recommended) with **Contents** read and write permission under the repository permissions:
  
    :::image type="content" source="/fabric/includes/media/github-prereqs/fine-grained-token.png" alt-text="Screenshot of GitHub token permissions.":::

    To use this token with GitHub Enterprise, follow <a href="https://github.blog/2022-10-18-introducing-fine-grained-personal-access-tokens-for-github/" target="_blank">these directions</a>.
  
  - A <a href="https://github.com/settings/tokens/new" target="_blank">Create a GitHub classic token</a> with repo scopes enabled:

    :::image type="content" source="/fabric/includes/media/github-prereqs/classic-token.png" alt-text="Screenshot of GitHub classic token scopes.":::

---
