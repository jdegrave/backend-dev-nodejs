# How to Setup Your Development Environment

- Open terminal using `command+space` to open Spotlight and type `terminal` into the search field
- Type `git` and download anything if there are prompts. Otherwise, you should see a usage guide.
- Install nvm:
  ```sh
  curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh | bash
  ```
- Create your bash profile `touch ~/.bash_profile`
- Open your bash profile `vim .bash_profile`
- Update your bash profile to include a path to your install of nvm: (use `command + v` to paste)
  ```sh
  export NVM_DIR="$HOME/.nvm"
  [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
  ```
  \sMake sure the first line has the full export command, since that was causing us problems in class yesterday. Manually fix it in your bash profile if you have to.
- Exit vim via `esc`, then press and hold `shift`, then press `z` twice
- Completely quit your terminal `command + q`
- Reopen terminal
- Install Node 6.6: `nvm install 6.6`
- Install Node 4.5: `nvm install 4.5`
- Use Node 6.6: `nvm use 6.6`
