# VIM For DevOps

A small, plugin-free Vim learning repository for DevOps engineers who need to edit configuration files, inspect logs, review changes, and work directly on Linux servers or SSH sessions.

The goal is deliberately limited:

> Learn enough Vim to work safely and comfortably during normal DevOps tasks — **not to master Vim**.

## What You Will Learn

- Open, save, exit, and recover safely.
- Understand the Vim modes needed for daily work.
- Navigate configuration files and logs efficiently.
- Edit, delete, copy, paste, indent, undo, redo, and repeat changes.
- Search and perform controlled replacements.
- Use Visual and block editing for repeated line changes.
- Work with basic buffers and split windows.
- Handle whitespace, line endings, configuration indentation, and logs.
- Compare files with Vimdiff.
- Review Git changes and run technology-specific validators.
- Apply a safe production-editing workflow.

Advanced Vim topics such as macros, Quickfix automation, argument-list loops, saved sessions, deep register workflows, and Vimscript/plugin development are intentionally excluded from the required learning path.

## Repository Structure

```text
VIM-For-Devops/
│
├── cheat-sheets/
│   │
│   └── vim-devops-cheat-sheet.md
│
├── notes/
│   │
│   ├── 01-introduction.md
│   ├── 02-start-save-exit-help.md
│   ├── 03-modes-and-navigation.md
│   ├── 04-editing-and-undo.md
│   ├── 05-search-replace-sort-filter.md
│   ├── 06-visual-mode-and-registers.md
│   ├── 07-files-buffers-windows-tabs.md
│   ├── 08-config-files-and-logs.md
│   └── 09-diff-shell-and-validation.md
│
├── practice/
│   │
│   ├── practice.txt
│   └── repeated-practice.md
│
├── .editorconfig
├── .gitignore
├── .vimrc
└── README.md
```


## Start Here

Read the required notes in this order:

```text
01-introduction.md
        ↓
02-start-save-exit-help.md
        ↓
03-modes-and-navigation.md
        ↓
04-editing-and-undo.md
        ↓
05-search-replace-sort-filter.md
        ↓
06-visual-mode-and-registers.md
        ↓
07-files-buffers-windows-tabs.md
        ↓
08-config-files-and-logs.md
        ↓
09-diff-shell-and-validation.md
```

Then practise with:

```bash
vim practice/practice.txt
```

and follow:

```text
practice/repeated-practice.md
```

Recommended learning loop:

```text
Read → Understand → Practice → Repeat → Use At Work
```

## Production Safety Rules

1. Use read-only mode when you only need to inspect a file:

   ```bash
   view FILE
   ```

2. Do not practise unfamiliar commands on production files.
3. Prefer Git-controlled source or a recoverable backup before broad changes.
4. Prefer confirmed replacement when scope is uncertain:

   ```vim
   :%s/old/new/gc
   ```

5. Review the complete diff before deployment.
6. Run the correct formatter, syntax check, test, policy check, or infrastructure plan required by the technology.
7. Use `sudoedit` / `sudo -e` for authorized privileged edits where appropriate rather than habitually launching the whole editor as root.
8. Prefer the normal configuration-management/deployment workflow over ad-hoc production edits when one exists.
9. Never put real passwords, tokens, credentials, certificates, or customer data in the practice file.

## Optional Vim Configuration

The included `.vimrc` is intentionally small and plugin-free. Test it without replacing your existing Vim configuration:

```bash
vim -u .vimrc practice/practice.txt
```

You do not need to study Vim configuration as part of this curriculum.

## Completion Criteria

You are finished with this Vim learning project when you can comfortably:

- Open and safely leave a file.
- Navigate to the value you need.
- Make a controlled edit.
- Search and replace with the correct scope.
- Use Visual/block mode when several visible lines need the same edit.
- Work with two files when needed.
- Review the diff.
- Validate the result.
- Recover from a small editing mistake without panic.

At that point, stop expanding the Vim curriculum. Learn additional commands only when repeated real-world work justifies them.
