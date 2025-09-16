# proneliner

A small, easy-to-use script that outputs GitHub PR information in a single line, including reviewers, additions/deletions, and the PR URL. Perfect for quick reference in terminal or sharing with your team.

Example: @reviewer1 @reviewer2 @author Add new login feature (+120/-20) https://github.com/yourcompany/repo/pull/42

## License

This project is licensed under the [MIT License](LICENSE).

---

## Installation

1. **Clone the repository** (or download the script):

```
git clone https://github.com/yourcompany/proneliner.git
cd proneliner
```
Make the script executable:

```
chmod +x proneliner
```
Add the script to your PATH (optional, for easy usage anywhere):

```
export PATH="$PATH:$(pwd)"
```
Ensure required dependencies are installed:

GitHub CLI (gh)

jq

```
# macOS
brew install gh jq

# Ubuntu/Linux
sudo apt install gh jq
```

---

## Usage

```
proneliner [options]
```
## Options

```
Option	      Description
-r	          Use reviewers from the GitHub PR (ignores saved defaults)
-ar <names>	  Add one or more reviewers to the default reviewer file
-rr <names>	  Remove one or more reviewers from the default reviewer file
-lr	          List saved reviewers
-h	          Show help message
```
## Examples

```
# Default usage (use saved reviewers, fallback to PR reviewers if none saved)
proneliner

# Force using PR reviewers only
proneliner -r

# Add reviewers to default file
proneliner -ar user1 user2

# Remove a reviewer
proneliner -rr user1

# List saved reviewers
proneliner -lr
```

## Example Output
If you run the script on a branch with a PR, it will output a single line like this:

```
@reviewer1 @reviewer2 @author Add new login feature (+120/-20) https://github.com/yourcompany/repo/pull/42
```
- @reviewer1 @reviewer2 — the reviewers (from PR or saved defaults)
- @author — the PR author
- Add new login feature — the PR title
- (+120/-20) — additions and deletions
- https://github.com/yourcompany/repo/pull/42 — PR URL

## Reviewer Storage
Default reviewers are stored in:

```
$HOME/.proneliner_reviewers
```
You can version-control this file or share it with your team by symlinking it to a shared repo.

---

## Notes
The script automatically creates the reviewers file if it doesn't exist.

Reviewers are sorted alphabetically for neatness.

Works best if your branch already has a GitHub PR associated.
