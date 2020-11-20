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
<br/>
