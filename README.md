# github_demo<br>
A simple demo repository to show the basic Git workflow<br>
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
git mv: you can update file changes or file location status including delete and new file status at the staged status simultaneously<br>
git log: <br>
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

### how to rename filename and moving file in git<br>
git mv file_name new_file_name<br>
#### if you use bash mv commands<br>
mv file_name new_file_name<br>
git add -A : you need to use -A option since add command only track new file and ignore deleted old_file status<br>
#### if you rename by GUI operations<br>
git add new_file_name (: better to avoing using git add -A because your methods(GUI) will be remained or you can add the string to .gitignore)<br>
git add -u (: to make sure git understand we are just renaming file)<br>

### how to delete files in git<br>
#### if you haven't add file at staged area<br>
rm file_name<br>
#### if you added file at staged area<br>
git rm file_name (the files you can see with "git ls-files" commands)<br>
#### if you tracked files by git removed by mistakes<br>
git reset HEAD file_name (or)<br>
git restore file_name (I personally prefer this one tho teacher used the one above because I don't want to use reset)<br>
#### want to include delete status at staged area and commit<br>
git add -A<br>
git commit<br>

### how to have fun with log commands<br>
#### abbreviate commit ID<br>
git log --abbrev-commit<br>
#### see clear and neat<br>
git log --oneline --graph --decorate<br>
#### see specific logs<br>
git log commit_newer_ID...commit_older_ID<br>
#### specify the date(like 3 days ago)<br>
git log --since="3 days ago"<br>
#### check the rename history for file<br>
git log --follow -- file_name<br>
#### check the diff the specific commit<br>
git show commit_ID<br>

### how to compare files<br>
#### compare local working dir vs staged area<br>
git diff<br>
git difftool<br>
#### compare local working dir vs local repository<br>
git diff HEAD<br>
git difftool HEAD <br>
#### compare staged area vs local repository<br>
git diff --staged<br>
git difftool --staged<br>
#### compare specific file<br>
git diff -- (path)file_name<br>
git difftool -- (path)file_name<br>
#### compare commits<br>
git diff commit_id commit_other_id <br>
git difftool commit_id commit_other_id (HEAD: latest commit on the current branch)<br>
#### compare local repo vs remote repo<br>
git diff local_branch_name origin/remote_branch_name<br>
git difftool local_branch_name origin/remote_branch_name (origin: refer to remote)<br>
#### compare local repo1 vs local repo2<br>
git diff local_branch1 local_branch2<br>
git difftool local_branch1 local_branch2<br>
<br>

### Branch <br>
#### show all branch(includes remote branches)<br>
git branch -a<br>
#### create new branch<br>
git branch new_branch_name<br>
#### change the current branch<br>
git checkout your_branch<br>
### change branch name<br>
git branch -m branch_name new_branch_name<br>
### delete branch<br>
git branch -d branch_name (not allowed when you are there)<br>
### create new branch and mv at the same time<br>
git checkout -b branch_name<br>
<br>

### Merge<br>
#### Fast Forward Branch Merge: only works when target branch does not have any changes from your current branch<br>
After commiting--<br>
git checkout main_branch<br>
git merge target_branch<br>
git log --oneline --decorate --graph : check if the current commit points target_branch & merged_branch<br>
#### None Fast Forward Branch Merge: commits in target_branch will be different but merge_branch will integrate and merge all commits at the same time<br>
After commitng--<br>
git checkout main_branch<br>
git merge target_branch --no-ff<br>
git log --oneline --decorate --graph : check if the current commit integrates all commits in merge_branch<br>
#### Automatic Merge: <br>
After commiting at target_branch--<br>
After different commiting at main_branch--<br>
git merge target_branch : eventually main_branch will merge unless merge does not have conflicts (changes in same files) because main is always prioritized<br>
#### Conflict Merge Resolution: when conflict happens is when multipul branches have different changes at the same time<br>
After commiting changes for file1 at target_branch--<br>
After commiting changes for file1 at main_branch--<br>
git checkout main<br>
git merge target_branch : Conflicts happens => how to resolve below<br>
git mergetool: pick up the choices you have and save<br>
git commit -m "Resolved Merge conflicts"<br>
git status<br>
Interestingly, git will automatically create .orig file after resolving conflicts to backup! Therefore, lots of people add "*.orig" in .gitignore<br>
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
git config --global alias.hist "log --oneline --graph --decorate --all"<br>
git config --global alias.logn "log --name-status --oneline"<br>
git config --global alias.firstcom "commit --allow-empty -m \"Initial commit\""<br>
git config --global alias.dtool "difftool"<br>
git config --global alias.mtool "mergetool"<br>
<br>

### memo<br>
git status can track consistently for the same file like mod1, mod2<br>