Git is a opensource version control software used to manage code.


A git project can be thought of as having three parts:

    A Working Directory: where you’ll be doing all the work: creating, editing, deleting and organizing files
    A Staging Area: where you’ll list changes you make to the working directory
    A Repository: where Git permanently stores those changes as different versions of the project


The Git workflow consists of editing files in the working directory, adding files to the staging area, and saving changes to a Git repository.
In Git, we save changes with a commit, which we will learn more about in this lesson.





#core workflow
git init
    This means initialize, the command line sets up the tools to begin tracking changes made to the project.


git add filename
    Adds files from the working directory to the staging area.
    In order for Git to start tracking a file (like scene-1.txt), the file needs to be added to the staging area.


    git add filename_1 filename_2

        Use this variation when I want to add multiple files to the staging area.

    git add *
    git add .

        Use this to add all files in working directory.



git commit -m "message"
    This is the last step in our workflow;
    A commit permanently stores chnges from the staging area inside the repository.
    The -m "message" part is max 50 characters, and describes what the commit does in present tense.



git status
    Inspects the contents of the working directory and the staging area.



#status and back tracking


git log
    Shows all previous commits.
    Commits are stored chronologically in the repository and can be viewed with this command.

    From the terminal, the output will be something liek this;
    40 character SHA code that identifies the commit.
    Author, date time, and commit message.


        commit e2ec9ac574d97c15096e790913f995694cb4dc86
        Author: codecademy <ccuser@codecademy.com>
        Date:   Thu Dec 17 15:43:42 2020 +0000

            Complete first line of dialogue



git diff filename
    We can check the differences between the working directory and the staging area with this command



git show HEAD

    in Git the commit you are currently on is known as the HEAD commit.
    Thsi is usally the most recently made commit;
    use this show command above to show the HEAD


git checkout HEAD filename
git checkout -- filename
git checkout *

    this command restores the file in your working directory to look exactly as it did when you last made a commit (HEAD);
    Discarding changes in the working directory.
    Both commands do the same thing.

    The thrid command selects all;




git reset HEAD filename

    This command resets the file in the staging area to be the same as the HEAD commit.
    It does not discard file changes from the working directory, it just removes them from the staging area back to the HEAD commit.


git reset SHA1234

    This command resets the HEAD / most recent commit to the commit SHA1234 of your choice;
    SHA1234 is the first 7 characters of the unique SHA code of that commit.

    All the commits from the targeted reset commit and beyond is no longer a part of the project;
    It is basically rewinding a project's history.








# git branching
Up until this point you've worked with a single git branch called master.
Git allows us to create branches to experiment with versions of a project.
Changes made in branches will have no effect on the master branch until you are ready to merge.


git branch

    This command will show the branch that I am on with an asterisk along with the other branches in existence.



git branch new_branch

    This command will create new branch new_branch;
    make sure to name the branch something that describes the purpose of the branch.
    It can't contain white spaces.


git checkout branch_name

    This command will switch your current branch to another branch brnch_name.
    You can now work on this branch while master stays intact.

    You can work wih another branch just like the master one.




git merge branch_name

    You first switch back to the master branch, or whichever receive branch that you want to merge the changes in;

    This command merges the branch branch_name with the master branch;
    Make sure that you...
        - Your goal is to updat master with the changes you made in branch_name
        - branch_name is the giver branch, since it provides the changes.
        - master is the receiver branch since it accepts those changes.



    Outputs for merging;

        Fast forward
        - Fast foward means that the branch that is being merged already contains the most recent commit;
        - Thus git fast forwards master to be up to date with branch_name

        Merge conflict
        - Git doesn't know which changes you want to keep when there are two similar changes made in two branches.
        - Like changing the same line in different ways in your resume.

        - Git uses markings to indicate HEAD (master) version of the file and the branch_name version of the file like so;

            <<<<<<< HEAD
            master version of line
            =======
            branch_name version of line
            >>>>>>> branch_name



git branch -d branch_name

    In Git, branches are usually a means to an end.
    You create them to work on a new project feature, but the end goal is to merge that feature into the master branch.
    After the branch has been integrated into master, it has served its purpose and can be deleted.

    This command will delete the specified branch from your Git project



    git branch -D branch_name

        You need the -D option when branch_name was never merged into master



















# git teamwork
working with a shared remote repository with a team. Often using Github or other repo hosting sites.

    Typical git collaborative workflow;
    This workflow allows for smooth project development when working with a team of contributors.
    This way you always have and are working on the newest / up to date version of main on your local, as your remote repo;
    Then you can branch off into another branch, and work on a new feature and commit that feature branch to the remote repo for review.



        Fetch and merge changes from the remote - to your master / main.
        Create a branch to work on a new project feature
        Develop the feature on your branch and commit your work
        Fetch and merge from the remote again (in case new commits were made while you were working)
        Push your branch up to the remote for review - which would be worked on and hopefully eventually merged to main / master.






git clone remote_location clone_name

    remote_location -- tells Git where to go find the remote; this could be a web address (github repo) or a filepath;
    clone_name -- this is the name you give the directory in which Git will clone the repository


git remote -v

    You can see a list of Git project's remotes with this command.
    Where the fetch / pull / push destinations are.



git fetch

    This command will not merge changes from the remote into your local repository.
    It brings those changes onto what's called a remote branch.
    It fetches from the origin destination.


git merge origin/master

    After new commits have been fetched from origin, those commis are on origin/master branch.
    Your local master has not been updated yet, so you can't view or make changes to any of the work added.

    you can use this command to integrate origin/master into your local master branch;

    The receiving branch is your local master.




git pull

    Does something similar with merge origin / master.



git push origin your_branch_name

    This command will push your branch up to the remote, origin.
    From there, your team members can review your branch and merge your work into the master branch;
    making it part of the definitive project version.

    You are pushing your branch to the origin, others can now review this stuff on the origin.










===== GitHub and Git Configs =====
For setting up email addresses, you can do this on GitHub or on Git, either way works.



# configurations
git config --global user.name "User Name"
git config user.name "User Name"

    The option with --global sets the Git username for every single repository
    Whereas the other one sets it locally for that repo / working directory.

        git config user.name
        git config --global user.name

        Use these to check



git config --global user.email "email@example.com"
git config user.email "email@example.com"

    Similar to setting user.name on Git, you do the same for setting up your email address.


        git config user.email

        use to check;


https://docs.github.com/en/free-pro-team@latest/github/using-git/setting-your-username-in-git
https://docs.github.com/en/free-pro-team@latest/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address

    Use your confidential email address + PAT





# using github




### git pull requests
Pull requests lets you tell others about changes you've pushed to a branch in a repository on GitHub.
Once a pull request is opened, you can discuss and review the potential changes with collaborators and add follow up
commits before your changes are merged into the base branch.


https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/about-pull-requests





…or create a new repository on the command line
echo "# git_practice" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/thewooniverse/git_practice.git
git push -u origin main



…or push an existing repository from the command line
git remote add origin https://github.com/thewooniverse/git_practice.git
git branch -M main
git push -u origin main












