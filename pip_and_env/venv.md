
https://www.youtube.com/watch?v=Kg1Yvry_Ydk
tutorial link by Corey Schafer

why use a venv?
to control different versions / environments;
say you have a global environment, and you built stuff on Django 1.0; -->
Then you upgrade it to Django 2.0 and all your shit breaks now.
separate packages, versions from each other.



python -m venv project_env
    -m and specify which module like we did here -- in this case the venv module;
    Python will search for this module and use it;
    The venv module expects a environment name;
    This makes a new directory called project_env;

    YOu would usually name this project_env --> venv; or even .venv
    And #NEVER# put in stuff into the environments directory.

    The environment is something you want to be able to throw away and re-build;
    And you shouldn't really be commiting your virtual environment to source control;
    This is why gitignore files include venv;
    But you would commit requirements.txt - but not the environment itself;


python -m venv venv --system-site-packages;
    This will import all of your system packages, and put them into the venv;
    And any installation in the venv won't affect your system packages;




source project_env/bin/activate
    This activates the environment, and we will see the environment name in parentheses
    And we can also run

    which python
    This will point to the python in the environment.


If you need a old version of python (which in most cases you won't) then you probably can use virtualenv instead;

Now once this is installed - any new packages pip installed will be placed right in the venv;





====
You can also export or import other people's requirements with pip

pip freeze > requirements.txt


pip install -r requirements.txt
    to install a requirements.txt




====
deactivate
to deactivate lol;

rm -rf project_env -> to delete a environment;



