
# Baseline tools

help
Display helpful information about builtin commands.
    help help
    help test
    help times
    help alias


info
You can use info to find out about any commands

    info ls
    info grep
    info head
    info echo







# Exploring and manipulating file systems with shell

pwd

cd
cd dir1/dir2


ls
ls dir1/dir2
ls -alt dir1/dir2

    • -a - lists all contents, including hidden files and directories
    • -l - lists all contents of a directory in long format
    • -t - order files and directories by the time they were last modified.

The -l option lists files and directories as a table. Here there are four rows, with seven columns separated by spaces. Here’s what each column means:
    For example;
    drwxr-xr-x  2 Joo  staff   64 Nov 21 17:44 password_encryptor
    -rw-r--r--  1 Joo  staff  621 Dec  5 20:00 project_pipeline.md

    1. Access rights. These are actions that are permitted on a file or directory.
    2. Number of hard links. This number counts the number of child directories and files. This number includes the parent directory link (..) and current directory link (.).
    3. The username of the file’s owner. Here the username is cc.
    4. The name of the group that owns the file. Here the group name is eng.
    5. The size of the file in bytes.
    6. The date & time that the file was last modified.

The name of the file or directory.



touch
touch dir1/dir2

mkdir
mkdir dir1/dir2

cp
cp item1 item2(or dir)
cp item1 item2 dir/
cp m*.txt dir1/
- This code will take everything that ends with a .txt and begins with m in the working direcory and move it to dir1.

mv
- similar to cp in its usage, but moves; similar syntax

rm
rm -r dir1
- -r starnds for recursive, is used for deleting directory and all its child;
- rm totally deletes things and is not recoverable
- -rf, f stands for force.





# Redirecting input and output
Through redirection you can direct the input and output of a command to and from other files and programs, and chain commands together in a pipeline.

    1. standard input, abbreviated as stdin, is information inputted into the terminal through the keyboard or input device.
    2. standard output, abbreviated as stdout, is the information outputted after a process is run.
    3. standard error, abbreviated as stderr, is an error message outputted by a failed process.


echo "Hello"
The echo command accepts the string “Hello” as standard input, and echoes the string “Hello” back to the terminal as standard output.


>
Takes the standard output of the command on the left, and redirects it to the file on the right.
If the output / redirect to a file doesn't exist - is is created.
    cat oceans.txt > contents.txt
    Here the standard output of cat oceans.txt is redirected to continents.txt





>>
takes the standard output of the command on the left and appends it to the file on the right.
    cat volcanoes.txt >> rivers.txt


<
takes the standard input from the file on the right and inputs it into the program on the left.

    Here, lakes.txt is the stdin for the cat command, and stdout appears in the terminal.


|
This is a pipe, and it takes the stdoutput of the command on the left and pipes it as a standard input to the command on the right.
You can think of it as a "command to command" redirction.
That pipes from command on the left to the command on the right.

    cat volcanoes.txt | wc
    Here the output of cat volcanoes.txt is the stdin of wc,
    The wc command outputs the number of lines, words and characters in volcanoes.txt respectively.

    cat volcanoes.txt | wc | cat > islands.txt
    Here the stdin output of cat volcanoes.txt is "piped" to the wc command.
    The stnadard output of wc is then "piped" to cat.
    Finally, the stdoutput of cat is redirected to islands.txt




sort
sort takes the stdin and orders it alphabetically for the stdout.
    sort lake.txt
    The lakes in sort lakes.txt are listd in alphabetical order.
    Sorting it as a sdout alone does not change the data / file itself, you would need to sort it and redirect the output of the sort to another file for it to be saved;
    Even redirecting it to itself

    cat lakes.txt | sort > sorted-lakes.txt
    Here the command taks the stdout from cat lakes.txt | pipes it to sort, then the stdout of sort is redirected to sorted-lakes.txt


uniq
stands for 'unique' and filters out adjacent, duplicate lines in a file - and outputs result as stdout

    cat deserts.txt

        Arctic Desert
        Sahara Desert
        Sahara Desert
        Arabian Desert
        Gobi Desert
        Kalahari Desert
        Gobi Desert

    uniq deserts.txt

        Arctic Desert
        Sahara Desert
        Arabian Desert
        Gobi Desert
        Kalahari Desert
        Gobi Desert

    Sahara is filtered out for duplicates, because Sahara Desert directly follows the previous one.
    Whereas Gobi Desert doesn't so it says.

    sort deserts.txt | uniq > uniq-deserts.txt
    Here we sort the deserts.txt and pipe that to a uniq, whose outputs are redirected to uniq-deserts.txt




