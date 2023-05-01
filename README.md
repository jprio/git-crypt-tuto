Référence! 
* https://dev.to/heroku/how-to-manage-your-secrets-with-git-crypt-56ih

* install git-crypt :
sudo apt install git-crypt

* create project (ex cargo new git-crypt-tuto)
* use git-crypt
git-crypt init

* export and save key
git-crypt export-key ../git-crypt-key

This command creates a copy of the git-crypt symmetric key that was generated for this repository. We're putting it in the directory above this repository so that we can re-use the same key across multiple git repositories.

This git-crypt-key the file is important. It's the key that can unlock all the encrypted files in our repository. We'll see how to use this key later on.

* tell what to encrypt by creating a .gitattributes file at the root of our repository:
by default :

jp@LAPTOP-KRPIGAD3:~/dev/code/rust/git-crypt-tuto$ git-crypt status
not encrypted: .envrc
not encrypted: .gitignore
not encrypted: Cargo.lock
not encrypted: Cargo.toml
not encrypted: README.md
not encrypted: src/main.rs

echo ".envrc filter=git-crypt diff=git-crypt" > .gitattributes

jp@LAPTOP-KRPIGAD3:~/dev/code/rust/git-crypt-tuto$ git-crypt status
    encrypted: .envrc
not encrypted: .gitattributes
not encrypted: .gitignore
not encrypted: Cargo.lock
not encrypted: Cargo.toml
not encrypted: README.md
not encrypted: src/main.rs


=> https://github.com/jprio/git-crypt-tuto/blob/master/.envrc : not in plain text !

* Use it

Now we can locally "source .envrc"

* Auto-source .envrc file in new terminal : see direnv (https://direnv.net/)