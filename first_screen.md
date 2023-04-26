# django 첫 화면 만들기
## 1. App 만들기
- blog app을 만들기
```
python manage.py startapp blog
```
> start_django 폴더는 프로젝트의 기본 폴더 blog라는 app이 존재, start_django 폴더는 프로젝트 전체에 대한 설정 파일들이 담겨 있다


## 2. 첫번째 화면 만들기


- url지정
> start_django > start_django > urls.py 

```
from django.contrib import admin
from django.urls import path, include
 
urlpatterns = [
    path('', include('blog.urls')),
    path('admin/', admin.site.urls),
]
```
> include라는 함수를 추가로 import 
> path함수를 활용하여 첫 화면, 아무것도 입력되지 않은 url에서는 blog의 urls를 참고
 blog라는 폴더안에 urls.py 이라는 파일을 새로 생성

```
from django.urls import path
from . import views
 
urlpatterns = [
    path('', views.index),
]
```

> blog에서는 존재하지 않은 admin관련 import를 삭제
> views 파일을 import 하였고, url패턴에서 아무것도 입력되지 않은 주소에 대해서 views의 index를 참고
> blog 폴더에 있는 views.py 파일을 열어 코드를 작성

```
from django.shortcuts import render
from django.http import HttpResponse
 
# Create your views here.
def index(request):
    return HttpResponse("Main Screen!!!")
```

> index라는 함수를 만들었고 HttpResponse함수를 통한 반환
> start_django 폴더에 위치하게 한 다음,
```
python manage.py runserver
```
> localhost:8000 으로 접속
