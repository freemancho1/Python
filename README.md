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
$ conda activate {env-name}                                                 #2</pre>
> #1: <br/>
> **{env-name}**은 생성할 환경의 이름이며, **python={version}**은 옵션으로 해당 환경에서 사용할 python 버전을 지정한다.  생략하면 CONDA에서 가장 안정적이라고 생각하는 버전을 설치해 주는데, '20년11월 기준으로 3.6.9가 설치된다.

#### 관련 프로그램 설치
<pre>$ pip list</pre>

