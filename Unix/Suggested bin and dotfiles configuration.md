
# Suggested bin and dotfiles configuration

Create a `bashrc` file in your home directory and include it from your `.profile` file

In `bashrc`, load bashrc from `~/bin/dotfiles/bashrc`

In `~/bin/dotfiles/bashrc`, load all other files under `/bash` (env, config, aliases)

	~/bin
		/dotfiles
			bashrc
			/bash
				env
				config
				aliases

Create standard dotfiles configuration layout

	mkdir -p ~/bin/dotfiles/bash && touch ~/bin/dotfiles/bashrc ~/bin/dotfiles/bash/{env,config,aliases}

Reload bashrc in terminal

	source bashrc
