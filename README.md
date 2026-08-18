# Linux System Security: Access Control Assessment

## Project Overview
This project details a technical security assessment of a Linux-based file system. The objective was to inspect existing IT assets within a research environment, identify permission-based vulnerabilities, and execute precise command-line remediations to secure sensitive data.

## Scenario
Working with a corporate research team, I conducted an audit of their primary workspace (`/home/researcher2/projects`). The initial scan indicated that the directory was vulnerable to internal threats due to misconfigured authorization. Permissions across multiple files and subdirectories required immediate correction to authorize only appropriate users and revoke unauthorized access.

## Key Findings & Vulnerabilities
The command-line investigation (`ls -la`) exposed the following misconfigurations:
* **Violation of Separation of Duties:** Global write permissions were active on shared project files, allowing any system user to alter data (`Other = read, write`).
* **Improper Archive Protection:** The `.project_x.txt` hidden file lacked strict read-only protections, maintaining active write permissions for users and groups.
* **Over-Privileged Directories:** The `drafts` folder allowed execution by group members, contradicting the requirement for owner-isolated access.

## Technical Controls & Methodologies Applied
* **Linux Command Line Interface (CLI):** Utilized `chmod` with symbolic arguments (e.g., `u-w,g-w,g+r`, `o-w`, `g-x`) to precisely alter 10-character permission masks.
* **Access Control Enforcement:** Aligned system settings with the Principle of Least Privilege by systematically removing unauthorized write and execute capabilities.
* **Security Verification:** Implemented continuous verification by validating permission states before and after execution to ensure control effectiveness.

## Documentation Included
* **linux_permissions_audit_report.pdf:** A comprehensive technical log documenting the full audit lifecycle, including terminal outputs, permission string deconstruction, and executed mitigation commands.
*  **Current file permissions.pdf** A character mask of permissions is set before the audit starts
