bash script to add ssh keys from Github to your `~/.ssh/authorized_keys` file.

Or use a one liner like this to add all members of an organization `$ORG` to user `$U`:

```sh
curl -s https://api.github.com/orgs/${ORG}/members  | jq -r ".[].login" | xargs -I {} printf "https://github.com/{}.keys\n" | xargs curl -s >> /${U}/.ssh/authorized_keys
```
