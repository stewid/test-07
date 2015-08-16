# Add an existing project to GitHub using SSH and git2r

Create a new repository on GitHub before running the following R code.

```r
library(git2r)

# 1) Create a new repository
repo <- init("test-07")

# 2) Add 'README.md' to local repository
add(repo, "README.md")

# 3) Commit staged 'README.md'. Add sessionInfo to commit message
commit(repo, message = "Initial commit", session = TRUE)

# 4) Add URL for the remote repository
remote_add(repo, "origin", "git@github.com:stewid/test-07.git")

# 5) Create SSH credentials
cred <- cred_ssh_key("~/.ssh/id_rsa.pub", "~/.ssh/id_rsa")

# 6) Push changes in local repository to GitHub
push(repo, "origin", "refs/heads/master", credentials = cred)
```
