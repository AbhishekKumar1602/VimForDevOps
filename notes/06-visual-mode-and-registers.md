# F. Visual Mode And Registers

Visual mode is useful when a change must affect an exact visible range. For normal DevOps work, you only need basic Visual selection and the default copy/paste behavior.

## Select Text

| Command | Selection |
| --- | --- |
| `v` | Character-wise selection. |
| `V` | Line-wise selection. |
| `<C-v>` | Rectangular block selection. |
| `gv` | Reselect the previous Visual area. |

After starting a selection, use normal movements such as `j`, `k`, `w`, `$`, `G`, or a search.

## Act On A Selection

| Command | Action |
| --- | --- |
| `y` | Copy the selection. |
| `d` | Delete the selection. |
| `c` | Change the selection. |
| `>` / `<` | Indent / unindent the selection. |
| `=` | Re-indent the selection. |
| `:` | Start an Ex command scoped to the selected range. |

## Rectangular Block Edit

A common DevOps use case is adding the same prefix to several lines:

```text
<C-v>    start block selection
j / k    extend over the required lines
I        insert at the left edge
server=  type the prefix
<Esc>    apply the insertion to every selected line
```

This is useful for flat lists and repeated key/value-style edits. Inspect the complete block before saving.

## What Is A Register?

A register is Vim's internal storage for copied or deleted text. The normal commands you already know use registers automatically:

```text
yy   copy a line
p    paste it
```

For this learning scope, **named registers, numbered deletion registers, expression registers, and macro registers are intentionally excluded**. They are not necessary for day-to-day DevOps work.
