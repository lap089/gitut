# GitHub Tutorial

## Git Basics

###  Git configuration
* Username:  
  ```git config --global user.name "Your Name"```
* E-mail:  
  ```git config --global user.email "your@email.com"```
* Editor:  
  ```git config --global core.editor editor-shortcut```  
  ```git config --global core.editor "path/to/your/edtitor"```
* Get a specific configuration:  
  ```git config [field]```
* List all configrations:  
  ```git config --list```

### Git workspace setup
* Initialize current folder for Git system: (required to be an empty folder)  
  ```git init```
* Initialize a new child folder (of current one) for Git system:  
  ```git init [path]```
* Clone an existing repository to current folder: (empty folder required)  
  ```git clone [repository-url]```
* Clone an existing repository to a child folder of current: (empty folder required)  
  ```git clone [repository-url] [path]```

### Git Lifecycle
* Overview:

![Git lifecycle](https://git-scm.com/book/en/v2/book/02-git-basics/images/lifecycle.png)

* Add a file to staged: (from both untracked and modified)
  * A specific folder/file:  
    ```git add [path]```
  * Everything:  
    ```git add [ * | . | -A ]```
  * Everything except _removed_ files:  
    ```git add --ignore-removal .```
  * Everything except _new_ files: (```-u``` stands for "update")  
    ```git add -u```
* Removal:  
  * Remove a file completely from staged or unmodified area and stage that removal:  
    * Productive way:  
      ```git rm [path]```
    * Traditional way:  
    ```rm [path]```  
    ```git add [path]```
  * Remove ```[path]``` in the next commit but there is a whole new file which is untracked.  
    ```git rm --cached [path]```
* Unstage:
  * A file:  
    ```git reset [path]```
  * Everything:  
    ```git reset```
* Undo everything and revert back to the latest commit:  
  ```git reset --hard```
* Move a file from one place to another and stage it:
  * Productive way:  
  ```git mv [from-path] [to-path]```
  * Traditional way:  
    ```mv [from-path] [to-path]```  
    ```git rm [from-path]```  
    ```git add [to-path]```
* Commit from staged to unmodified:
  * Commit with an inline message:  
    ```git commit -m```
  * Commit with a pop-up editor (specified by core.editor):  
    ```git commit```
  * Commit by replacing the last commit:  
    ```git commit [ | -m ] --amend```
* Check status of current workspace:
  * Status of workspace in general:  
    ```git status```
  * Log of commits throughout the history:  
    ```git log [ | -p | --stat | --pretty ]```
    * ```-p```: difference between each commits.
    * ```--stat```: how many lines are modified, inserted or removed
    * ```--pretty```: show logs with specified format. Go [here](https://git-scm.com/docs/pretty-formats) for more infos.

### Git Branch
* Create a new branch:   
  ```git branch [branch-name]```
* Rename a branch:
  * Current branch:  
    ```git branch -m [new-name]```
  * Another branch: 
    ```git branch -m [new-name] [branch-name```
* Switch to another branch:  
  * Requirements for switching is current workspace must be clean.  
    No untracked files or modified files that haven't been committed.
  * If a branch already exists:  
  ```git checkout [branch-name]```
  * If a branch does not exist and it should be created:
    * Productive way:  
      ```git checkout -b [branch-name]```
    * Traditional way:  
      ```git branch [branch-name]```  
      ```git checkout [branch-name]```
* Merge work from ```[branch-name]``` to current branch:  
  ```git merge [branch-name]```
  * Conflicts:  
  ```<<<<<<< HEAD:[conflicted-file]```   
  ```[Code exists in current-branch]```  
  ``` ======= ```  
  ```[Code exists in branch-name]```  
  ```>>>>>>> [branch-name]:[conflicted-file]```
    * Resolve conflicts and remove ```<<<<<<<```, ``` ======= ``` and ```>>>>>>>```.
    * Add the ```[conflicted-file]``` to staged and then it is merged.
* Delete a branch:
  ```git branch [ -d | -D ] [branch-name]```
  * ```-d```: delete a branch but canceled if that branch is not merged to its parent (with warning).
  * ```-D```: force a delete on a branch (without any warning)
* List all branches:  
  ```git branch [ | -v | --merged | --no-merged ]```
  * ```-v```: show branches with their last commits
  * ```--merged```: branches merged to current branch.
  * ```--no-merged```: branches not merged to current branch.
* Branch is just an alias for a commit. Therefore, `checkout` can be applied to move HEAD to a commit:  
  ```git checkout [commit-id]```
  * Checking out this way results in "detaching" HEAD from branches (no branch is attached with HEAD).
    * Create a new branch and that branch is attached to current commit with HEAD.
    * Otherwise, any new commit is not tracked by any branch but HEAD's history can be shown to see it:  
      ```git reflog```
* Stash: save all working tree and the staged area (the index) to a "safe" place
  ```git stash [ | save ]```
  * Show shashes:
    * All stashes:  
      ```git stash list```
    * A stash:
      ```git stash show stash@{i}```
  * Apply a stash:
    * Most recent one:
      ```git stash apply```
    * At a stash history: (with the format `stash@{i}`, retrieved from `git stash show`)
      ```git stash apply stash@{i}```
  * Drop a stash:
    * Most recent one:  
      ```git stash drop```
    * At a stash history:  
      ```git stash drop stash@{i}```

## Workflow
