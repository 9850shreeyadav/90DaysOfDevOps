# Day 23 - Git Branching & Working with GitHub  https://git-scm.com/cheat-sheet

# Task 1: Understanding Branches
  1.  What is a brand in Git
   - A branch in Git is a movable pointer to a commit. it allows to add or update the code features without affecting the main branch. 
  3.  Why do we use branches instead of committing everything to main?
   -  We use branches to keep the main branch(master) stable, work on feature safly, allow multiple devs to work in parallel.  
  4.  What is HEAD in Git?
   -  HEAD is a pointer that refers to the current branch. basically it tells git where new commits will be added.  
  5.  What happens to your files when you switch branches?
   -  When switching branches, Git updates the working directory to match the selected branch. Files may appear, disappear, or change depending on what exists in that branch.

 # Task 3 Branching Commands
  1. Create a new repository on GitHub (do NOT initialize it with a README) Done
     <img width="693" height="108" alt="image" src="https://github.com/user-attachments/assets/4d65b09c-8c87-492a-8896-190a096a2969" />

  2. Connect your local devops-git-practice repo to the GitHub remote
     -  git init
     -  git remote add origin https://github.com/username/devops-git-practice.git
             
  3. Push your main branch to GitHub
     -  git push -u origin main
       
  5. Push feature-1 branch to GitHub
     -  git checkout -b feature-1
     -  git push --set-upstream origin feature-1
  
  7. Verify both branches are visible on GitHub
     <img width="926" height="653" alt="image" src="https://github.com/user-attachments/assets/5973dda6-294d-4fcb-9ca0-2af7d608ef2c" />

  8. Difference between origin and upstream?
     -  origin is the default name for the remote repository that you cloned from or you own
     -  upstream is the original repository you forked from.
    
# Task 2 Branching Commands

1.  List all branches in your repo
   -  git branch
2.  Create a new branch called feature-1
   -  git branch feature-1  
3.  Switch to feature-1
    -  git switch feature-1
4.  Create a new branch and switch to it in a single command — call it feature-2
    -  git checkout -b feature-2
5.  Try using git switch to move between branches — how is it different from git checkout?
    -  git checkout: it is a old command which switches the branch and can restrore the files
    -  git switch: this only switches the branch
6.  Make a commit on feature-1 that does not exist on main (Done)
    -  git log: to verify the commits are different on both branches

#  Task 4: Pull from GitHub
  What is the difference between git fetch and git pull?
  ## Git Fetch vs Git Pull

| git fetch | git pull |
|-----------|----------|
| Downloads changes from the remote repository | Downloads changes **and merges** them into your current branch |
| Does **not** modify your local branch or working directory | **Updates** your local branch and working directory |
| Safe — cannot break your branch | Can cause merge conflicts if changes overlap |
| Only updates remote-tracking branches (e.g., `origin/main`) | Updates current branch directly |
| Lets you review changes before merging | Automatically merges changes after fetching |
| Use when you want more control over integration | Use when you want to quickly update your branch |

# Task 5: Clone vs Fork
  1.  What is the difference between clone and fork?
      -  clone: clone used to cloning the repo on local.
      -  fork: Creates a copy of someone else’s repository under your GitHub account.
  3.  When would you clone vs fork?
      -  clone: Use when have access already and want to add any feature into it.
      -  fork: Use when you want to contribute to someone else’s project.
  5.  After forking, how do you keep your fork in sync with the original repo?
      -  git remote add upstream https://github.com/original-owner/repo.git
      -  git fetch upstream
      -  git switch main
      -  git merge upstream/main
      -  git push origin main 


     
