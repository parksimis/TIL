1. django 설치

   `pip install django`

   *  특정 버전 사용

     `pip install django == version_name`

   ```python
   (venv) C:\Users\qkrtj\DataScience\web\first_django>pip install django
   Collecting django
     Downloading Django-3.1.5-py3-none-any.whl (7.8 MB)
        |████████████████████████████████| 7.8 MB 2.2 MB/s
   Collecting asgiref<4,>=3.2.10
     Downloading asgiref-3.3.1-py3-none-any.whl (19 kB)
                                                                                    Collecting pytz
     Downloading pytz-2020.5-py2.py3-none-any.whl (510 kB)
        |████████████████████████████████| 510 kB 6.8 MB/s
   Collecting sqlparse>=0.2.2
     Downloading sqlparse-0.4.1-py3-none-any.whl (42 kB)
        |████████████████████████████████| 42 kB ...
   Installing collected packages: sqlparse, pytz, asgiref, django
   Successfully installed asgiref-3.3.1 django-3.1.5 pytz-2020.5 sqlparse-0.4.1
   
   ```

2. 프로젝트 시작(생성과 동시에 시작)

   `django-admin startproject <프로젝트 명> <프로젝트 시작위치>`

   * 위 명령어는 가상환경 안에서 작업되어야 함.

   * 대부분 프로젝트는 최상위폴더에서 생성(파이참프로젝트 폴더 내에 생성)

     * `django-admin startproject config .`

     ```python
     (venv) C:\Users\qkrtj\DataScience\web\first_django>django-admin startproject config .
         
     (venv) C:\Users\qkrtj\DataScience\web\first_django>dir
      C 드라이브의 볼륨에는 이름이 없습니다.
      볼륨 일련 번호: B41D-A093
     
      C:\Users\qkrtj\DataScience\web\first_django 디렉터리
     
     2021-01-28  오후 01:15    <DIR>          .
     2021-01-28  오후 01:15    <DIR>          ..
     2021-01-28  오후 01:14    <DIR>          .idea
     2021-01-28  오후 01:15    <DIR>          config
     2021-01-28  오후 01:15               684 manage.py
     2021-01-28  오전 11:40    <DIR>          venv
                    1개 파일                 684 바이트
                    5개 디렉터리  47,885,799,424 바이트 남음
     
     ```

3. 앱 시작

   `django-admin startapp <앱 이름>`

   * 의미 있는 이름으로 작성할 것

4. settings.py 파일을 열어서 app 등록해야 함.(프로젝트에게 등록)

   ```python
   # 프로젝트에 등록된 app
   # 자동으로 등록되어 있는 것들 밑에 추가
   INSTALLED_APPS = [
       'django.contrib.admin',
       'django.contrib.auth',
       'django.contrib.contenttypes',
       'django.contrib.sessions',
       'django.contrib.messages',
       'django.contrib.staticfiles',
       'bookmark', # 앱 등록 문법 (간단히 축약)
       'polls.apps.PollsConfig', # 앱 등록문법
   ]
   ```

   * 마지막 문단이어도 ','가 있어야 함.

5. migrate 

   * model과 관련된 기능을 추가시키는 작업
     * dbms의 구조를 변경하는 작업이 일어나면(모델링 - 테이블 생성/수정, 필드 수정) migrate 진행
     * 단, 생성 후 한 번은 `migrate`만 진행
     * model 변경하면(모델링) - `make migrations` 후에 `migrate` 명령 진행

   * `python manage.py migrate`

   ```python
   (venv) C:\Users\qkrtj\DataScience\web\first_django>python manage.py migrate
      
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
   (venv)
   ```

   

6. 서버구동 확인

   * `python manage.py runserver`

     ```python
     (venv) C:\Users\qkrtj\DataScience\web\first_django>python manage.py runserver
     Watching for file changes with StatReloader
     Performing system checks...
     
     System check identified no issues (0 silenced).
     January 28, 2021 - 13:42:12
     Django version 3.1.5, using settings 'config.settings'
     Starting development server at http://127.0.0.1:8000/
     Quit the server with CTRL-BREAK.
     [28/Jan/2021 13:42:16] "GET / HTTP/1.1" 200 16351
     [28/Jan/2021 13:42:17] "GET /static/admin/css/fonts.css HTTP/1.1" 200 423
     [28/Jan/2021 13:42:17] "GET /static/admin/fonts/Roboto-Bold-webfont.woff HTTP/1.1" 200 86184
     [28/Jan/2021 13:42:17] "GET /static/admin/fonts/Roboto-Regular-webfont.woff HTTP/1.1" 200 85876
     [28/Jan/2021 13:42:17] "GET /static/admin/fonts/Roboto-Light-webfont.woff HTTP/1.1" 200 85692
     Not Found: /favicon.ico
     [28/Jan/2021 13:42:17] "GET /favicon.ico HTTP/1.1" 404 1972
     ```
     
