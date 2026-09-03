# C. Modes And Navigation

Efficient movement matters because DevOps files often contain long paths, URLs, YAML blocks, Terraform resources, logs, and service configuration.

## Essential Mode Keys

| Key | Action |
| --- | --- |
| `<Esc>` | Return to Normal mode. |
| `i` / `a` | Insert before / after the cursor. |
| `I` / `A` | Insert at first non-blank / line end. |
| `o` / `O` | Open a new line below / above. |
| `v` | Character-wise Visual mode. |
| `V` | Line-wise Visual mode. |
| `<C-v>` | Block-wise Visual mode. |
| `:` | Enter an Ex command. |
| `/` / `?` | Search forward / backward. |

## Move By Character, Word, And Line

| Command | Movement |
| --- | --- |
| `h` / `l` | One character left / right. |
| `j` / `k` | One line down / up. |
| `w` / `b` / `e` | Next word / previous word / end of word. |
| `W` / `B` | Next / previous whitespace-separated WORD; useful for URLs and paths. |
| `0` | First column. |
| `^` | First non-blank character. |
| `$` | End of line. |
| `fX` | Move to the next `X` on the current line. |
| `tX` | Move just before the next `X`. |
| `;` / `,` | Repeat the last `f` or `t` forward / backward. |

Counts work with many commands: `5j` moves five lines and `3w` moves three words.

## Move Through A File

| Command | Movement |
| --- | --- |
| `gg` | First line. |
| `G` | Last line. |
| `42G` | Line 42. |
| `%` | Matching bracket, brace, or parenthesis. |
| `<C-d>` / `<C-u>` | Half-page down / up. |
| `zz` | Center the current line. |

`%` is especially useful when reviewing JSON, Terraform, shell conditionals, and nested configuration.

## Search As Navigation

```vim
/server_name
n
N
```

`n` moves to the next match and `N` moves in the opposite direction.

## Return After A Jump

| Command | Result |
| --- | --- |
| `<C-o>` | Go to an older jump location. |
| `<C-i>` | Go to a newer jump location. |

This is useful after following a file with `gf` or jumping around a large file.

## Practical Sequence

```vim
/replicas
n
zz
```

Search for a value, move through matches, and center the current match before editing.
