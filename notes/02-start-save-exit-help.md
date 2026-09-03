# B. Start, Save, Exit, And Help

These commands are the minimum survival skills to learn before editing files on a server.

## Start Vim From The Shell

| Command | Practical Use |
| --- | --- |
| `vim FILE` | Open one file for editing. |
| `view FILE` | Open a file read-only when you only need to inspect it. |
| `vim +42 FILE` | Open directly at line 42. |
| `vim +/ERROR FILE` | Open at the first match for `ERROR`. |
| `vimdiff OLD NEW` | Open two files for comparison. |

Use read-only mode when investigation does not require a change.

## Save And Exit

Press `<Esc>`, type the command, and press `<Enter>`.

| Command | Result |
| --- | --- |
| `:w` | Save the current buffer. |
| `:update` | Save only if the buffer changed. |
| `:q` | Quit the current window when there are no unsaved changes. |
| `:q!` | Quit and intentionally discard unsaved changes. |
| `:wq` | Save and quit. |
| `:x` | Save if changed, then quit. |
| `:qa` | Quit all windows when nothing is unsaved. |
| `:wqa` | Save changed buffers and quit all windows. |
| `:edit!` | Reload from disk and discard unsaved changes in the current buffer. |

Commands containing `!` deliberately override a safety check. Use them only when the impact is intentional.

## Confirm What You Are Editing

| Command | Result |
| --- | --- |
| `:file` | Show the current filename and cursor information. |
| `:pwd` | Show Vim's current working directory. |

Before a broad or privileged change, confirm the file path.

## Built-In Help

You do not need to memorize everything. Vim's built-in help is available when needed.

```vim
:help
:help :write
:help dd
```

## Recover From Common Situations

| Situation | Action |
| --- | --- |
| You do not know which mode is active. | Press `<Esc>` once or twice. |
| You changed something accidentally. | Press `u`; use `<C-r>` to redo if needed. |
| Search highlighting is distracting. | Run `:nohlsearch`. |
| You want to discard every unsaved change in the buffer. | Run `:edit!` only after confirming that this is intentional. |
| Vim reports a swap file. | Read the warning. Do not blindly delete the swap file; confirm that no other editor session is active and whether recovery is needed. |

## Privileged Files

When you are authorized to edit a root-owned system file, prefer a controlled privileged-edit workflow such as:

```bash
sudoedit /etc/example.conf
```

or:

```bash
sudo -e /etc/example.conf
```

Where a configuration-management or deployment workflow exists, prefer editing the reviewed source and deploying through that normal process rather than making ad-hoc production changes.
