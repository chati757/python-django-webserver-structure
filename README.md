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
    
    install django
        pip install Django==1.11.5 (or other version)
    
    create src folder
        mkdir src
    
    start project
        ..\<src>\django-admin startproject <project name> . (don't use '-' in project name)

    start server 
        cd ..\<src>\<project name> python3 manage.py runserver
        *incase custom port for startserver
            ..\<src>\<project name> python3 manage.py runserver <portnumber>

        open webbrowser > goto localhost:8000
        
## build structure
### build home_page
#### create views file
    
    ..\<src>\<project name>views.py
        from django.http import HttpResponse #allow to use HttpResponse
        from django.shortcuts import render #allow to use html template

        def home_page(req):
            context = {
                "title":"hello world context"
            }
            eturn render(req,"home_page.html",context)

#### edit urls.py for routing

    from django.conf.urls import url
    from django.contrib import admin

    from .views import home_page

    urlpatterns = [
        url(r'^$', home_page),#<-----add this line
        url(r'^admin/', admin.site.urls),
    ]

#### using template 

    create template folders
        ..\<src>\templates

    ..\<src>\templates\home_page.html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="utf-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <!-- The above 3 meta tags *must* come first in the head; any other head content must come *after* these tags -->
            <title>Bootstrap 101 Template</title>

            <!-- Bootstrap -->
            <link href="css/bootstrap.min.css" rel="stylesheet">

            <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
            <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
            <!--[if lt IE 9]>
            <script src="https://oss.maxcdn.com/html5shiv/3.7.3/html5shiv.min.js"></script>
            <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
            <![endif]-->
        </head>
        <body>
            <div class='text-center'>
                <h1>{{title}}</h1>
                <h1>Hello, world! template using</h1>
            </div>

            <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
            <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
            <!-- Include all compiled plugins (below), or include individual files as needed -->
            <script src="js/bootstrap.min.js"></script>
        </body>
        </html>

    set default template directory
    ..\<src>\<project name>\setting.py (edit)
        TEMPLATES = [
            {
                'BACKEND': 'django.template.backends.django.DjangoTemplates',
                'DIRS': [os.path.join(BASE_DIR, 'templates')], #<-----edit this line
                'APP_DIRS': True,
                'OPTIONS': {
                    'context_processors': [
                        'django.template.context_processors.debug',
                        'django.template.context_processors.request',
                        'django.contrib.auth.context_processors.auth',
                        'django.contrib.messages.context_processors.messages',
                    ],
                },
            },
        ]