# branchs
## local branch (non-tracking)
- git br
- .git/refs/heads
    
## remote branch
- branch on remote machine
- git remote show <remote>

## remote tracking branch
- a local cache of remote branch
- it's read only
- git fetch //used to syn with remote branchs 
- git br -r //origin/master
- under dir .git/refs/remotes/
- git remote prune <remote> //delete all stale remote-tracking branch

## local tracking branch
- create branch to track remote br //git br --track branchname remote-branch
- local branch make update and sync with remote branch much more convienent
- git br -vv //show branch and it's tracking branch
- it's tracking remote tracking branch
- git pull //update remote tracking branch, then merge with local tracking branch

## Undo changes
1. Undo a pushed commit
`git revert <SHA>`
1. Fix last commit message
`git commit --amend -m "xxxx"`
1. Undo local changes
`git checkout -- <bad filename>`
1. Reset "local" change
`git reset --hard <last good SHA>`
1. Get back local resetted commit
`git reflog`
It only shows a list of times when HEAD changed, the data won't last forever.
Git will periodically clean up objects which are unreachable. Your reflogs is
yours and yours alone. Once get the commit `git reset --hard <SHA>` and 
`git checkout <SHA> -- <filename>` could be used to recover the data.

## Set remote urls
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
