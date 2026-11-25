# First-Run Checklist

## Before the first session
- [ ] Open the actual XIVA repository as the workspace, not a parent folder containing unrelated projects.
- [ ] Confirm which agent adapter Msty is using. A normal chat model selection is not necessarily the Agent Mode model.
- [ ] Confirm the local model server is running and the exact model ID is selected.
- [ ] Start with read-only or review-before-edit permissions.
- [ ] Enable `xiva-project-assistant` and only the specialist skill needed for the task.
- [ ] Do not provide production credentials, real member data, or patient records.

## Read-only smoke test
Send:

> Inspect this repository without changing any files. Identify the application entry points, PHP version evidence, database access pattern, JavaScript conventions, and documentation locations. For each conclusion, provide the file path and a short explanation. Clearly label anything you cannot verify. Do not infer missing details.

Expected behavior:
- Agent reads real files.
- It cites actual paths and identifiers.
- It distinguishes confirmed facts from unknowns.
- It does not edit files or invent project structure.

## Controlled edit test
Choose a low-risk documentation typo or a small isolated UI change. Ask for a plan, approve the focused change, then inspect the diff yourself.

## Permissions
Allow individual read/write actions when practical. Avoid broad "always allow" permissions for terminal commands, filesystem access, database operations, or commands outside the workspace.
