# Meta-Search, a web application powered by Django.

## Live DEMO:
  http://zeyang.alwaysdata.net/metasearch

## Main features:
- Aggregated and non-aggregated search mode
- Client-side and server-side validation
- Query pre-processing
- Boolean operator support
- Optional cluster feature
  
## Installation:

1. Make sure the following software are installed in your system:
    - Python 2.7.x ( http://python.org/download/ )
    - Django 1.5.x ( https://www.djangoproject.com/download/ )

2. Install the following Python package:
    - requests 2.0.0 ( https://pypi.python.org/pypi/requests/2.0.0 )

3. Create a new Django project or choose from one of your existing Django projects, then unzip "metasearch" folder into that project's root folder.

4. Edit the following sector in `settings.py` of that project:
    - In `INSTALLED_APPS` append 'metasearch'

5. Edit `urls.py` of that project:
    - In `patterns()` append the following line:
        ```
        url(r'^metasearch/', include('metasearch.urls')),
        ```

## Getting it run:

* If you are using Django's own development server, just run `manage.py` of your project and locate `http://your-domain:port/metasearch/` in your browser.

* For Apache httpd server (only applicable for version 2.2.xx), in WSGI mode:
    1. Install `mod_wsgi` module for Apache. ( https://code.google.com/p/modwsgi/wiki/DownloadTheSoftware?tm=2 )
    2. Open `httpd.conf` in `your_apache_path/conf/`, and append the following lines at the end of file:
        ```
        #change the path into your actual path of mod_wsgi.so
        LoadModule wsgi_module /your_apache_path/modules/mod_wsgi.so

        #change the path into your project's path of /static/
        Alias /static/ your_project_path/static/

        #change the path into your project's path of /static/
        <Directory your_project_path/static/>
        Order deny,allow
        Allow from all
        </Directory>
        
        #change the path into your project's path of wsgi.py
        WSGIScriptAlias / your_project_path/your_app/wsgi.py

        #change the path into your project's path
        WSGIPythonPath your_project_path

        #change the path into the path that contains your wsgi.py
        <Directory your_project_path/your_app>
        <Files wsgi.py>
        Order deny,allow
        Allow from all
        </Files>
        </Directory>
        ```
    3. Run Apache and locate `http://your-domain:port/metasearch/` in your browser. 

## Contact me:
Zeyang Lin
zeyanglin2013@gmail.com
