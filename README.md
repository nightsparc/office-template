# office-template

A template for repositories office-related repositories with preset issue-labes and preconfigured `gitignore` and `gitattribute` files.

## Usage / Configuration

### Word files (`.docx`/`.odt`)

The `.gitattributes` file is configured to redirect calls to `git diff` for `.docx` and `.odt` files to [`pandoc`](https://pandoc.org) prior diffing them, using pandoc's output as (textual) input to `git diff`.

Therefore, `pandoc` should be [installed](https://pandoc.org/installing.html) and callable by `git`.

Furthermore, the (repository-local or global) git config must be modified accordingly. To do so, add the following lines to your `$GIT_DIR/config` or `$HOME/.gitconfig`.


```gitconfig
[diff "pandoc"]
    textconv=pandoc --to=rst
    prompt=false
[alias]
    # Shortcut for word-diff
    wdiff = diff --word-diff=color --unified=1
```

After configuration, `.docx` and `.odt` files should be diffable by git via: `git diff YOUR.docx` and `git wdiff YOUR.docx` respectively:

- `git diff`: performs a diff, highlighting the whole line in which changes were detected with deletions in red and insertions in  green;
- `git wdiff`: performs a word-based diff, highlighting only the changed words in red or green.

#### Sources
- <http://blog.martinfenner.org/2014/08/25/using-microsoft-word-with-git/>
- <https://github.com/vigente/gerardus/wiki/Integrate-git-diffs-with-word-docx-files>

### Presentations (`.pptx`/`.odp`)

Possible: yes

TBD

### Spreadsheets (`.xlsx`/`.ods`)

Possible: yes

TBD

### PDF/A

Possible: yes

TBD
