This repo exposes the issue I'm having with zed and a nix devenv setup.

If I open zed from the root:

`zed flaketest`

things work fine.

If I instead:

```
cd flaketest
zed .
```

I get the following in a terminal:

```
bash: line 6: compgen: command not found
set: Tried to modify the special variable 'PWD' with the wrong scope
set: Tried to modify the special variable 'SHLVL' with the wrong scope
warning: Could not set up terminal.
warning: TERM environment variable not set.
warning: Using fallback terminal type 'xterm-256color'.
warning: Could not set up terminal.
warning: TERM environment variable not set.
warning: Using fallback terminal type 'xterm-256color'.
/nix/store/sk8z3kdy6iaky6sg972k6fkh3iw2rn3d-bash-5.2p37/bin/bash: line 1: env: command not found
/nix/store/sk8z3kdy6iaky6sg972k6fkh3iw2rn3d-bash-5.2p37/bin/bash: line 1: env: command not found
Error: $HOME must be set to run brew.
fish: Unknown command: starship
/Users/viktor/.config/fish/config.fish (line 25):
starship init fish | source
^~~~~~~^
from sourcing file /Users/viktor/.config/fish/config.fish
	called during startup
/nix/store/mmwqalliqz09swrrgiy8r4sf95v51rdq-any-nix-shell-2.0.1/bin/.any-nix-shell-wrapped: line 55: cat: command not found
/Users/viktor/dev/lightbend/kalix/infra-aws/scripts/aws-auth-functions.sh: line 8: dirname: command not found
bash: line 6: awk: command not found
bash: line 6: awk: command not found
bash: line 6: awk: command not found
direnv: error couldn't find a cache directory for direnv
@studio ~/U/v/d/z/flaketest (main)>
```

seems just like the entire _env_ is broken.

An .envrc _without_ nix flakes seems to work just fine:

```
cd nonflaketest
zed .
```


This was all working fine about a week ago.


So just to visualize — when its working, I get my fish shell and everything looks fine and dandy:

<img width="1153" alt="image" src="https://github.com/user-attachments/assets/6b477413-b0e4-46e3-83d5-dc60374b394c">


When I open zed from within a devenv-folder it tries bash and seem to have no env setup at all:

<img width="1194" alt="image" src="https://github.com/user-attachments/assets/08141c60-83fe-4fb6-9a8e-2a1469afb523">

