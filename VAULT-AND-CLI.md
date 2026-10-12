# Obsidian and the flote CLI

Select **Settings → Obsidian → Choose Obsidian Vault…**. flote creates or uses `flote/` inside that vault. Previous collections stay where they are; selecting a vault does not migrate notes or images. Switching back uses **Notes Folder → Change…**. Open editors retain their original collection.

New notes get a readable filename from their first heading/non-empty content line, with unsafe filename characters removed and numbered collision suffixes. Existing UUID filenames remain supported. New readable files carry a terminal `<!-- flote-id: UUID -->` identity comment; flote hides only that identity line from its editor, including when Obsidian appends text after it. Unknown frontmatter, Markdown and image references are preserved. Opening a legacy note adds its stable identity so later external renames are recognized. Do not remove or duplicate the identity line.

Use **Rename Note…** in the editor’s context menu, or the CLI `rename` command. Renaming retains identity and relative image references and updates recognized incoming links in other managed flote notes. External vault documents are never rewritten. If you rename externally, use Obsidian’s own automatic link updates; flote follows the embedded identity but does not rewrite external documents.

External edits of a clean open note are loaded within roughly one second. If you also have unsaved changes, flote preserves your version as a separate conflict note and shows a message with **Open saved copy**. A deleted original is not recreated. Changes from flote processes are serialized through a collection lock, and commits use macOS file coordination with source comparisons. Unavailable storage produces a visible save error. The app’s existing temporary spill protection remains available when a folder grant cannot be used.

## Links, tags and navigation

Type a link directly or insert it using `/link`, then Command-click to follow it:

```markdown
[another flote note](Meeting%20notes.md)
[external document](../Projects/Plan%20A.md)
[[flote/Meeting notes|Meeting]]
[[Projects/Plan A]]
```

Supported: ordinary Markdown links, wiki links with optional `.md`, explicit vault paths, optional aliases and `#heading` suffixes. Links with spaces in Markdown destinations should be percent encoded. A heading suffix opens the target document; flote does not jump to the heading. Duplicate short wiki names that cannot be uniquely resolved need an explicit path. Missing, ambiguous and out-of-vault links show a useful error; flote does not create their targets. Links inside code and image embeds are not treated as backlinks. Reference-style links, block references and Obsidian plugin syntax are outside this lightweight subset.

**Backlinks.md** lists incoming links to managed notes from both flote and external vault files. **Topics.md** groups notes by existing inline `#tags`, nested `#work/project` tags and basic YAML `tags` lists. Tags are treated case-insensitively. The app refreshes these files after relevant vault changes, or you can run `flote indexes`. Use the Obsidian Settings buttons or **Show Backlinks** in the note context menu to open navigation files. No Obsidian plugin is required. See Obsidian’s [link documentation](https://obsidian.md/help/links) and [tag documentation](https://obsidian.md/help/tags).

Both indexes are ordinary Markdown; handwritten content outside `flote-generated` markers is preserved. The indexes do not modify external files or change tags. [AI tagging](AI-GENERATION.md) separately adds reviewed or explicitly auto-accepted tags to managed notes. The lightweight index scan skips hidden/package/symlink paths, reads Markdown up to 1 MB and caps the vault inventory at 10,000 files. Keep larger vaults in mind when evaluating completeness.

## Install and use the CLI

In **Settings → Terminal / CLI**, select **Install CLI…** and choose a writable `bin` folder in your PATH (for example `~/.local/bin`; create it in the picker if needed). The app creates a link to its bundled executable. The status, installation path and **Repair Installation** / **Uninstall CLI** controls are shown there. Existing unrelated executables are never overwritten. App updates at the same location keep the linked CLI current; use Repair after moving the app.

If the folder is not yet in PATH, use **Copy PATH Line**, add the line to `~/.zshrc`, and open a new terminal. flote does not edit your shell configuration automatically. Deinstallation removes the link, retaining notes and shell settings.

For the packaged app installed in Applications:

```sh
mkdir -p "$HOME/.local/bin"
ln -s /Applications/flote.app/Contents/Helpers/flote "$HOME/.local/bin/flote"
# Add ~/.local/bin to PATH if needed. Remove ~/.local/bin/flote to uninstall.
flote --version
```

From the source checkout with Xcode Command Line Tools installed:

```sh
scripts/install-cli.sh
# Add ~/.local/bin to PATH if it is not already there.
flote --help
flote --version
```

A custom absolute prefix is accepted: `scripts/install-cli.sh /your/prefix`. Uninstall with `scripts/uninstall-cli.sh` (or the same prefix). Uninstallation removes only the executable and retains notes.

The CLI uses the app’s exported current collection, located at `~/Library/Containers/chillig.zeronote/Data/Library/Application Support/flote/collection.json`. The historical container name is retained for upgrade compatibility. Select a notes folder in the updated app once to export this configuration. The CLI can create, list, read, search and rename notes while the app is stopped. Basic access works offline and does not require an embedding or generation model.

```sh
flote "einkauf finden"
flote "Milch" "Brot" "Äpfel"
flote help
flote create 'Remember to call tomorrow'
printf '# Meeting\nTwo lines, Unicode: Grüße 👋\n' | flote create
flote create 'Body text' --title 'Readable title'
flote list
flote search meeting
flote read NOTE_UUID
flote open NOTE_UUID
flote rename NOTE_UUID 'New readable filename'
flote indexes
```

A single quoted string creates a note with exactly that text. Multiple positional strings create **one note** containing Markdown bullet points; quote each item including its spaces. For example `flote "Milch" "Brot kaufen"` stores:

```markdown
- Milch
- Brot kaufen
```

Existing subcommands remain reserved: `flote search Einkauf` searches. Use `flote -- "search"` to create a note containing only a reserved word, or `flote create "search"`. `flote create one continuous note` retains its continuous-text behavior. Unknown words are note text, so a misspelled command also creates a note. `flote help` and `flote --help` show the syntax and examples without needing a configured collection.

Use `--root /absolute/notes-folder` or `--vault /absolute/vault` before the command to select a collection explicitly. `--vault` manages only its `flote/` subfolder. Explicit selection does not change the app’s Settings. `open` requires the app to use the same collection and invokes its validated `flote://open/UUID` handler. Install/launch the updated app once to register that handler. A mismatched app collection is rejected.

`flote --json list`, `flote --json search QUERY`, `flote --json create TEXT`, `flote --json read UUID`, `flote --json rename UUID TITLE` and `flote --json config` provide structured output. Plain `create`/`rename` print the path; `read` prints exact body bytes; `list`/`search` print UUID, filename and title separated by tabs. Results go to stdout, diagnostics to stderr. Exit codes: 0 success, 1 storage/operation failure, 2 usage/configuration errors. Notes are UTF-8 and limited to 1 MB. Creating empty notes is rejected.

## Verification

Run `python3 scripts/test-cli.py` for real subprocess acceptance, including concurrent creation and symlink confinement. `scripts/test.sh unit` includes storage/link/conflict tests and existing app regressions. Native `ImageNoteUITests` cover picture import, size controls, crop cancel/apply, persistence, reopening, original restoration and undo. The image original remains immutable; dimensions are display metadata and cropping writes a derivative.
