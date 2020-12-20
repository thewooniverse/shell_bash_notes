You can run pip from the command line;


pip help
pip help command
pip help search

    Pretty standard, lists all, and specify for help on specific commands.
    As well as their -options


pip search package
    pip search Pympler
    This finds and tells you about a package.


pip install package
pip uninstall package
    pip install package -U, upgrade

    pip install -r requirements.txt
    installs all requiremens in .txt file






pip list
    pip list --outdated or pip list -o
    shows all outdated packages;


pip freeze
    pip freeze > requirements.txt
    the freeze command outputs all packages and version number in a requirements format.





pip freeze --local | grep -v '^\-e' | cut -d = -f 1 | xargs -n1 pip install -U
    updating verything in local env;

