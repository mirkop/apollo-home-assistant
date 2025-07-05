You are working on YAML templates, automations, and integrations for Apollo Automation products (https://wiki.apolloautomation.com/), a company dedicated to high-quality, affordable, and community-driven home automation hardware. This workspace may include sensors, dashboards, and other smart home solutions.

## General Best Practices

- Write clear, concise YAML and follow Home Assistant best practices.
- Use template variables (e.g., `device_title`, `device_base_name`) for reusability and customization.
- Document all new variables, options, and features in the README.
- Follow the structure and naming conventions of existing files when adding new cards, automations, or integrations.
- Provide sensible default values for variables and document them.
- Ensure all code is easy to understand for Home Assistant users of all skill levels.
- Make solutions accessible, transparent, and community-friendly, reflecting Apollo Automation's values.

## Using the "scp" Shortcut for Git

### What is "scp"?

The `scp` shortcut is a convenient way to stage, commit, and push your changes to the git repository in a single step.

### How does it work?

When you use the `scp` shortcut, it executes the following commands in sequence:

```sh
git add . && git commit -m "your message" && git push
```

- `git add .` stages all changes in the repository.
- `git commit -m "your message"` commits the staged changes with your message.
- `git push` uploads the commit to the remote repository.

The commands are chained with double ampersands (`&&`), so each command only runs if the previous one succeeds. This ensures a smooth, reliable workflow.

### Example Usage

After making changes, simply use the `scp` shortcut. For example:

```
scp
```

You will be prompted for a commit message. The shortcut will then stage, commit, and push your changes automatically.

#### Best Practices for Using `scp`

- Write clear, descriptive commit messages that summarize your changes.
- Review your changes with `git status` or `git diff` before running `scp`.
- Use `scp` frequently to keep your work backed up and your repository up to date.

**This shortcut streamlines the process of staging, committing, and pushing changes, saving you time and reducing errors.**

---

If you have questions about this workflow or need help with Git or GitHub Copilot, feel free to ask!
