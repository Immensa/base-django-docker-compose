# Instalação

## 1º Para criar o ambiente virtual para o projeto

```shell
$ python3 -m venv env
$ source env/bin/activate

(env) gladson@linuxg:/mnt/hdextra/django_project$
```

## 2º Instalar os pacotes no ambiente virtual

```shell
$ pip3 install -r django/requirements.txt 
Collecting Django<4.0,>=3.0
  Downloading Django-3.1.4-py3-none-any.whl (7.8 MB)
     |████████████████████████████████| 7.8 MB 49 kB/s 
Collecting psycopg2-binary>=2.8
  Downloading psycopg2_binary-2.8.6-cp38-cp38-manylinux1_x86_64.whl (3.0 MB)
     |████████████████████████████████| 3.0 MB 1.8 MB/s 
Collecting ipython>=7.19.0
  Downloading ipython-7.19.0-py3-none-any.whl (784 kB)
     |████████████████████████████████| 784 kB 3.6 MB/s 
Collecting pytz
  Downloading pytz-2020.4-py2.py3-none-any.whl (509 kB)
     |████████████████████████████████| 509 kB 3.2 MB/s 
Collecting sqlparse>=0.2.2
  Downloading sqlparse-0.4.1-py3-none-any.whl (42 kB)
     |████████████████████████████████| 42 kB 197 kB/s 
Collecting asgiref<4,>=3.2.10
  Downloading asgiref-3.3.1-py3-none-any.whl (19 kB)
Collecting pygments
  Downloading Pygments-2.7.3-py3-none-any.whl (950 kB)
     |████████████████████████████████| 950 kB 2.9 MB/s 
Collecting decorator
  Downloading decorator-4.4.2-py2.py3-none-any.whl (9.2 kB)
Collecting traitlets>=4.2
  Downloading traitlets-5.0.5-py3-none-any.whl (100 kB)
     |████████████████████████████████| 100 kB 1.9 MB/s 
Collecting pexpect>4.3; sys_platform != "win32"
  Downloading pexpect-4.8.0-py2.py3-none-any.whl (59 kB)
     |████████████████████████████████| 59 kB 3.1 MB/s 
Collecting backcall
  Downloading backcall-0.2.0-py2.py3-none-any.whl (11 kB)
Collecting pickleshare
  Downloading pickleshare-0.7.5-py2.py3-none-any.whl (6.9 kB)
Collecting prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0
  Downloading prompt_toolkit-3.0.8-py3-none-any.whl (355 kB)
     |████████████████████████████████| 355 kB 3.4 MB/s 
Requirement already satisfied: setuptools>=18.5 in ./env/lib/python3.8/site-packages (from ipython>=7.19.0->-r django/requirements.txt (line 3)) (44.0.0)
Collecting jedi>=0.10
  Downloading jedi-0.17.2-py2.py3-none-any.whl (1.4 MB)
     |████████████████████████████████| 1.4 MB 3.5 MB/s 
Collecting ipython-genutils
  Downloading ipython_genutils-0.2.0-py2.py3-none-any.whl (26 kB)
Collecting ptyprocess>=0.5
  Downloading ptyprocess-0.6.0-py2.py3-none-any.whl (39 kB)
Collecting wcwidth
  Downloading wcwidth-0.2.5-py2.py3-none-any.whl (30 kB)
Collecting parso<0.8.0,>=0.7.0
  Downloading parso-0.7.1-py2.py3-none-any.whl (109 kB)
     |████████████████████████████████| 109 kB 3.7 MB/s 
Installing collected packages: pytz, sqlparse, asgiref, Django, psycopg2-binary, pygments, decorator, ipython-genutils, traitlets, ptyprocess, pexpect, backcall, pickleshare, wcwidth, prompt-toolkit, parso, jedi, ipython
Successfully installed Django-3.1.4 asgiref-3.3.1 backcall-0.2.0 decorator-4.4.2 ipython-7.19.0 ipython-genutils-0.2.0 jedi-0.17.2 parso-0.7.1 pexpect-4.8.0 pickleshare-0.7.5 prompt-toolkit-3.0.8 psycopg2-binary-2.8.6 ptyprocess-0.6.0 pygments-2.7.3 pytz-2020.4 sqlparse-0.4.1 traitlets-5.0.5 wcwidth-0.2.5
```

## 3º Criar o projeto Django

> Caso queira criar o app, ele e a partir do camando "cd src"

```shell
$ mkdir src
$ django-admin startproject core src
$ cd src
$ python3 manage.py startapp app
```

## 4º Instalar o Docker e Docker-Compose (Linux)

```shell
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
OK
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
$ sudo apt update
$ apt-cache policy docker-ce
docker-ce:
  Instalado: (nenhum)
  Candidato: 5:20.10.0~3-0~ubuntu-focal
  Tabela de versão:
     5:20.10.0~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
     5:19.03.14~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
     5:19.03.13~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
     5:19.03.12~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
     5:19.03.11~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
     5:19.03.10~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
     5:19.03.9~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
$ sudo apt install docker-ce
$ sudo usermod -aG docker ${USER}
$ su - ${USER}
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
$ sudo groupadd docker-compose
$ sudo usermod -aG docker-compose ${USER}
$ docker-compose --version

docker-compose version 1.27.4, build 40524192
```

## 5º Rodar o projeto com o Docker-Compose

```shell
$ docker-compose up --build
Creating network "django_project_default" with the default driver
Creating volume "django_project_pgdata" with default driver
Successfully built 96bb3111c79d
Successfully tagged django_project_django:latest
Creating app-pgdb    ... done
Creating app-pgadmin ... done
Creating app-server  ... done
Attaching to app-pgdb, app-pgadmin, app-server
```

## 6º Comandos basicos para o projeto Django

> Valeu meu caro... Espero que te ajude ai...

```shell
$ ./console python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
```

## 7º Acessar páginas (localhost)

[Django](http://localhost:8000/)
[PgAdmin](http://localhost:5050/login?next=%2F)

### Problemas

#### Pacote Python venv - não encontrado

```shell
$ python3 -m venv env
The virtual environment was not created successfully because ensurepip is not
available.  On Debian/Ubuntu systems, you need to install the python3-venv
package using the following command.

    apt-get install python3-venv

You may need to use sudo with that command.  After installing the python3-venv
package, recreate your virtual environment.
```

#### Solução

```shell
$ sudo apt-get install python3-venv
```

#### Obs.

> Caso ocorra do executador "./console" aparecer permissão negada e so reiniciar o computador.