# AWSP - AWS Profile Switcher

Easily switch between AWS Profiles

<img src="demo.gif" width="500">

## Prereqs
Setup your profiles using the aws cli

```sh
aws configure --profile PROFILE_NAME
```

You can also leave out the `--profile PROFILE_NAME` param to set your `default` credentials

Refer to this doc for more information
https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

## Setup

Copy the binary to a directory in your $PATH:
```sh
cp awsp /usr/local/bin
```

Add the following to your `.bashrc` or `.zshrc` config
```sh
alias awsp="/usr/local/bin/awsp && set -o allexport && source ~/.awsp && set +o allexport"
```

## Usage
```sh
awsp
```

## Show your AWS Profile in your shell prompt
For better visibility into what your shell is set to it's helpful to configure your prompt to show the value of the env variable `AWS_PROFILE`.

<img src="screenshot.png" width="300">

Here's a sample of my zsh prompt config using oh-my-zsh themes

```sh
function aws_prof {
  local profile="${AWS_PROFILE:=default}"

  echo "%{$fg_bold[blue]%}aws:(%{$fg[yellow]%}${profile}%{$fg_bold[blue]%})%{$reset_color%} "
}
```

```sh
PROMPT='OTHER_PROMPT_STUFF $(aws_prof)'
```
