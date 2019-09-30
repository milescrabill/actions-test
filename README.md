### Configuration

- Generate a fresh SSH keypair
- Add the public key as a write-access deploy key to the repo
- Create a new secret called `DEPLOY_KEY` with the private key in PEM format

### Notes

- We hardcode Github's SSH pubkeys into our known_hosts for security reasons
    - these are gotten via: `ssh-keyscan github.com`
