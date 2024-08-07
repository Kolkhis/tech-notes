# Programmable Bash Completion

You can extend the default bash autocompletion (or tab completion) in Bash.

## Where to put completions

##### From `/usr/share/doc/bash-completion/README.Debian`:
bash-completion for Debian
--------------------------

Completions are kept in `/usr/share/bash-completion/completions`.

If a package installs its completion files under `/etc/bash_completion.d/`,
bash-completion is still able to use them, but bash-completion itself does
not install any files under that directory.

If you are a package maintainer, you are encouraged to use
`dh_bash-completion(1)`, which will take care of installing third-party
completions into the appropriate directory.

-- David Paleino `<dapal@debian.org>` Sun, 10 Apr 2011 15:33:19 +0200
-- Gabriel F. T. Gomes `<gabriel@inconstante.net.br>` Mon, 12 Feb 2018 21:46:42 -0200
