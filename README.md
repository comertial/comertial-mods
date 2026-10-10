# comertial-mods

A [Claude Code](https://docs.claude.com/en/docs/claude-code) plugin marketplace, `comertial-mods`, listing mods by comertial. Each mod lives in its own repository; this one only holds the catalog in `.claude-plugin/marketplace.json`.

## Install a mod

In a Claude Code session:

```
/plugin install <mod> --marketplace comertial/comertial-mods
```

Or from a shell:

```bash
claude plugin marketplace add comertial/comertial-mods
claude plugin install <mod>@comertial-mods --scope user
```

Update with `claude plugin marketplace update comertial-mods`, then `claude plugin update <mod>@comertial-mods`.

## Mods

| Mod | What it does |
| --- | --- |
| [pending-changes](https://github.com/comertial/claude-pending-changes) | Copilot-style review of the files Claude changes: a tree of changed files with +/- counts, accept/reject per file, folder or all, and a VS Code diff to revert single blocks. |

## Adding a mod

1. The mod gets its own repository, `comertial/<mod>`, with `.claude-plugin/plugin.json` at its root and no `marketplace.json`.
2. Add an entry to `.claude-plugin/marketplace.json`:
   ```json
   { "name": "<mod>", "description": "<one line>", "source": { "source": "github", "repo": "comertial/<mod>" } }
   ```
3. Add a row to the table above.
4. Run `claude plugin validate .`, then commit.

To pin a mod to a release, add `"ref": "vX.Y.Z"` to its `source`. Without it, users get the default branch.

## License

[GPL-3.0](LICENSE). Each mod carries its own license. This is an independent project, not affiliated with or endorsed by Anthropic.
