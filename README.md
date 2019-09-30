### Configuration

- Generate a fresh SSH keypair
- Add the public key as a write-access deploy key to the repo
- Create a new secret called `DEPLOY_KEY` with the private key in PEM format

### Notes

- We hardcode Github's SSH pubkeys into our known_hosts for security reasons
    - these are gotten via: `ssh-keyscan github.com`
- Expects `develop` branch to exist already by convention

#### Creates pull requests as follows:

- If we’re on master:
    - Open PRs with changes from head branch master onto base branches matching:
        - 'release/.*'
        - 'hotfix/.*'
- If we’re on a branch matching release\/.*:
    - Open PRs from each release branch to develop
- If we’re on develop:
    - Open PRs with changes from head branch develop onto base branches matching 'sprint/.*'
