This repo contains an ansible playbook for configuring a macOS machine the way I like it.

## Pre-reqs and manual steps

- Install homebrew `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
- Install pip with `$ sudo easy_install pip`
- Install ansible with `sudo pip install ansible --quiet` OR with `pip install -r requirements.txt` from this project's root
- Install these: `sudo pip install paramiko PyYAML jinja2`
- Install Java8 via [Oracle install page](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and take note of the destination
- Add a `group_vars/secrets` file for variables with secrets (i.e. passwords). I actually don't think any of the tasks use these, but I set this up so it's clear where they should go if needed in the future.

## Things you should probably update if you aren't me
- `ansible.cfg`
- `group_vars/all`
- `roles/java/vars/main.yml`
  - This is where you should put the Java version and location you took note of after installing Java from Oracle

OPTIONAL:
- `roles/dotfiles/vars/main.yml`
  - You'll probably want to clone [my separate dotfiles repo](https://github.com/parkeristyping/dotfiles) and use your clone instead
- `roles/spacemacs` -> this has my specific Spacemacs setup and is by far the most customized role. I'm guessing you'll at least want to point it at your own `.spacemacs.d`.

And, if there are any roles you want to exclude entirely, you can just remove them from `main.yml`.

## Usage

Once you've done the pre-reqs and tweaked this to the degree you want, just run `make full-setup` to run everything in `main.yml`.
