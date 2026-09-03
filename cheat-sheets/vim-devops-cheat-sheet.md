# Vim for DevOps: Quick Reference

This sheet contains only the Vim commands worth remembering for normal DevOps work. Press `<Esc>` before a Normal-mode or `:` command when you are unsure which mode is active.

## Open, Save, and Leave

| Command | Action |
| --- | --- |
| `vim FILE` | Open a file for editing. |
| `view FILE` | Open a file read-only. |
| `vim +42 FILE` | Open at line 42. |
| `vim +/ERROR FILE` | Open at the first `ERROR`. |
| `:w` | Save. |
| `:update` | Save only if changed. |
| `:q` | Quit the current window. |
| `:q!` | Quit and discard unsaved changes. |
| `:wq` / `:x` | Save and quit. |
| `:qa` | Quit all windows when nothing is unsaved. |
| `:wqa` | Save changed buffers and quit all. |
| `:edit!` | Reload from disk and discard unsaved buffer changes. |
| `:file` | Confirm the current file. |
| `:pwd` | Show Vim's working directory. |

## Modes and Movement

| Command | Action |
| --- | --- |
| `<Esc>` | Return to Normal mode. |
| `i a I A` | Insert before/after cursor or at line start/end. |
| `o O` | Open a line below/above. |
| `v V <C-v>` | Character, line, or block Visual mode. |
| `h j k l` | Left, down, up, right. |
| `w b e` | Next word, previous word, end of word. |
| `W B` | Move by whitespace-separated WORD. |
| `0 ^ $` | Column zero, first non-blank, line end. |
| `fX` / `tX` | Move to `X` / just before `X` on the line. |
| `;` / `,` | Repeat the last line-find forward/backward. |
| `gg` / `G` | First / last line. |
| `42G` | Go to line 42. |
| `%` | Jump to matching bracket/brace/parenthesis. |
| `<C-d>` / `<C-u>` | Half-page down / up. |
| `<C-o>` / `<C-i>` | Older / newer jump. |
| `zz` | Center the current line. |

## Edit

| Command | Action |
| --- | --- |
| `x` | Delete one character. |
| `dd` / `D` | Delete line / to line end. |
| `cc` / `C` | Change line / to line end. |
| `dw` | Delete a word forward. |
| `diw` / `ciw` | Delete / change the current word. |
| `ci"` / `ci'` | Change inside quotes. |
| `ci{` / `ci(` | Change inside braces / parentheses. |
| `yy` | Copy the current line. |
| `p` / `P` | Paste after / before. |
| `>>` / `<<` | Indent / unindent line. |
| `==` / `=ip` | Re-indent line / current paragraph-like block. |
| `u` / `<C-r>` | Undo / redo. |
| `.` | Repeat the last change. |

## Search and Replace

| Command | Action |
| --- | --- |
| `/PATTERN` / `?PATTERN` | Search forward / backward. |
| `n` / `N` | Next / opposite-direction match. |
| `*` / `#` | Search the word under the cursor forward / backward. |
| `:nohlsearch` | Clear search highlighting. |
| `:s/old/new/` | Replace first match on current line. |
| `:%s/old/new/gc` | Confirm replacements through the file. |
| `:'<,'>s/old/new/gc` | Confirm replacements only in Visual selection. |
| `:%s/old/new/gn` | Count matches without changing text. |
| `:%s/\s\+$//e` | Remove trailing whitespace. |
| `:g/PATTERN/p` | Preview matching lines. |
| `:g/PATTERN/d` | Delete matching lines. |
| `:v/PATTERN/d` | Delete non-matching lines. |
| `:'<,'>sort` | Sort selected lines. |
| `:'<,'>sort u` | Sort and deduplicate selected flat lines. |

## Visual Block Editing

```text
<C-v>      start block selection
j / k      extend over lines
I          insert at the left side
TEXT       type the prefix
<Esc>      apply to all selected lines
```

Use `gv` to reselect the previous Visual area.

## Buffers and Splits

| Command | Action |
| --- | --- |
| `:edit FILE` | Edit another file. |
| `gf` | Open filename under cursor. |
| `:ls` | List buffers. |
| `:bnext` / `:bprev` | Next / previous buffer. |
| `<C-^>` | Switch to alternate buffer. |
| `:split FILE` / `:vsplit FILE` | Horizontal / vertical split. |
| `<C-w>h/j/k/l` | Move among splits. |
| `:close` | Close current window. |
| `:only` | Close other windows in the current tab. |
| `:tabedit FILE` | Open a file in a new tab page. |
| `gt` / `gT` | Next / previous tab page. |

## DevOps Configuration and Logs

| Command | Action |
| --- | --- |
| `:set list` / `:set nolist` | Show / hide hidden whitespace. |
| `:set nowrap` / `:set wrap` | Disable / enable display wrapping. |
| `:set number` | Show line numbers. |
| `:set fileformat?` | Check line-ending format. |
| `:setlocal fileformat=unix` | Write LF line endings. |
| `:setlocal expandtab ts=2 sw=2 sts=2` | Common two-space indentation settings. |
| `:%!jq .` | Format/validate JSON through `jq`. |
| `:%!yq .` | Format YAML through a compatible `yq`. |
| `:%!terraform fmt -` | Format HCL through Terraform. |

## Diff and Validation

| Command | Action |
| --- | --- |
| `vimdiff OLD NEW` | Compare two files. |
| `]c` / `[c` | Next / previous changed block. |
| `do` / `dp` | Obtain / put the current diff block. |
| `:diffupdate` | Recalculate the diff. |
| `:!COMMAND` | Run a shell command and return to Vim. |
| `:!git diff -- %` | Show Git diff for the current file. |

Common validators include `shellcheck`, `yamllint`, `ansible-lint`, `terraform validate`, `nginx -t`, and the validation command appropriate to the technology you are editing.

## Safe Final Check

```vim
:update
:!git diff --check
:!git diff --stat
:!git diff
```

Run the correct formatter and validator before committing or deploying.
