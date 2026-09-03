# D. Editing And Undo

The goal is to make common configuration edits quickly without learning a large command vocabulary.

## Insert Text

| Command | Action |
| --- | --- |
| `i` / `a` | Insert before / after the cursor. |
| `I` / `A` | Insert at first non-blank / line end. |
| `o` / `O` | Open a line below / above. |

## Delete And Change

| Command | Action |
| --- | --- |
| `x` | Delete the character under the cursor. |
| `dd` | Delete the current line. |
| `3dd` | Delete three lines. |
| `D` | Delete from cursor to line end. |
| `dw` | Delete forward by a word. |
| `diw` | Delete the current word. |
| `cc` | Change the current line. |
| `C` | Change from cursor to line end. |
| `ciw` | Change the current word. |
| `ci"` / `ci'` | Change inside matching quotes. |
| `ci{` / `ci(` | Change inside braces / parentheses. |

Text objects such as `iw`, `i"`, and `i{` are very useful when changing configuration values because they reduce cursor movement.

## Copy And Paste

| Command | Action |
| --- | --- |
| `yy` | Copy the current line. |
| `3yy` | Copy three lines. |
| `p` / `P` | Paste after / before the cursor or line. |

For this DevOps-focused course, normal copy/paste is sufficient; named-register workflows are intentionally not required.

## Indentation

| Command | Action |
| --- | --- |
| `>>` / `<<` | Indent / unindent the current line. |
| `==` | Re-indent the current line. |
| `=ip` | Re-indent the current paragraph-like block. |

For YAML, indentation changes meaning. Always inspect the result and validate the file after structural indentation changes.

## Repeat, Undo, And Redo

| Command | Action |
| --- | --- |
| `.` | Repeat the last change. |
| `u` | Undo the last change. |
| `<C-r>` | Redo an undone change. |
| `:edit!` | Discard all unsaved changes and reload from disk. |

The `.` command is one of the most useful Vim productivity features. Make one correct change, move to the next target, and repeat it.

## Practical Example

Given:

```text
image: api:v1
replicas: 2
```

You can search for `api:v1`, place the cursor on the value, use `ciW`, type the new value, press `<Esc>`, and save.

Before deployment, review the resulting Git diff instead of trusting the edit from memory.
