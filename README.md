# fmt-adapter
An adapter repository to plug the fmt open-source formating library into the NJOY21 build system.

## Git Subtree
This repository uses a git subtree for the directory `src`. The remote from which the subtree is made is located at [https://github.com/fmtlib/fmt.git](https://github.com/fmtlib/fmt.git). Equivalently, you can use the ssh location at `git@github.com:fmtlib/fmt.git`.

To facilitate updating the subtree when it gets updated upstream, do the following:

```bash
# This only needs to be done once
git remote add fmt https://github.com/fmtlib/fmt.git

# Do this when you need to update the subtree
git subtree pull --prefix=src fmt master
```

# License
The code contained in this repository is covered by the license contained in the [LICENSE](LICENSE) file.

