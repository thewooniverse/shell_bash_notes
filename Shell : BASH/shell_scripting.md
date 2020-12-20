


Any command you run in your terminal can be run in a Bash script to perform it.
When saving the script file, it is good to practice to place commonly used scripts in the ~/bin/ directory.
I've created and appended a new bin folder in my ~home directory; from .bash_profile which has been added to the $PATH variable.
Now I can run script.sh anytime, or add any other scripts in the same way;

You can set up aliases for your bash scripts within your .bashrc or .bash_profile file to allow calling your scripts without the full filename.

    alias saycolors="./saycolors.sh"

You can even add standard input arguments to your alias;

    alias saycolors='./saycolors.sh "green"'



#!/bin/bash
    The beginning of your script file should start with this on its own line.
    This is called a shebang and can be used for scritping in python as well;
    This tells the computer which type of interpreter to use for the script.

        #!/usr/bin/env python3





chmod +x script.sh
    This gives the script the 'execute' permission, to allow them to be run.
    Run this command in the terminal to chmod




variables in shell scripting
    varname="var_value"
    echo $varname
    This is the syntax for assigning and accessing the variable in shell.



conditionals in shell scripting
    if [ $index -lt 5 ]
    then
      echo $index
    else
      echo 5
    fi



comprison operators in shell scripting;
    Equal: -eq
    Not equal: -ne
    Less than or equal: -le
    Less than: -lt
    Greater than or equal: -ge
    Greater than: -gt
    Is null: -z


    ==
    !=
    if [ "$foo" == "$bar" ]
    These are common operators for comparing strings.
    When comparing strings, it is best practice to put the variable into quotes ("). This prevents errors if the variable is null or contains spaces.



loops in shell scripting;
    3 different types - for, while and until


    for word in $paragraph
    do
      echo $word
    done

    A for loop is used to iterate through a list and execute an action at each step.
    Note that word is being “defined” at the top of the for loop so there is no $ prepended. Remember that we prepend the $ when accessing the value of the variable.
    So, when accessing the variable within the do block, we use $word as usual.


    while [ $index -lt 5 ]
    do
      echo $index
      index=$((index + 1))
    done

    until [ $index -eq 5 ]
    do
      echo $index
      index=$((index + 1))
    done

    Within bash scripting until and while are very similar.
    while loops keep looping while the provided condition is true whereas until loops loop until the condition is true.
    Conditions are established the same way as they are within an if block, between square brackets.
    In this example we want to print the index variable as long as it is less than 5, we would use the following while loop;
    We achieve this with while and until as above.






arithmetic operators in shell;

    $((...))
    Note that arithmetic in bash scripting uses the $((...)) syntax and within the brackets the variable name is not prepended with a $.





inputs in shell;
To make bash scripts more useful, we need to be able to access data external to the bash script file itself.


    first way is to get input from the user through the read syntax.

        echo "Guess a number"
        read number
        echo "You guessed $number"


    Another way to access external data is to have the user add input arguments when they run your script.
    These arguments are entered after the script name and are separated by spaces.
    within the script, these are accessed using $1, $2, $3 etc.. (first argument here being "red")

    If your script needs to accept an indefinite number of input arguments, you can iterate over them using the "$@" syntax.
    For our saycolors example, we could print each color using the below.

        saycolors red green blue

        for color in "$@"
        do
          echo $color
        done



    Lastly, we can access external files to our script.
    You can assign a set of files to a variable name using standard bash pattern matching using regular expressions.
    For example, to get all files in a directory, you can use the * character:

        files=/some/directory/*

        for file in $files
        do
          echo $file
        done







#Other functions



head

    firstline=$(head -n 1 source/changelog.md)

    default is 10 lines, in this case we used -n 1 to define that we want 1 line from the head of changelog.md




accessing

    The syntax for accessing the value at index of an array foo is:
    ${foo[index]}











