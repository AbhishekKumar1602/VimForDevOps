# A. Introduction To Vim And Its Modes

## What Is Vim?

Vim stands for **Vi Improved**. It is a terminal-friendly text editor commonly available on Linux and Unix-like systems. For DevOps work, Vim is useful when editing configuration files, shell scripts, infrastructure code, service files, or small operational files directly in a terminal or SSH session.

The goal of this repository is **not Vim mastery**. It is to become comfortable enough to inspect and safely edit files during normal DevOps work.

## Vim Is Modal

The same key can perform different actions depending on the active mode. When you are unsure which mode is active, press `<Esc>` to return to Normal mode.

| Mode | Purpose | Enter / Return |
| --- | --- | --- |
| **Normal Mode** | Navigation and editing commands. | Vim starts here; press `<Esc>` to return. |
| **Insert Mode** | Type or insert text. | `i`, `a`, `I`, `A`, `o`, or `O`; press `<Esc>` to leave. |
| **Visual Mode** | Select text before acting on it. | `v`, `V`, or `<C-v>`; press `<Esc>` to cancel. |
| **Command-Line Mode** | Save, quit, search, replace, and run `:` commands. | `:`, `/`, or `?`; press `<Enter>` to execute. |

Replace mode exists, but it is not required for this DevOps-focused learning path.

## File, Buffer, Window, And Tab Page

| Term | Meaning |
| --- | --- |
| **File** | Persistent text stored on disk. |
| **Buffer** | The file content currently loaded in Vim memory. Unsaved edits live here. |
| **Window** | A visible area displaying a buffer. Splits create more windows. |
| **Tab Page** | A workspace containing one or more windows. |

A file is loaded into a **buffer**, and a **window** displays that buffer.

## Core Editing Grammar

Vim becomes much easier when you understand this pattern:

```text
[count] operator motion-or-text-object
```

Common operators:

| Operator | Meaning |
| --- | --- |
| `d` | Delete. |
| `c` | Change, then enter Insert mode. |
| `y` | Yank, Vim's word for copy. |

Common motions and text objects:

| Item | Meaning |
| --- | --- |
| `w` | Move to the next word. |
| `$` | Move to line end. |
| `iw` | Inner word. |
| `i"` | Inside double quotes. |
| `i{` | Inside braces. |

Examples:

```text
dw      delete forward by a word
ciw     change the current word
ci"     change text inside quotes
yy      copy the current line
```

You do not need to memorize every possible Vim combination. Learn the small command set in these notes and build muscle memory through practice.
