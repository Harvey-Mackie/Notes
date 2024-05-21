# Core Concept
Git is a tool which is used for managing distributed version control. There are four key areas.
- Local Areas (on developers machine)
	1. Working Directory
		- The working directory is where you perform all your work: creating, editing, deleting and organizing files. It holds the actual files in your project and represents a single checkout of one version of the project.
	2. Staging Area (Index)
		- The staging area, also known as the index, is where Git prepares changes before they are committed to the repository. When you add changes (like with git add), you're moving them to the staging area, making them ready for a commit.
	3. Local Repository
		- This is where your project's history resides with all your commits and branches. It's a database of your project’s entire history, and it's managed by Git.
- Remote Areas (on remote server e.g. GitHub)
	4. Remote Repository
		- A remote repository is a version of your project that is hosted on the internet or network, enabling collaboration with others. Common hosting services include GitHub, Bitbucket, and GitLab. Changes are pushed to and pulled from the remote repository.

# Considerations 
- Merging vs Rebasing 
	- Rebasing looks more streamlined and clean as the commit history is in a linear timeline
	- Whereas, Merging creates a commit to link the branches together, resulting in an extra commit.
	- However, rebasing refactors history by creating new commits as it is essentially re-committing to the new branch which means the commit hashes will be different - commit-date will change as well.
	- The question lies in what is most important - **a tidy history or a true representation of the sequence of development**


# Cheat Sheat
### **Branch Management**

- **Create and Switch to New Branch:**
    
    **`git checkout -b feature/1223-branch-name`**
    
    Creates and checks out a new branch based on the current branch.
    
- **Switch to an Existing Branch:**
    
    **`git switch feature/123-test`**
    
    A modern command to switch branches, replacing **`git checkout`**.
    

### **Staging Changes**

- **Stage All Modified Files:**
    
    **`git add .`** 
    
    Adds all changed files in the directory to the staging area.
    
- **Stage Specific File or Directory:**
    
    **`git add filename.txt`**
    
    Adds changes from the specified files or directories to the staging area.
    
- **Interactively Stage Parts of Files:**
    
    **`git add --patch filename.txt`**
    
    Opens an interactive UI to select parts of a file to stage.
    

### **Committing Changes**

- **Commit with a Message:**
    
    **`git commit -m "commit message"`**
    
    Commits staged changes with a provided message.
    
- **Stage All & Commit with Detailed Message:**
    
    **`git commit -a`**
    
    Automatically stages all modified and deleted files (not new files) and opens an editor for a detailed commit message.
    

### **Pushing Changes**

- **Push to Remote Repository:**
    
    **`git push`**
    
    Pushes commits from the local branch to the corresponding remote branch.
    
- **Push and Set Upstream Branch:**
    
    **`git push --set-upstream origin <local-branch-name>`** or **`git push -u origin <local-branch-name>`**
    
    Pushes the current branch and sets the remote as upstream.
    

### **Fetching and Pulling Changes**

- **Fetch Changes:**
    
    **`git fetch`**
    
    Downloads all the changes from the remote repository but does not integrate them into your local repository.
    
- **Pull Changes:**
    
    **`git pull`**
    
    Fetches changes from the remote repository and merges them into the current branch.
    

### **Merge and Rebase**

- **Merge Another Branch:**
    
    **`git merge feature/123-test`**
    
    Merges changes from the specified branch into the current branch.
    
- **Interactive Rebase:**
    
    **`git rebase -i <branch-name>`**
    
    Rebases the current branch onto the specified branch, allowing for interaction such as squashing or reordering commits.
    

### **Stashing and Cherry-picking**

- **Stash Current Changes:**
    
    **`git stash`**
    
    Temporarily stores all modified tracked files and stages changes.
    
- **Apply Stashed Changes:**
    
    **`git stash pop`**
    
    Restores the most recently stashed changes and removes them from the stash.
    
- **Cherry-pick a Commit:**
    
    **`git cherry-pick <commit-hash>`**
    
    Applies the changes from a specific commit to the current branch.
    

### **Undoing Changes**

- **Soft Reset to Previous Commit:**
    
    **`git reset --soft HEAD^`**
    
    Undoes the last commit but keeps the changes in your working directory.
    
- **Hard Reset (discard changes):**
    
    **`git reset --hard HEAD^`**
    
    Completely undoes the last commit and discards all changes in the working directory.
    
- **Restore File to Last Commit:**
    
    **`git restore file-path`**
    
    Restores the specified file to its state at the last commit.
    

### **Amend Commits**

- **Amend Most Recent Commit:`git commit --amend`**Modifies the most recent commit, allowing changes to files and/or the commit message.

### **View Commit History**

- **View Commit Log:`git log`**Displays a log of commits for the current branch.
