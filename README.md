# Django를 이용한 Web 프로젝트 만들기

> 이곳에서는 기본적으로 Django에 대한 내용을 기술할 예정이지만, Python에 대한 내용되 간단히 언급하겠다.

<br/>

### 기본적인 소프트웨어 
* conda 4.8.4
* python 3.8.5
* django 3.1.3
* mysqlclient 2.0.1

<br/><br/>

## Django 프로젝트 생성
<br/>

### CONDA 환경 생성 및 관련 프로그램 설치
<br/>

#### 환경 생성 및 환경 진입
<pre>$ conda create -n {env-name} [python={version}]                             #1
$ conda activate {env-name}
({env-name}) $                                                              #2</pre>
> #1: <br/>
> <strong>{env-name}</strong>은 생성할 환경의 이름이며, <strong>python={version}</strong>은 옵션으로 해당 환경에서 사용할 python 버전을 지정한다.  생략하면 CONDA에서 가장 안정적이라고 생각하는 버전을 설치해 주는데, '20년11월 기준으로 3.6.9가 설치된다. <br/>
> #2: <br/>
> 프롬프트가 변경된다.
<br/>

#### 관련 프로그램 설치
<pre>({env-name}) $ pip list
({env-name}) $ python -m pip install --upgrade pip                          #1
({env-name}) $ python -m pip install --upgrade setuptools                   #2
({env-name}) $ pip install {install-pkg-name ...}                           #3 </pre>
> #1/#2: <br/>
> 옵션으로 버전이 낮을 때 강제적으로 기본 패키지인 pip와 setuptools를 업그레이드를 실행한다. <br/>
> #3: <br/>
> 원하는 패키지를 설치한다. 여기서는 django, mysqlclient를 설치한다.
<br/>

#### 전체 소스
<pre>$ conda create -n django python=3.8
$ conda activate django
(django) $ pip list
(django) $ python --version
(django) $ pip install django mysqlclient</pre>

<br/>

### Django 프로젝트 생성
<br/>

#### 생성
<pre>(django) $ django-admin startproject {project-name}</pre>
> {project-name}은 임으로 작성해도 되지만, django 특유의 tree 구조상 <strong>main, manager</strong>로 설정한다. <br/>
###### 작성 예
<pre>(django) $ django-admin startproject MyBlog
(django) $ tree MyBlog
MyBlog                                                                       #1
├── manage.py
└── MyBlog                                                                   #2
    ├── __init__.py
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py </pre>
> #1은 이름을 변경해도 아무 상관없지만, #2를 변경하면 수정할 부분이 너무 많기 때문에 가급적 수정하지 않는다.
<br/>
<pre>(django) $ django-admin startproject main
(django) $ mv main MyBlog
(django) $ tree MyBlog
MyBlog
├── manage.py
└── main
    ├── __init__.py
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py </pre>

> 위와 같은 트리 구조를 가지고 프로젝트를 수행하고 싶기 때문이다.

<br/><br/>

## 환경 설정
<br/>

> **주요 파일들:** <br/>
> * settings.py - 해당 장고 프로젝트의 여러가지 설정을 정의한 파일(아래 내용은 설정할 내용이 많아서 별도로 빼둔 파일들이다.)
> * urls.py - 장고 프로젝트에서 관리하는 URL을 정의한 파일
> * wsgi.py - Web Server Gateway Interface(웹표준 서비스 인터페이스) 설정 파일, Django와 WAS를 연결하기 위한 설정들이 들어감
> * asgi.py - Asynchronous Server Gateway Interface(비동기 웹서비스 및 애플리케이션 인터페이스) 설정 파일

<br/>

### settings.py
> 다양한 설정이 있는데 프로젝트 구성 후 사용하는 순서대로 작성하겠다.

<br/>

##### DATABASES
###### MySql(or MariaDB)
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'django_apps',
        'USER': 'freeman',
        'PASSWORD': 'free4567',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```    
###### SQLite
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```
<br/>

##### 지역화
```python
LANGUAGE_CODE = 'ko-kr'
TIME_ZONE = 'Asia/Seoul'
USE_I18N = True
USE_L10N = True
USE_TZ = False
```

<br/>

### urls.py
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('', include('common.urls')),
    path('admin/', admin.site.urls),
]
```

<br/><br/>

## 기타
<br/>

### 프로젝트 DB 적용
> manage.py가 있는 폴더에서 실행한다.
<br/>

<pre>(django) $ python manage.py makemigrations {app-name}
(django) $ python manage.py migrate</pre>
<br/>

### Admin Web 관리자 생성
<pre>(django) $ python manage.py createsuperuser</pre>
<br/>

### Apps 생성
<pre>(django) $ python manage.py startapp common</pre>
<br/>

### Web server 실행
<pre>(django) $ python manage.py runserver {port}</pre>
> {port}의 기본값은 8000임
<pre> http://localhost:8000/admin </pre>

