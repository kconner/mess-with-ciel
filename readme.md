```sh
# refer: https://github.com/ciel-lang/CIEL/blob/master/docs/install.md

brew install roswell rlwrap

# sbcl is roswell's default lisp.
# it comes with asdf, but the version is too old.
ros install asdf

# add ciel project
cd ~/.roswell/lisp/quicklisp/local-projects
git clone https://github.com/ciel-lang/CIEL

# cd CIEL
# had to replace sbcl with $(LISP) once:
# LISP=ros QLDIR=~/.roswell/lisp/quicklisp/local-projects make ql-deps
# that took no action, so I gave up and:

cd ~/.roswell/lisp/quicklisp/local-projects
git clone https://github.com/alex-gutev/cl-environments
git clone https://github.com/alex-gutev/cl-form-types
git clone https://github.com/ruricolist/moira
git clone https://github.com/vindarel/progressons
git clone https://github.com/vindarel/termp
git clone https://github.com/lisp-maintainers/file-finder
git clone https://github.com/Shinmera/dissect
git clone https://gitlab.common-lisp.net/misc-extensions/misc-extensions
git clone https://github.com/slburson/fset
git clone https://github.com/lisp-maintainers/clesh

# build ./ciel:

cd ~/.roswell/lisp/quicklisp/local-projects/CIEL
LISP=ros make build

# if ciel/repl complains, make it happy and then retry
ln -s ~/.roswell/lisp/quicklisp ~/quicklisp

./ciel
* (sort (mapcar #'package-name (list-all-packages)) #'string<)

# or just load it:

rlwrap ros run
* (ql:quickload :ciel)
* (sort (mapcar #'package-name (list-all-packages)) #'string<)
```
