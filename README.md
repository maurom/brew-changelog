brew-changelog
==============

A lightweight Homebrew external command that quickly opens the changelog or release notes for formulas and casks in your default browser.

When placed anywhere in your `$PATH`, Homebrew recognizes it as a subcommand, allowing you to run `brew changelog <package>`.

Features
--------

- **Simple and portable**: A single POSIX-compliant shell script with minimal dependencies that runs on macOS and Linux.
- **Smart Changelog discovery**: Derives release note URLs automatically from formula/cask homepages hosted on major platforms. It uses a curated internal lookup table for other projects and falls back to `brew home <package>` if no changelog URL could be resolved.
- **Print / Scripting Support**: Supports `-u` / `--url` to print the resolved URL without launching a browser.

Install
-------

```sh
chmod +x brew-changelog

# On Apple Silicon / default Homebrew:
mv brew-changelog "$(brew --prefix)/bin/brew-changelog"

# Or install directly to /usr/local/bin:
sudo cp brew-changelog /usr/local/bin/
```

Usage
-----

```sh
brew changelog [options] <formula|cask> ...
brew changelog firefox
```

Or run the script directly:

```sh
./brew-changelog [options] <formula|cask> ...
./brew-changelog --url jq ripgrep
```

Adding Custom URLs
------------------

Add custom changelog entries by editing the `__DATA__` section at the end of the script.

If you have a large batch, feel free to prepare a pull request.

Example entry:

```csv
# formula or cask,changelog-url,last-updated
sqlite,https://www.sqlite.org/changes.html,2026-09-12
formula,https://example.com/changelog,YYYY-MM-DD
```

Alternatives
------------

- [pavel-voronin/homebrew-changelog](https://github.com/pavel-voronin/homebrew-changelog)

License
-------

This project is licensed under the BSD 2-Clause ("Simplified") License. See [LICENSE](LICENSE) for details.
