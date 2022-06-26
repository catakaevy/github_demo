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

### Commit message fix<br>
git commit<br>
git commit --amend<br>
-- reopen and compose commit message again<br>

### how to rename filename and moving file in git<br>
git mv file_name new_file_name<br>
#### if you use bash mv commands<br>
mv file_name new_file_name<br>
git add -A : you need to use -A option since add command only track new file and ignore deleted old_file status<br>
#### if you rename by GUI operations<br>
git add new_file_name (: better to avoing using git add -A because your methods(GUI) will be remained or you can add the string to .gitignore)<br>
git add -u (: to make sure git understand we are just renaming file, changed_file)<br>

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

### how to rebase<br>
#### Normal case1(rebase from above_branch): fundamental reasone we use this is for when we want to continue developing (like creating codes) at proceeding branch but some changes happen to main or branch above your developing branch. Example below.<br>
git checkout -b your_dev_branch<br>
-- keep commiting and want to continue tasks here<br>
-- but someone edited and commited branch above your_dev_branch directly<br>
-- in this case, you should use them<br>
git rebase main (above_branch)<br>
#### Rebase Conflicts(if you want to leave rebase mode)<br>
git rebase --abort<br>
#### Rebase Conflicts(if you want to fix conflicts)<br>
git rebase main<br>
git mergetool<br>
(git add file_name)<br>
git rebase --continue<br>
(git rebase --skip)<br>
git log --oneline --graph --decorate --all<br>
#### Rebase remote branches<br>
-- publish commiting at local<br>
-- publish commiting at remote<br>
git fetch origin main : you need to update remote status at local git<br>
git status<br>
=> will say "Your branch and 'origin/main' have diverged<br>
git pull --rebase origin main<br>
<br>

### how to stash<br>
#### Normal case (when you are not ready to commit your changes in the current state and allow you to change gear and work on something else)<br>
-- modified file 1<br>
git stash (save)<br>
git status<br>
=> your modified untracked file is gone<br>
-- modified another file but you want to get back the stash state above 2<br>
git stash apply : this allow you to go back the state including the second modifications you saved with stash commands and see status too<br>
-- modified adding changes to modification1 and complete<br>
git commit<br>
git stash list : list all stash you saved in git<br>
git stash drop : you can drop the last unneccesary stash record after applying<br>
#### Stash Untracked / Pop<br>
git ls-files<br>
-- modification tracking_file.txt in ls-files<br>
vim non-trackedfile.txt<br>
git status<br>
=> shows modified state tracking_file.txt & Untracked files state, non-trackedfile.txt<br>
git stash<br>
=> only works for tracking_file.txt<br>
-- clean up stash<br>
git stash list<br>
git stash drop<br>
-- but you want to stash including Untracked files<br>
git stash -u : you can stash Ubntracked files too excluding files specified in .gitignore<br>
-- another new modification<br>
git stash pop: integrated commands (git stash apply & drop)<br>
#### Multiple Stashes<br>
-- if you want to stash several times, you should use this commands to identify each stashes well<br>
git stash save "Message"<br>
git stash list<br>
git show stash@{stack_num} : you can see what the chosen stash is<br>
git stash apply stash@{stack_num} : you can stash apply for specific stash<br>
git stash clear : you can stash all stash_lists at the same time<br>
#### Stashing into Branches: when you avoid commiting current changes on main or your current branches<br>
-- a bit messed up changes (like staged:1 tracked_file:2 Untracked_file:1 on main) and you want to avoid commiting at main branch<br>
git stash save -u: stash branch commands requires existing stash beforehand<br>
git stash branch new_branch_name<br>

### how to tag in git<br>
#### Lightweigh: tag allows us to refer specific commits<br>
git tag tag_name : Creating tag at latest commit<br>
git tag --list : show list of tag<br>
git show tag_name : works with tag_name commit<br>
git tag --delete tag_name : delete tag_name tag<br>
#### Annotated tags: Lightweigh tag + extra info(messages)<br>
git tag -a tag_name (or git tag tag_name -m "Message")<br>
-- open editor to add messages for this tag<br>
git tag --list<br>
git log --oneline --decorate --graph --all => same as Lightweight<br>
git show tag_name => you can see the message<br>
#### Comparision between tags<br>
git diff tag_name1 tag_name2<br>
git difftool tag_name1 tag_name2<br>
#### Taggin Previous Commits<br>
git log --oneline --decorate --graph --all<br>
-- copy commit_id<br>
git tag -a tag_name commit_id <br>
#### Update Tagging (for same tag_name)<br>
git tag -a same_tag_name -f commit_id<br>
#### Using Tag with Github<br>
git push origin target_branch tag_name<br>
-- In Github we can see at Releases (tags) and you can download zip or tar.gz file at that commit sources<br>
-- want to push all tags at one time in remote repo<br>
git push origin target_branch --tags<br>
-- want to delete tags after pushing remote repo<br>
git push origin :tag_name<br>

### Reset & Reflog & Revert : Unfortunately, teacher does not explain well here<br>
#### Reset soft: when you commited mistakingly in local<br>
git reset HEAD^(num): only undo the commit and it is more like your state will be movable to specific commit but in the staged area and local workdir do not have any changes<br>
git reset reflog_style(HEAD@num)<br>
#### Revert: when you pushed commit mistakingly in remote<br>
git revert commit_id<br>
#### Reflog<br>
git reflog : show logs of everything we've done including HEAD changes of resets or anything like that<br>



### git config_file<br>
.gitconfig is our config file for git setting<br>
my commands for git alias setting lists below<br>
<br>
git config --global alias.ss status<br>
git config --global alias.ls ls-files<br>
git config --global alias.sh stash<br>
git config --global alias.shls "stash list"<br>
git config --global alias.shap "stash apply"<br>
git config --global alias.shp "stash pop"<br>
git config --global alias.shd "stash drop"<br>
git config --global alias.shcl "stash clear"<br>
git config --global alias.shbr "stash branch"<br>
git config --global alias.tg tag<br>
git config --global alias.tga "tag -a"<br>
git config --global alias.tgls "tag --list"<br>
git config --global alias.tgd "tag --delete"<br>
git config --global alias.br branch<br>
git config --global alias.brm "branch -m"<br>
git config --global alias.brd "branch -d"<br>
git config --global alias.brdd "branch -D"<br>
git config --global alias.co checkout<br>
git config --global alias.cob "checkout -b"<br>
git config --global alias.adu "add -u"<br>
git config --global alias.adup "add -u -p"<br>
git config --global alias.com commit<br>
git config --global alias.coma "commit --amend"<br>
git config --global alias.mg "merge --no-ff"<br>
git config --global alias.mgff "merge --ff"<br>
git config --global alias.rest restore<br>
git config --global alias.cp cherry-pick<br>
git config --global alias.log1 "log -1"<br>
git config --global alias.log2 "log -2"<br>
git config --global alias.log3 "log -3"<br>
git config --global alias.logo "log --oneline"<br>
git config --global alias.hist "log --oneline --graph --decorate --all"<br>
git config --global alias.logn "log --name-status --oneline"<br>
git config --global alias.rl reflog<br>
git config --global alias.firstcom "commit --allow-empty -m \"Initial commit\""<br>
git config --global alias.dtool "difftool"<br>
git config --global alias.mtool "mergetool"<br>
<br>

### memo<br>
git status can track consistently for the same file like mod1, mod2<br>