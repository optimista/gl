# `gl` script 
Script for creation and removal of Gitlab repositories directly from terminal.  
The script does check for existence of Vercel project and guides you through connecting it with repo.

## Prerequisites

### Gitlab CLI Installation

Script uses `python-gitlab` CLI.  
Follow the official instructions to intall it [here](https://python-gitlab.readthedocs.io/en/stable/install.html)  

#### Installation Guide

However, this should be enough to install it:

1. `pip install python-gitlab`.  
2. Create a Gitlab personal access token here: https://gitlab.com/-/profile/personal_access_tokens with `api`, `read_user`, `read_api`, `read_repository`, `write_repository` scopes (more [here](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)).
3. Create `~/.python-gitlab.cfg` with these contents:

```
[global]
default = main
ssl_verify = true
timeout = 5

[main]
url = https://gitlab.com
private_token = your_gitlab_personal_access_token_you_just_generated
```

More on configuring Gitlab CLI [here](https://python-gitlab.readthedocs.io/en/stable/cli.html#configuration).

## Installation

### Basic idea

Be sure to load the script in bin path (`gl/bin`) to your `$PATH`.

### Step-by-step

Just run this and you are fine.

```
cd ~/.bin
git clone git@github.com:optimista/gl.git
```

If you don't have `~/.bin` folder yet run this:   
[Don't forget to change `~/.zshrc` to your bash]

```
mkdir ~/.bin
echo 'for d in ~/.bin/*/bin; do export PATH="$d:$PATH"; done' >> ~/.zshrc
echo 'export PATH=~/.bin:$PATH' >> ~/.zshrc
```

### Explanation

I have all my scripts in `~/.bin` folder.  
Simple ones are in one file (`~/.bin/simplescript`).  
Complex ones are within a folder (`~/.bin/complexscript/bin/complexscript`).  
I load them in my `~/.zshrc` (if you use bash `~/.bashrc`).  

## Usage
```
gl myreponame# To generate a new project
gl rm myreponame# To remove existing project (must be run from parent directory)
```
