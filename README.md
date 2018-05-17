# python-django-webserver-structure
basic start django webserver with MTV(model template view)

## basic installation (window version)
### editor (recommend)

    https://code.visualstudio.com/

### install python3

    https://www.python.org/downloads/

    *install pip default

### set env

    goto python directory path (Ex:C:\Python3.6.5)
    change python.exe to python3 (prevent python2 path collision)

### update pip

    python3 -m pip install --upgrade pip

### install virtualenv

    check python pip
        pip -V (if that pip path from python3 is ok)

    pip virtualenv

## build project and using virtualenv to install django web framework

### Make virtualenv parent directory
    
    create project with virtulenv
        mkdir ..\<github project folder> or git clone <clone url>
        mkdir ..\<github project folder>\<project name folder>
        cd ..\<github project folder>
        ..\<github project folder>\virtulenv -p python3 <project name folder>
    
    create src folder
        mkdir src
    
    start project
        ..\<src>\django-admin startproject <project name> . (don't use '-' in project name)

    start server 
        cd ..\<src>\<project name> python3 manage.py runserver
        *incase custom port for startserver
            ..\<src>\<project name> python3 manage.py runserver <portnumber>

        open webbrowser > goto localhost:8000 
        
    