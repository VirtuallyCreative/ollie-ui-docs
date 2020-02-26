---
title: Sharing & Security
weight: 3
template: docs
---

## Security Checks
A security audit is an assessment of package dependencies for security vulnerabilities. Security audits help you protect your package’s users by enabling you to find and fix known vulnerabilities in dependencies that could cause data loss, service outages, unauthorized access to sensitive information, or other issues.

## Packages in Use
Since HopeJS uses many packages to help scaffold the experience for developers, making sure developers pay attention to NPM's security audit checks are important as project dependencies should only be updated for the project itself, not in HopeJS.

#### Reviewing and acting on the security audit report
Running npm audit will produce a report of security vulnerabilities with the affected package name, vulnerability severity and description, path, and other information, and, if available, commands to apply patches to resolve vulnerabilities. For more information on the fields in the audit report, see “About audit reports ”

#### Security vulnerabilities found with suggested updates
If security vulnerabilities are found and updates are available, you can either:

Run the npm audit fix subcommand to automatically install compatible updates to vulnerable dependencies.

## Security vulnerabilities found requiring manual review
If security vulnerabilities are found, but no patches are available, the audit report will provide information about the vulnerability so you can investigate further.

Command-line audit report requiring manual review
To address the vulnerability, you can

- [Check for mitigating factors](https://docs.npmjs.com/auditing-package-dependencies-for-security-vulnerabilities#check-for-mitigating-factors)
- [Update dependent packages if a fix exists](https://docs.npmjs.com/auditing-package-dependencies-for-security-vulnerabilities#update-dependent-packages-if-a-fix-exists)
- [Fix the vulnerability](https://docs.npmjs.com/auditing-package-dependencies-for-security-vulnerabilities#fix-the-vulnerability)
- [Open an issue in the package or dependent package issue tracker](https://docs.npmjs.com/auditing-package-dependencies-for-security-vulnerabilities#open-an-issue-in-the-package-or-dependent-package-issue-tracker)

## Sharing
Sharing is an aspect added to Ollie-UI to help developers rapidly prototype. With the concept built around rapid feedback, using the `$ npm run share` command creates a tunnel pointing to the `src` dev build for outside-the-network access. Personally, I use this to let other involved business teams quickly see something you wish to show them for feedback.