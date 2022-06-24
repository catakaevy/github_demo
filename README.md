# github_demo<br>
A simple demo repository to show the basic Git workflow<br>
<br>
<br>
### git commands<br>
git status ; check your git status in 3 staging area(local, stage, .git-repository) => remote<br>
git init ; you can initialize git in your existing local folders or new folders<br>
git add ; you can add the untracted files by git to staging area and preferbly specifying file name<br>
- opt <br>
- -a: adding at the stage but only works for tracked files by git<br>
- .: adding all files recursively all the different levels<br>
git commit ; you can see which branch you are in and unique SHA-1 commit id after commiting <br>
git push (remote_branch_that_we_cloned_from) (remote_branch_name) ; always push from local to remote <br>
git ls-files : list tracking files in git<br>
git reset HEAD file_name: you can reset staged changes to untracked changes<br>
<br>
### Basic commands order (add=>commit=>pull=>push)<br>
git add -A or filename (avoid using .)<br>
git commit<br>
git pull origin main(or your branch): to avoid conflit when you share one repo with other developers<br>
git push<br>
<br>
### Restore commands order for staged area(0=>add=>reset=>restore=>0)<br>
git add file_name<br>
git reset HEAD file_name<br>
git restore file_name (or checkout file_name)<br>
<br>
### git config_file<br>
.gitconfig is our config file for git setting<br>
my commands for git alias setting lists below<br>
<br>
git config --global alias.ss status<br>
git config --global alias.br branch<br>
git config --global alias.brm "branch -m"<br>
git config --global alias.brd "branch -d"<br>
git config --global alias.brdd "branch -D"<br>
git config --global alias.co checkout<br>
git config --global alias.cob "checkout -b"<br>
git config --global alias.adu "add -u"<br>
git config --global alias.adup "add -u -p"<br>
git config --global alias.com commit<br>
git config --global alias.mg "merge --no-ff"<br>
git config --global alias.mgff "merge --ff"<br>
git config --global alias.cp cherry-pick<br>
git config --global alias.log1 "log -1"<br>
git config --global alias.log2 "log -2"<br>
git config --global alias.log3 "log -3"<br>
git config --global alias.logo "log --oneline"<br>
git config --global alias.logn "log --name-status --oneline"<br>
git config --global alias.firstcom "commit --allow-empty -m \"Initial commit\""<br>
<br>
<br>
### memo<br>
git status can track consistently for the same file like mod1, mod2<br>