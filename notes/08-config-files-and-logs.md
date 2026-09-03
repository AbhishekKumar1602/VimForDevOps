# H. Configuration Files And Logs

This module combines the core Vim commands into workflows that are directly useful for DevOps configuration and troubleshooting.

## Reveal Whitespace And Line Endings

| Command | Result |
| --- | --- |
| `:set list` / `:set nolist` | Show / hide tabs, trailing spaces, and line endings. |
| `:set fileformat?` | Show the current line-ending format. |
| `:setlocal fileformat=unix` | Write LF line endings. |
| `:%s/\s\+$//e` | Remove trailing whitespace. |

Use these commands when a file behaves differently across Linux/Windows environments or CI reports whitespace problems.

## Indentation

Common two-space configuration for YAML, JSON, and many Terraform projects:

```vim
:setlocal expandtab tabstop=2 shiftwidth=2 softtabstop=2
```

Common four-space configuration when a project requires it:

```vim
:setlocal expandtab tabstop=4 shiftwidth=4 softtabstop=4
```

Useful commands:

```text
==     re-indent current line
=ip    re-indent current block
>>     indent current line
<<     unindent current line
```

For YAML, indentation changes meaning. Always validate after structural edits.

## Read Long Logs

| Command | Result |
| --- | --- |
| `:set nowrap` | Keep a long log entry on one display line. |
| `:set wrap` | Wrap long lines for reading. |
| `:set number` | Show source line numbers. |
| `/ERROR` | Search for errors. |
| `n` / `N` | Move through error matches. |
| `:%s/ERROR//gn` | Count `ERROR` occurrences. |
| `:g/ERROR/p` | Preview error lines. |

Vim is not a continuous log follower. For live logs, use tools such as `tail -F`, `journalctl -f`, `kubectl logs -f`, or the platform-specific log command in another terminal.

## Format Through External Tools

When the required formatter is installed, Vim can pass the current buffer through it:

```vim
:%!jq .
:%!yq .
:%!terraform fmt -
```

These commands replace the buffer with command output. Work under version control or keep a recoverable copy, and press `u` immediately if a formatter returns an error message into the buffer.

## Practical Configuration Cleanup

```vim
:set list
:%s/\s\+$//e
:setlocal fileformat=unix
:w
```

Then review the Git diff and run the correct technology-specific formatter or validator.
