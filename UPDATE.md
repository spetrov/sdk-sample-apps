# Introduction

As our SDKs evolve over time, and introduce new features, optimizations, and bug fixes, we need to also maintain our sample apps. Staying up to date with the new changes is crucial. Updating sample apps to leverage new features in dependencies not only improves their functionality but also provides a better learning experience for our customers.

This article aims to define a successful strategy for updating sample apps when new features are introduced in the dependency SDKs. Discuss how to leverage automated testing and CI/CD pipelines to ensure the update process is smooth, reliable, and scalable.

# Objectives

- Reflect the latest SDK features in our sample apps.
- Maintain functionality and usability.
- Ensure that apps are  in good shape - compile with no issues, and all tests are passing.
- Reduce the manual effort required for updates.
- Ensure users can easily adopt the new features.

# Step-by-Step Strategy

## Prerequisites

- **Private Dependency Manager**: Assume that our SDKs are automatically published in a private dependency manager (e.g., Artifactory, Nexus, or private npm registry, etc).
- **Monitoring Sample Apps Repository**: Ensure the sample apps repository is configured to monitor the private dependency manager for updates. Tools like Dependabot can be used to detect changes and trigger GitHub action workflows, alerts, or pull requests.
- **iOS Sample apps**: Our iOS sample apps use Swift Package Manager (SPM). The sample apps repo will monitor the `develop` branch of the iOS SDK repositories for changes.

## 1. Detect SDKs Changes

Before updating a sample app, the first step is to detect changes introduced in the SDKs. This will help us to prioritize the changes. We can employ tools like Dependabot to automatically open pull requests when a new version of the SDK is detected.&#x20;

Another approach is to subscribe to notifications - e.g. monitor release notes, changelogs, JIRA tickets, or other release announcement channel(s).

## 2. Analyze Impact on Sample Apps and Plan

Once we detect changes in the SDKs we should analyze the impact and plan appropriately. This includes the following: 

- **Prioritize changes**: Address breaking changes first, followed by enhancements and new features.
- **Set goals**: Define what each sample app should demonstrate with the updated SDK.
- **Create timeline**: Plan milestones for implementing and testing updates.

We can automate to a certain extent the process by automatically creating JIRA tickets and assigning them for triage.

## 3. Automatic Dependency Updates and Testing

As mentioned above we can employ tools like **Dependabot** to automatically open pull requests when a new version of the SDK is released. Once the PR is open we can execute all unit and integration tests in order to verify that the new version of the SDK does not impact the sample apps.

- **Unit Tests**: Run all existing unit tests and add new ones if needed.
- **Integration Tests**: Verify end-to-end functionality.

## 4. Update Documentation

Keep the sample app’s documentation up-to-date with the changes:

- **Readme Files**: Reflect the new SDK version and any updated instructions for setup.
- **Code Comments**: Revise inline comments to explain any changes in functionality or usage.
- **Changelogs**: Add an entry detailing the update and its impact.

## 5. Merge and Release

Once updates are validated:

- Merge Changes: Integrate the updated branch into the main branch.
- Tag the Release: Tag the repository with the new version of the sample app.
- Announce the Update: Notify users of the update through release notes, blog posts, or community channels.

## 6. Monitor and Maintain

- Stay vigilant for issues or feedback related to the update:
- Bug Reports: Address any issues reported by users promptly.
- Further Updates: Monitor for subsequent SDK patches or minor updates and keep the app in sync.

By following these steps, you can ensure your sample applications remain relevant, functional, and aligned with the latest SDK versions, providing an excellent resource for developers.

```mermaid
graph TD
    A[Detect SDK Changes (Dependabot)] --> B[Automatic Dependency Updates and Testing]
    B --> C[Analyze Impact and Plan]
    C --> D[Update Documentation]
    D --> E[Merge and Release]
    E --> F[Monitor and Maintain]
```

