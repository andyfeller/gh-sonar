# gh-sonar

A `gh` extension to scan and report on GitHub CLI extensions throughout user, organization, or enterprise account.

Reliably discovering GitHub CLI extensions is difficult because extension authors must reliably follow specific conventions:

1. Prefix the repository with `gh-`
1. Name extension asset(s) appropriately
1. Apply `gh-extension` topic to repository

`gh-sonar` aims to scan any type of GitHub account to find buried treasure! :pirate_flag:

## Quickstart

1. Download and install [jq](https://stedolan.github.io/jq/download/)
1. `gh extension install andyfeller/gh-sonar`
1. `gh sonar > you.md`
1. Profit! :moneybag: :money_with_wings: :money_mouth_face: :money_with_wings: :moneybag:

## Usage

> [!NOTE]
> To scan enterprises, run `gh auth refresh -s read:enterprise` to grant necessary scope.

```shell
$ gh sonar --help

Scan and report on GitHub CLI extensions throughout user, organization, or enterprise account.

USAGE
  gh sonar [flags] [ <organization> | <user> | -e <enterprise> ] > report.md

FLAGS
  -d, --debug                         Enable debugging
  -e, --enterprise                    Process as enterprise instead of organization; requires 'read:enterprise' scope
  -h, --help                          Display help usage
      --hostname=string               Hostname of the GitHub instance to authenticate with
  -m, --members                       Extend scanning to member repositories
  -p, --private                       Extend scanning to non-public repositories

EXAMPLES
  # Scan yourself
  $ gh sonar > you.md

  # Scan yourself including private repositories
  $ gh sonar -p > you.md

  # Scan yours truly
  $ gh sonar andyfeller > andyfeller.md

  # Scan organization including private repositories
  $ gh sonar -p tinyfists > tinyfists.md

  # Scan organization and member repositories including private repositories
  $ gh sonar -p -m tinyfists > tinyfists-with-members.md

  # Scan enterprise including private repositories
  $ gh sonar -p -e opensource > opensource.md

  # Scan enterprise and member repositories including private repositories
  $ gh sonar -p -m -e opensource > opensource-with-members.md
```

### Examples

<details><summary><b><code>$ gh sonar > you.md</code></b></summary>
<p>

```shell
Scanning user:  andyfeller
Scanning andyfeller repositories:  98
```

resulting output:

```markdown
# `andyfeller` user scan

1. [andyfeller/gh-artifact-purge](https://github.com/andyfeller/gh-artifact-purge)
1. [andyfeller/gh-catsup](https://github.com/andyfeller/gh-catsup)
1. [andyfeller/gh-codeowner-analysis](https://github.com/andyfeller/gh-codeowner-analysis)
1. [andyfeller/gh-dependency-report](https://github.com/andyfeller/gh-dependency-report)
1. [andyfeller/gh-kraken](https://github.com/andyfeller/gh-kraken)
1. [andyfeller/gh-montage](https://github.com/andyfeller/gh-montage)
1. [andyfeller/gh-publicize](https://github.com/andyfeller/gh-publicize)
1. [andyfeller/gh-quoth](https://github.com/andyfeller/gh-quoth)
1. [andyfeller/gh-repo-export](https://github.com/andyfeller/gh-repo-export)
1. [andyfeller/gh-ssh-allowed-signers](https://github.com/andyfeller/gh-ssh-allowed-signers)
1. [andyfeller/gh-sandbox](https://github.com/andyfeller/gh-sandbox)
1. [andyfeller/gh-sonar](https://github.com/andyfeller/gh-sonar)
```
</p>
</details>

<details><summary><b><code>$ gh sonar -p > you.md</code></b></summary>
<p>

```shell
Scanning user:  andyfeller
Scanning andyfeller repositories:  98
```

resulting output:

```markdown
# `andyfeller` user scan

1. [andyfeller/gh-artifact-purge](https://github.com/andyfeller/gh-artifact-purge)
1. [andyfeller/gh-catsup](https://github.com/andyfeller/gh-catsup)
1. [andyfeller/gh-codeowner-analysis](https://github.com/andyfeller/gh-codeowner-analysis)
1. [andyfeller/gh-dependency-report](https://github.com/andyfeller/gh-dependency-report)
1. [andyfeller/gh-kraken](https://github.com/andyfeller/gh-kraken)
1. [andyfeller/gh-montage](https://github.com/andyfeller/gh-montage)
1. [andyfeller/gh-publicize](https://github.com/andyfeller/gh-publicize)
1. [andyfeller/gh-quoth](https://github.com/andyfeller/gh-quoth)
1. [andyfeller/gh-repo-analysis](https://github.com/andyfeller/gh-repo-analysis)
1. [andyfeller/gh-repo-export](https://github.com/andyfeller/gh-repo-export)
1. [andyfeller/gh-ssh-allowed-signers](https://github.com/andyfeller/gh-ssh-allowed-signers)
1. [andyfeller/gh-app](https://github.com/andyfeller/gh-app)
1. [andyfeller/gh-hygiene](https://github.com/andyfeller/gh-hygiene)
1. [andyfeller/gh-org-team-repl](https://github.com/andyfeller/gh-org-team-repl)
1. [andyfeller/gh-promote-release](https://github.com/andyfeller/gh-promote-release)
1. [andyfeller/gh-sandbox](https://github.com/andyfeller/gh-sandbox)
1. [andyfeller/gh-sonar](https://github.com/andyfeller/gh-sonar)
```
</p>
</details>

<details><summary><b><code>$ gh sonar tinyfists > tinyfists.md</code></b></summary>
<p>

```shell
Scanning organization:  tinyfists
Scanning tinyfists repositories:  85
```

resulting output:

```markdown
# `tinyfists` organization scan

## organization extensions

1. [tinyfists/gh-nonsense](https://github.com/tinyfists/gh-nonsense)
1. [tinyfists/gh-pr-test](https://github.com/tinyfists/gh-pr-test)
1. [tinyfists/gh-testing-01](https://github.com/tinyfists/gh-testing-01)
```
</p>
</details>

<details><summary><b><code>$ gh sonar -m tinyfists > tinyfists.md</code></b></summary>
<p>

```shell
Scanning organization:  tinyfists
Scanning tinyfists repositories:  85
Scanning organization members:  19
Scanning amenocal repositories:  62
Scanning andyfeller repositories:  98
Scanning apdarr repositories:  20
Scanning BrytBoy repositories:  5
Scanning bval repositories:  73
Scanning david-wiggs repositories:  9
Scanning decyjphr repositories:  41
Scanning enyil repositories:  21
Scanning evgenyrahman repositories:  32
Scanning garnertb repositories:  124
Scanning igorcosta repositories:  191
Scanning JaredEgolf repositories:  20
Scanning jefeish repositories:  98
Scanning jonwicksy repositories:  7
Scanning katiem0 repositories:  33
Scanning kevfoste repositories:  32
Scanning polivebranch repositories:  11
Scanning ssulei7 repositories:  24
Scanning vila89 repositories:  61
```

resulting output:

```markdown
# `tinyfists` organization scan

## organization extensions

1. [tinyfists/gh-nonsense](https://github.com/tinyfists/gh-nonsense)
1. [tinyfists/gh-pr-test](https://github.com/tinyfists/gh-pr-test)
1. [tinyfists/gh-testing-01](https://github.com/tinyfists/gh-testing-01)

## member extensions

1. [amenocal/gh-pin-actions](https://github.com/amenocal/gh-pin-actions)
1. [andyfeller/gh-artifact-purge](https://github.com/andyfeller/gh-artifact-purge)
1. [andyfeller/gh-catsup](https://github.com/andyfeller/gh-catsup)
1. [andyfeller/gh-codeowner-analysis](https://github.com/andyfeller/gh-codeowner-analysis)
1. [andyfeller/gh-dependency-report](https://github.com/andyfeller/gh-dependency-report)
1. [andyfeller/gh-kraken](https://github.com/andyfeller/gh-kraken)
1. [andyfeller/gh-montage](https://github.com/andyfeller/gh-montage)
1. [andyfeller/gh-publicize](https://github.com/andyfeller/gh-publicize)
1. [andyfeller/gh-quoth](https://github.com/andyfeller/gh-quoth)
1. [andyfeller/gh-repo-export](https://github.com/andyfeller/gh-repo-export)
1. [andyfeller/gh-ssh-allowed-signers](https://github.com/andyfeller/gh-ssh-allowed-signers)
1. [andyfeller/gh-sandbox](https://github.com/andyfeller/gh-sandbox)
1. [andyfeller/gh-sonar](https://github.com/andyfeller/gh-sonar)
1. [apdarr/gh-artado](https://github.com/apdarr/gh-artado)
1. [igorcosta/gh-genissues](https://github.com/igorcosta/gh-genissues)
1. [igorcosta/gh-lazy](https://github.com/igorcosta/gh-lazy)
1. [katiem0/gh-branch-rules](https://github.com/katiem0/gh-branch-rules)
1. [katiem0/gh-collaborators](https://github.com/katiem0/gh-collaborators)
1. [katiem0/gh-environments](https://github.com/katiem0/gh-environments)
1. [katiem0/gh-export-secrets](https://github.com/katiem0/gh-export-secrets)
1. [katiem0/gh-migrate-rulesets](https://github.com/katiem0/gh-migrate-rulesets)
1. [katiem0/gh-organization-webhooks](https://github.com/katiem0/gh-organization-webhooks)
1. [katiem0/gh-seva](https://github.com/katiem0/gh-seva)
1. [ssulei7/gh-dormant-users](https://github.com/ssulei7/gh-dormant-users)
1. [ssulei7/gh-runner-usage](https://github.com/ssulei7/gh-runner-usage)
1. [ssulei7/gh-test-extension](https://github.com/ssulei7/gh-test-extension)
```