grep
"global regular expression print"
It searches the files for lines that match a pattern and return the results (as in the strings themselves), it is also case sensitive.
A regular expression is a sequence of characters that define a search pattern.
You can often use regular expressions to search for patterns in files

    grep Moun mountains.txt
    Here grep searches for "Mount" in mountains.txt

    grep -i Mount mounains.txt
    The -i enables the command to be case insensitive.
    Here grep searches for capial or lowercase strings that match Mount in mountains.txt

    grep -R Arctic /home/ccuser/workspace/geography
    -R searches all files in a directory and outputs filenames and lines containing matches results.
    -R stands for recursive.
    Here, the grep -R searches the dirctory for the string "Arctic" and outputs all filenames and lines with matched results.

    grep -Rl
    -Rl searches all files in a directory and outputs only FILENAMES with matched result .
    -R stands for recursive and
    -l sands for "files with matches"
    Here grep -Rl searches the directory for the string "Arctic" and outputs filenames with matched results.
    can also be stacked like -Rli, to make it not case sensitive.



sed
sed stands for "stream editor"
accepts stdin and modifies it based on an expression, before displaying it as output data.
It is similar to "find and replace"

    sed 's/snow/rain/' forests.txt
    s: stands for substitution, is always used when using sed for substitution
    snow - is the text to find
    rain - is the text to replace it with
    In this cas, sed searches and substitutes THE FIRST instance of the word snow and replaces it with "rain."

    sed 's/snow/rain/g'
    The above command uses g, meaning "global"
    Here the sed searches forests.txt for the word snow and replaces it with rain globally;
    Such that all instances are replaced.





# Environment
Each time we launch the terminal application, it creates a new session.
The session immediately loads settings and preferences that make up the command line environment.
We can configure the environment to support the commands and programs we create.
This enables us to customize greetings and command aliases, and create variables to share across commands and programs.
You can reference the filesystem for this lesson here.
    (https://s3.amazonaws.com/codecademy-content/courses/learn-the-command-line/img/LCL-fileTrees-04.png)



nano
nano is a command line text editor, works just like text editor
    Ctrl + O saves a file. ‘O’ stands for output.
    Ctrl + X exits the nano program. ‘X’ stands for exit.
    Ctrl + G opens a help menu.


bash profile
bash profile is the name of the file used to store environment settings.
When a session starts, it will load the contents of the bash profil before executing commands

    nano ~/.bash_profile
    opens up ~/.bash_profile in nano;
    The ~ represent's the user's home directory.
    The . indicates a hidden file.


alias
The alias command allows you to create keyboard shortcuts or "aliases" for commonly used commands.

    alias pd="pwd"
    alias hy="history"
    alias ll="ls -la"

    Here the alias pd='pwd' creates the alias pd for the pwd command.



export
Environment variables are variables that can be used across commands and programs and hold information about the environment.

    export USER="Wooyoung Joo"
    The line USER="Wooyoung  Joo" sets the environment variable USER to the name.
    Usually the USER varible is set to the name of the computer's owner.
    The line export makes the variable to be available to all child sessions initiated from the session you are in.
    THis is a way to make the variable persist across programs.

    you can now
        echo $USER
    to return the value of the variable.
    $ sign is always used when returning a variable's value.






environment variables
In addition to the user env variable - there are several others that are quite important / useful to know.


    HOME
    HOME is an environment variable that displays the path of the home directory.
    echo $HOME displays the path /home/ccuser as output on code academy;
    and on mine, it is /Users/Joo/

    export PS1=">>> "
    PS1 is a variable that defines the makeup and style of the command prompt.


    PATH
    PATH is an environment variable that stores a list of direcories separated by a colon.
    Each directory contains scripts for the command line to execute.
    The PATH variable simply lists which directories conain scripts.

    For example, many commands we've learned are scripts stored in the /bin directory.

    >>> cd ../../../usr
    to get ti it on my mac; you can ls all the things there - you'll find things like ls, pwd, sudo, su;



env
The env command stands for "environment", and returns a list of the environment variabls for the current user.

    env | grep PATH
    is a command that displays the value of a single environment variable.
    here the stdout of env is piped to the grep command, then the grep command searches for the value of the variable PATH and outputs it to the terminal.














