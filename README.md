<div align="center">

# comertial-mods

**Mods that make Claude Code work the way you do.**

A [Claude Code](https://docs.claude.com/en/docs/claude-code) plugin marketplace. Add it once, install any mod with one command.

</div>

```
/plugin install <mod> --marketplace comertial/comertial-mods
```

---

## Mods

### 🔍 [pending-changes](https://github.com/comertial/claude-pending-changes)

**Review every file Claude touches, like a pull request, without leaving the terminal.** A docked pane lists Claude's changes as a tree with +/- counts. Accept or reject per file, per folder or all at once, revert single blocks in a VS Code diff, and Claude is told what you decided.

<img src="https://raw.githubusercontent.com/comertial/claude-pending-changes/v1.0.1/assets/demo.gif" alt="pending-changes demo: Claude edits files, the review pane lists them, changes are reverted in VS Code and rejected with one click" width="720">

```
/plugin install pending-changes --marketplace comertial/comertial-mods
```

---

## Install and update

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

## Adding a mod

Each mod lives in its own repository; this one only holds the catalog in `.claude-plugin/marketplace.json`.

1. The mod gets its own repository, `comertial/<mod>`, with `.claude-plugin/plugin.json` at its root and no `marketplace.json`.
2. It ships a short demo at `assets/demo.gif` in its own repository (under ~2 MB, ~900px wide).
3. Add an entry to `.claude-plugin/marketplace.json`, pinned to a release tag:
   ```json
   { "name": "<mod>", "description": "<one line>", "source": { "source": "github", "repo": "comertial/<mod>", "ref": "vX.Y.Z" } }
   ```
4. Add a card under [Mods](#mods): an emoji and linked name, a bold one-line hook plus a sentence, the GIF from `https://raw.githubusercontent.com/comertial/<mod>/vX.Y.Z/assets/demo.gif`, and the install command.
5. Run `claude plugin validate .`, then commit.

**Releasing a new version of a mod:** bump the `ref` in `marketplace.json` and the tag in the mod's GIF URL together, so the demo always matches what users install. Without a `ref`, users get the mod's default branch.

## License

[GPL-3.0](LICENSE). Each mod carries its own license. This is an independent project, not affiliated with or endorsed by Anthropic. Claude and Claude Code are products of Anthropic.
