# E. Search, Replace, Sort, And Filter

Search and controlled replacement are among the most valuable Vim skills for DevOps work. Start with a narrow scope and expand only after checking matches.

## Search

| Command | Result |
| --- | --- |
| `/ERROR` | Search forward for `ERROR`. |
| `?ERROR` | Search backward. |
| `n` / `N` | Next match / opposite direction. |
| `*` / `#` | Search the word under the cursor forward / backward. |
| `:nohlsearch` | Clear search highlighting. |

Useful simple patterns:

| Pattern | Meaning |
| --- | --- |
| `^server` | `server` at the beginning of a line. |
| `enabled$` | `enabled` at the end of a line. |
| `\<prod\>` | Whole word `prod`. |
| `\s\+` | One or more whitespace characters. |
| `\d\+` | One or more digits. |

You do not need to become a Vim regular-expression expert. Learn additional patterns only when a real task requires them.

## Replace

General form:

```text
:[range]s/pattern/replacement/[flags]
```

| Command | Result |
| --- | --- |
| `:s/old/new/` | Replace first match on current line. |
| `:%s/old/new/g` | Replace all matches in the file. |
| `:%s/old/new/gc` | Confirm each replacement in the file. |
| `:10,30s/old/new/gc` | Confirm replacements only on lines 10-30. |
| `:'<,'>s/old/new/gc` | Confirm replacements only in Visual selection. |
| `:%s/old/new/gn` | Count matches without changing text. |
| `:%s/\s\+$//e` | Remove trailing whitespace. |

When the impact is uncertain, prefer the `c` confirmation flag.

Confirmation keys:

| Key | Action |
| --- | --- |
| `y` | Replace this match. |
| `n` | Skip this match. |
| `a` | Replace this and all remaining matches. |
| `q` | Stop replacement. |

## Preview, Delete, Or Keep Matching Lines

| Command | Result |
| --- | --- |
| `:g/ERROR/p` | Preview lines containing `ERROR`. |
| `:g/ERROR/d` | Delete lines containing `ERROR`. |
| `:v/ERROR/d` | Delete lines that do not contain `ERROR`. |

Commands that delete many lines should normally be used on a copy, in a Git-controlled file, or followed immediately by inspection and undo if the scope is wrong.

## Sort A Flat List

Select only the flat list with Visual line mode, then run:

```vim
:'<,'>sort
```

or:

```vim
:'<,'>sort u
```

Do not sort an entire YAML, JSON, Terraform, or ordered configuration file unless you know its structure permits it.

## Safe Replacement Workflow

```vim
/staging
n
:%s/\<staging\>/production/gn
:%s/\<staging\>/production/gc
:w
```

Then review the Git diff and run the correct validator.
