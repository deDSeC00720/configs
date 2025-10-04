# configs

Collection of personal configuration files and scripts.

```bash
curl -s 'https://raw.githubusercontent.com/corvo-007/configs/refs/heads/main/setup.sh' -o setup.sh
chmod u+x setup.sh
./setup.sh
. .bashrc
```

Update the PS1 variable - \\[\033[01;31m\\]$(git_branch)\\[\033[00m\\]

# nvm

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

# Adding SSH key to git and github to use ssh
## Key generation

```bash
ssh-keygen -t ed25519 -C "email"
```

## Add key to ssh-agent

```bash
eval "$(ssh-agent -s)" # start ssh-agent in background

ssh-add ~/.ssh/id_ed25519 # add key to ssh-agent
```

## Add public key to github

Add the contents of ~/.ssh/id_ed25519.pub to github

## Add the key to git to sign commits

```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
```

## Sign commits by default

```bash
git config --global commit.gpgsign true
```

# Adding GPG key to git and github to sign commits
## Key generation

```bash
gpg --full-generate-key
```

## List keys

```bash
gpg --list-secret-keys --keyid-format=long
```

## Add public key to github

```bash
gpg --armor --export KEY-ID
```

Add the output of the above command to github

## Add key to git

```bash
git config --global user.signingkey KEY-ID
git config --global commit.gpgsign true
git config --global tag.gpgSign true
```
