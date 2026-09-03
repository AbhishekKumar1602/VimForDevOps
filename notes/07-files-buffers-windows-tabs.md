# G. Files, Buffers, Windows, And Tabs

DevOps work sometimes requires comparing or editing two related configuration files. Learn only the small set of file, buffer, and split commands needed for that workflow.

## Open Another File

| Command | Result |
| --- | --- |
| `:edit FILE` | Edit a file in the current window. |
| `gf` | Open the filename under the cursor when Vim can resolve it. |
| `:pwd` | Show Vim's working directory. |

Use `<C-o>` to return after a jump when appropriate.

## Buffers

| Command | Result |
| --- | --- |
| `:ls` | List open buffers and their status. |
| `:bnext` / `:bprev` | Next / previous buffer. |
| `<C-^>` | Switch between the current and alternate buffer. |
| `:wall` | Save changed buffers. |

In `:ls`, a `+` indicates a modified buffer. Check this before quitting a multi-file session.

## Split Windows

| Command | Result |
| --- | --- |
| `:split FILE` | Open a horizontal split. |
| `:vsplit FILE` | Open a vertical split. |
| `<C-w>h/j/k/l` | Move to the window left/below/above/right. |
| `:close` | Close the current window. |
| `:only` | Close the other windows in the current tab page. |

Splits are useful when comparing related YAML, Terraform, Nginx, inventory, or environment files side by side.

## Minimal Tab Usage

| Command | Result |
| --- | --- |
| `:tabedit FILE` | Open a file in a new tab page. |
| `gt` / `gT` | Next / previous tab page. |

Tabs are not required for every file. Buffers are the files; windows and tab pages are only ways to display them.

## Practical Two-File Review

```vim
:vsplit inventory/staging.ini
<C-w>l
/database
<C-w>h
/database
```

This opens a related file and searches the same concept in both windows.

Argument-list automation, session files, advanced resizing, and other workspace-management features are intentionally outside this DevOps-focused scope.
