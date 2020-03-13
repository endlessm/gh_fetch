gh_fetch
========
### Downloader and updater for your github repos.

- Did you ever needed to keep a backup of a large number of GitHub repos?
- Did you ever need to start using your dev machine quickly but had to clone repos one by one?
- Did you ever need to update (fetch) a ton of repositories from GitHub but you had to do it one by one?


**gh_fetch** is designed to fix all of these problems by automating the process to the maximum extent possible. This tool will go through your (or another account's) GitHub repos both public and private including repositories from organizations you are a member of and fetch the most recent changes for it, cloning the relevant repos if they are not already downloaded. Feature set will be expanding per my current needs but you are free to fork and issue a pull request.

**Note: This code works with both Python3 (default) and Python2 (when invoked with `python2` prefix)**

```
$ ./update_repos -h
usage: update_repos [-h] [--version] [-d DIRECTORY] [-t TOKEN_FILE] [-s] [-m]
                    [-x] [--exclude-forks] [--exclude-orgs]
                    [--include-org-forks] [--include-public-org-repos]
                    [--full-backup] [--debug]
                    username [token]

Retrieve and/or update local copies of GitHub-hosted repos

positional arguments:
  username              GitHub username that will be used for cloning and
                        fetching
  token                 GitHub auth token for that username. You can create
                        one at https://github.com/settings/applications

optional arguments:
  -h, --help            show this help message and exit
  --version             show program's version number and exit
  -d DIRECTORY, --directory DIRECTORY
                        Target directory for cloning and fetching
  -t TOKEN_FILE, --token-file TOKEN_FILE
                        File containing the github token
  -s, --ssh             Fetch repositories using ssh
  -m, --mirror          Mirror bare repositories instead of making full
                        checkouts
  -x, --exclude-own     Exclude own repositories in the updates
  --exclude-forks       Exclude forked repositories from the updates
  --exclude-orgs        Exclude repos that are in user's orgs (this does not
                        filter the ones you have)
  --include-org-forks   Include forked repos that are in user's orgs
  --include-public-org-repos
                        Include public repos that are in user's orgs
  --full-backup         Include all repository content
  --debug               Enable debugging output
```

## Examples

- Getting all your repos:
```
./update_repos -d /opt/checkout --exclude-orgs sgnn7 1234567890abfdefghijkl
```

- Backing up all organizational repos:
```
./update_repos -x -d ~/backups --include-org-forks --include-public-org-repos backup-user 1234567890abfdefghijkl
```

## TODO
- Scrubbing of remote endpoints
- Lots of testing

## Contributors
 - Srdjan Grubor ([@sgnn7](https://github.com/sgnn7))
 - Dan Nicholson ([@dbnicholson](https://github.com/dbnicholson))
 - Will Thompson ([@wjt](https://github.com/wjt))
 - Nimrod Adar ([@adarnimrod](https://github.com/adarnimrod))
