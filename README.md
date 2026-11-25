# XIVA Msty Agent Kit

A starter skill pack and session configuration for using Qwen2.5-Coder locally as a **coding assistant** for the XIVA repository.

## Package contents

- `skills/`: 8 independent skills. Each folder contains a `SKILL.md`.
- `config/AGENT-SESSION-INSTRUCTIONS.md`: reusable session-level instructions.
- `config/MODEL-SETTINGS.md`: conservative model/runtime recommendations.
- `config/FIRST-RUN-CHECKLIST.md`: safe validation sequence.
- `config/TASK-PROMPTS.md`: copy-ready prompts for common tasks.

## Install skills in Msty Studio

Msty's UI differs between Studio 2.x and 3.x. In current Studio 3.x documentation, Skills are managed in the Skills area; in 2.x, use Settings > Agent Mode > Skills Studio.

Recommended approach:
1. Open Msty Studio's Skills / Skills Studio.
2. Create a skill or import each skill folder, depending on the controls available in your installed version.
3. For each skill, use the folder name as the stable skill ID and paste/import its `SKILL.md`.
4. Add tags if supported: `xiva`, `php`, `mysql`, `javascript`, `architecture`, `documentation`, `security`, `debugging`.
5. Enable only the skills relevant to the current task. Start with `xiva-project-assistant` plus one or two specialist skills.

If your Msty version offers a GitHub repository import rather than local folder import, put this package in a private repository and add the repository through Discover. Do not assume that simply placing files in an arbitrary folder automatically installs them.

## Recommended model roles

- **Qwen2.5-Coder 7B Instruct Q4_K_M**: primary model for code explanation, focused implementation assistance, debugging, SQL review, and small cross-file changes.
- **Qwen2.5-Coder 3B Instruct Q4_K_M**: secondary model for quick explanations, simple code navigation, small documentation edits, and lightweight tasks.

Do not route complex architecture decisions or high-impact claim/benefit changes to either model without developer review. The 3B model is not a dependable substitute for the 7B model on multi-step work.

## Important distinction

Skills are instructions. They do not grant filesystem, terminal, browser, database, or IDE access. Agent capabilities depend on the selected Msty agent adapter, workspace, available tools, and permission settings.

Start in read-only / review-before-edit mode. Never allow unattended production database changes, destructive commands, deployment, credential access, or broad filesystem access.
