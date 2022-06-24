# github_demo
A simple demo repository to show the basic Git workflow


### git commands
git status ; check your git status in 3 staging area(local, stage, .git-repository) => remote
git init ; you can initialize git in your existing local folders or new folders
git add ; you can add the untracted files by git to staging area and preferbly specifying file name
- opt 
- -a: adding at the stage but only works for tracked files by git
- .: adding all files recursively all the different levels
git commit ; you can see which branch you are in and unique SHA-1 commit id after commiting 
git push (remote_branch_that_we_cloned_from) (remote_branch_name) ; always push from local to remote 
git ls-files : list tracking files in git
git reset HEAD file_name: you can reset staged changes to untracked changes

### Basic commands order (add=>commit=>pull=>push)
git add -A or filename (avoid using .)
git commit
git pull origin main(or your branch): to avoid conflit when you share one repo with other developers
git push

### Restore commands order for staged area(0=>add=>reset=>restore=>0)
git add file_name
git reset HEAD file_name
git restore file_name (or checkout file_name)

### git config_file
.gitconfig is our config file for git setting
my commands for git alias setting lists below

git config --global alias.ss status
git config --global alias.br branch
git config --global alias.brm "branch -m"
git config --global alias.brd "branch -d"
git config --global alias.brdd "branch -D"
git config --global alias.co checkout
git config --global alias.cob "checkout -b"
git config --global alias.adu "add -u"
git config --global alias.adup "add -u -p"
git config --global alias.com commit
git config --global alias.mg "merge --no-ff"
git config --global alias.mgff "merge --ff"
git config --global alias.cp cherry-pick
git config --global alias.log1 "log -1"
git config --global alias.log2 "log -2"
git config --global alias.log3 "log -3"
git config --global alias.logo "log --oneline"
git config --global alias.logn "log --name-status --oneline"
git config --global alias.firstcom "commit --allow-empty -m \"Initial commit\""


### memo
git status can track consistently for the same file like mod1, mod2