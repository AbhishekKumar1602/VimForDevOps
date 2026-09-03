# I. Diff, Shell Integration, And Validation

The important DevOps goal is not to run every tool inside Vim. It is to make a controlled edit, review the difference, and validate the result before deployment.

## Compare Files With Vimdiff

From the shell:

```bash
vimdiff config.before.yaml config.after.yaml
```

Essential diff commands:

| Command | Result |
| --- | --- |
| `]c` / `[c` | Next / previous changed block. |
| `do` | Obtain the other window's version of the current diff block. |
| `dp` | Put the current version into the other window. |
| `:diffupdate` | Recalculate diff highlighting. |

Before using `do` or `dp`, confirm which side contains the version you want. Undo immediately if content moves in the wrong direction.

## Run A Shell Command From Vim

```vim
:!COMMAND
```

Examples:

```vim
:!git status --short
:!git diff -- %
:!shellcheck %
:!yamllint %
:!ansible-lint %
:!terraform validate
:!nginx -t
```

`%` expands to the current filename in many Ex commands. Use `:file` first if the filename is uncertain.

It is also completely acceptable to save the file, return to the normal shell, and run the validator there. The objective is validation, not keeping every action inside Vim.

## Final DevOps Workflow

After an edit:

```vim
:update
:!git diff --check
:!git diff --stat
:!git diff
```

Then run the correct formatter, syntax checker, test, policy check, or infrastructure plan required by the technology before committing or deploying.

Examples include:

```text
JSON          jq . FILE
YAML          yamllint FILE
Shell         shellcheck FILE
Ansible       ansible-lint FILE
Terraform     terraform fmt / terraform validate / terraform plan
Nginx         nginx -t
Kubernetes    the validation/dry-run command used by your deployment workflow
```

Quickfix configuration, embedded terminal workflows, command-output insertion, and advanced bulk-edit automation are intentionally excluded from this learning path.
