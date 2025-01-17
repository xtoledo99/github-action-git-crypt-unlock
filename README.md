# Github Action running git-crypt unlock

## Usage

### Example Workflow file

```
workflow "Test git-crypt" {
  on = "push"
  resolves = ["Unlock secrets"]
}

action "Unlock secrets" {
  uses="sliteteam/github-action-git-crypt-unlock@master"
  secrets=["GIT_CRYPT_KEY"]
}
```

### Secrets

- `GIT_CRYPT_KEY` **Required** Base64 encoded git-crypt key file.
  - Get it from an unlocked git-crypt env with:
    ```sh
    git-crypt export-key ./tmp-key && cat ./tmp-key | base64 | pbcopy && rm ./tmp-key
    ```

## Development

There are few dependencies

- git-crypt
- docker
- node (for npm script convenience and [gha](https://github.com/tschoffelen/gha) dependency)

### Running tests

```
npm install
npm test
```
