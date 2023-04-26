# postgreSQL 서버 연결

## 1. postgreSQL 설정

- django에서 사용할 데이터베이스를 새로 만든다

 ```
create database django_test;
```



- 새롭게 만든, django_test 데이터베이스로 들어가서 새로운 유저를 만들고 몇가지 설정과 함께 권한을 부여


> 데이터베이스에 대한 설정
``` 
create user root with password 'password';

alter role root set client_encoding to 'utf-8';

alter role root set timezone to 'Asia/Seoul';

grant all privileges on database django_test to root;
```


2. django 설정


```
pip install --no-binary :all: psycopg2
```

- postgreSQL을 적용할 django 프로젝트로 들어가서 settings.py 파일을 연다.


- installed_apps 항목을 찾아서 만든 app을 추가



- DATABASES 항목
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'django_test',
        'USER': 'root',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```


- blog라고 새롭게 만든 app의 models.py 파일에 코드 작성
```
from django.db import models
 
# Create your models here.
class Post(models.Model):
    name = models.CharField(max_length = 20)
    content = models.TextField()
```

```
python manage.py makemigrations
```
```
python manage.py migrate
```
```
python manage.py runserver
```

- postgresql 터미널로 들어와서 아래 명령어를 입력하여 테이블 리스트를 확인


```
\dt 
```

> blog_post 테이블 : django 프로젝트를 통해서 만들게된 테이블
