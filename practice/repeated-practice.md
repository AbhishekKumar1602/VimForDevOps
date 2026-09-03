# Repeated Vim Practice

Use only `practice/practice.txt`. It contains fictional, non-deployable data created for these drills.

The objective is **muscle memory for normal DevOps work**, not mastery of Vim.

## Before Every Session

From the repository root:

```bash
git restore practice/practice.txt
vim practice/practice.txt
```

If the repository has not been committed yet, make a copy of the practice file before experimenting. Never substitute a production configuration file.

## Round 1: Survival

Repeat until the sequence feels natural:

1. Press `<Esc>`.
2. Run `:file` to confirm the current file.
3. Make a small edit with `i` or `A`.
4. Press `<Esc>`.
5. Undo with `u` and redo with `<C-r>`.
6. Save with `:update`.
7. Quit with `:q`.
8. Reopen the practice file.

Also practise `:q!` once on a deliberate throwaway edit so you understand that it discards unsaved changes.

## Round 2: Navigation

1. Press `gg`, then `G`.
2. Search `/BEGIN_NAVIGATION`.
3. Move through the block with `j` and `k`.
4. Move across values with `w`, `b`, `W`, and `B`.
5. Practise `0`, `^`, and `$` on a long line.
6. Use `f=` to jump to `=` on a key/value line.
7. Use `<C-d>` and `<C-u>` in the file.
8. Press `zz` on a target line.

## Round 3: Editing And Repeat

Reset the file first.

1. Search `/FEATURE_FLAG=false`.
2. Place the cursor on `false` and run `ciwtrue`, then `<Esc>`.
3. Search `/OLD_REGION=us-east-1`.
4. Change the first `us-east-1` with `ciWap-south-1`, then `<Esc>`.
5. Move to the next identical line and press `.`.
6. Repeat for the third line.
7. Copy a line with `yy` and paste it with `p`.
8. Undo any practice copy you do not want to keep.

## Round 4: Search And Safe Replacement

Reset the file first.

1. Search `/staging` and use `n` / `N` to inspect matches.
2. Count the whole word `staging` with `:%s/\<staging\>//gn`.
3. Run `:%s/\<staging\>/production/gc`.
4. Confirm only the replacements you actually want.
5. Run `:!git diff -- practice/practice.txt` and inspect the result.
6. Undo if the scope was wrong.

For log practice:

1. Search `/ERROR`.
2. Count with `:%s/ERROR//gn`.
3. Preview matching lines with `:g/ERROR/p`.

## Round 5: Visual And Block Editing

Reset the file first.

Line selection:

1. Search `/BEGIN_BLOCK_EDIT`, then move to the first node line.
2. Press `V` and select several node lines.
3. Press `y` to copy them.
4. Move elsewhere and paste with `p`.
5. Undo the paste.

Block prefix:

1. Return to the node list.
2. Press `<C-v>` and select the first column across all node lines.
3. Press `I`, type `server=`, then press `<Esc>`.
4. Inspect every changed line.
5. Undo the block edit.

## Round 6: Sort And Configuration Hygiene

Reset the file first.

1. Search `/BEGIN_FLAT_ALLOWLIST`, then move to the first address.
2. Press `V` and select only the IP-address lines.
3. Run `:sort u`.
4. Confirm that only the selected flat list changed.
5. Undo.
6. Run `:set list` and inspect whitespace markers.
7. Run `:%s/\s\+$//e`.
8. Run `:set fileformat?`.
9. Run `:set nolist`.

## Round 7: Professional DevOps Workflow

After any practice edit:

1. Run `:file` and confirm the file.
2. Run `:ls` and look for modified buffers marked with `+`.
3. Save intentionally with `:update`.
4. Run `:!git diff --check`.
5. Run `:!git diff --stat`.
6. Run `:!git diff`.
7. Run the formatter or validator appropriate to the real file type.
8. Exit Vim.
9. Restore the training file with `git restore practice/practice.txt`.

# DevOps Vim Readiness Check

Without opening the notes, be able to demonstrate these tasks:

1. Open a file and safely save or discard a change.
2. Move by word, WORD, line, file boundary, and matching bracket.
3. Change a word and a quoted/braced value.
4. Copy and paste lines.
5. Undo, redo, and repeat a change with `.`.
6. Search, count matches, and perform a confirmed replacement.
7. Select lines and perform a Visual block prefix edit.
8. Open another buffer or a vertical split and move between windows.
9. Compare files with `vimdiff` and navigate changed blocks.
10. Review `git diff` and run the correct validator before deployment.

If you can do these comfortably, your Vim knowledge is sufficient for normal day-to-day DevOps work. Learn additional Vim features only when a real task repeatedly creates the need.
