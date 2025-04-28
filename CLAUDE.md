This is a set of zsh utils that I add to my path to run on my mac.

They should either use zsh or python with a self-contained uv shebang to make them executable.

Read ./docs/uv-guide.md for how to do the latter; use it if needed.

TODO:

The following are helpful to have in a git-config, but not sure how to make them installable
like this.

- `git mm` fetch (only) master from remote and merge it into the current branch.
- `git nb ...` checkout -b makes a new branch from current state; this instead fetches master from remote and then checks out a new branch with the provided name from that up-to-date master.
- `git gb` fetches a branch from remote and checks out $USER/that-branch as a new branch.
