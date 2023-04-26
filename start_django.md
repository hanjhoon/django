# 1. Django 설치하기

https://docs.djangoproject.com/en/2.0/intro/install/

- python 버전 확인
```  python
python --version
```

- django 라이브러리 설치
``` pyton
pip install django
```

# 2. 장고 프로젝트 시작하기
- django 프로젝트 생성
``` python
django-admin startproject start_django
```

> ls 명령어를 통해 확인해보면 manage.py 파일과 start_django 폴더가 생긴것을 확인할 수 있다

- 서버를 돌려 정상적으로 프로젝트가 실행되는지 확인
``` python
python manage.py runserver
```

웹 브라우저의 주소창에 
> 127.0.0.1:8000 또는 localhost:8000 해당 주소를 입력
