# admin

* admin 사이트 사용하기 위한 준비
* 서버주소:8000/admin



1. 슈퍼 유저 생성(관리자)

   `python manage.py createsuperuser`

```python
(venv) C:\Users\qkrtj\DataScience\web\first_django>python manage.py createsuperuser
Username (leave blank to use 'qkrtj'): root
Email address: root@mysite.com
Password:
Password (again):
This password is too short. It must contain at least 8 characters.
This password is too common.
This password is entirely numeric.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.

```



# 장고 프로젝트 생성 시 환경 설정

* 서버 종료 후 작업

* `config/settings.py`

  ```python
  from pathlib import Path # 경로 설정을 위한 모듈
  # 프로젝트 시작한 위치를 기본 dir로 설정함
  BASE_DIR = Path(__file__).resolve().parent.parent
  # (BASE_DIR/)polls/detail
  
  # 개발자 모드(True) / 운영모드(False)
  DEBUG = True
  
  # 가동할 서버의 ip 나열 (나열된 ip로 서버가 운영됨.)
  ALLOWED_HOSTS = [] # 기본 127.0.0.1로 운영
  # Ex. ALLOWED_HOSTS = ['localhost', '127.0.0.1', '192.168.56.101']
  ## 서버 주소로 localhost, 127.0.0.1, 192.168.56.101 을 사용할 수 있음
  ## ALLOWED_HOSTS = ['*'] -> 모든 ip로 서버 운영 가능
  
  
  # 프로젝트에 포함되는 모든 app은 아래에 등록되어 있어야 함.
  INSTALLED_APPS = [
      'django.contrib.admin',
      'django.contrib.auth',
      'django.contrib.contenttypes',
      'django.contrib.sessions',
      'django.contrib.messages',
      'django.contrib.staticfiles',
      'bookmark',
      'polls.apps.PollsConfig',
  ]
  
  # db 설정
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.sqlite3', # 변경하려는 db 엔진명 찾아서 기록
          'NAME': BASE_DIR / 'db.sqlite3', # 해당 dbms 파일 경로 및 이름
      }
  }
  
  
  # Time Zone 변경
  # TIME_ZONE = 'UTC'
  TIME_ZONE = 'Asia/Seoul'
  
  # 정적파일 경로 설정 (js, css, image 파일을 /static/에 둠)
  STATIC_URL = '/static/'
  # BASE_DIR 밑에 static 폴더 생성해야 함.
  ```

  