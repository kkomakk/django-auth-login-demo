설명: Django의 내장 인증 모듈(django.contrib.auth)을 이용해 기본적인 로그인·로그아웃 흐름을 구현하고 실습하는 예제 프로젝트입니다. 수업/과제 제출용으로 로그인, 로그아웃, 인증 필요 페이지(@login_required), 메시지 표시, 관리자 확인 등을 포함합니다.

학습 목표

authenticate(), login(), logout()의 동작 원리 이해

세션 기반 인증 흐름 실습

@login_required로 접근 제어 구현

템플릿에서 {% csrf_token %} 사용 및 Django 메시지 프레임워크 연동

요구 환경

Python 3.8+

Django 4.x / 5.x (수업 환경에 맞춰 설정)

가상환경 사용 권장 (venv)

주요 기능

로그인 페이지 (/login/) — 사용자 인증 처리 (POST)

로그아웃 (/logout/) — 세션 삭제 및 리다이렉트 (권장: POST)

로그인 필요 페이지 (/home/) — @login_required 적용

관리자 페이지 (/admin/) — 슈퍼유저로 작성 데이터 확인

프로젝트 구조 (예시)
django-auth-login-demo/
├── manage.py
├── project_name/
│   ├── settings.py
│   ├── urls.py
│   └── ...
├── accounts/
│   ├── views.py
│   ├── urls.py
│   ├── templates/accounts/
│   │   ├── login.html
│   │   └── home.html
│   └── ...
└── requirements.txt

설치 및 실행
# 가상환경 생성/활성화
python -m venv venv
source venv/bin/activate     # mac/linux
# venv\Scripts\activate      # Windows

# 의존성 설치
pip install django

# 마이그레이션 및 슈퍼유저 생성
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser

# 로컬 서버 실행
python manage.py runserver


브라우저 접속:

로그인: http://127.0.0.1:8000/login/

홈(인증 필요): http://127.0.0.1:8000/home/

로그아웃: http://127.0.0.1:8000/logout/

관리자: http://127.0.0.1:8000/admin/

핵심 코드(요약)

로그인 처리: authenticate(request, username, password) → login(request, user)

로그아웃 처리: logout(request)

접근 제어: @login_required

템플릿: 모든 POST 폼에 {% csrf_token %} 포함

피드백: Django messages 프레임워크 사용

보안 권장사항

로그아웃은 가능한 POST로 처리 (CSRF 보호를 위해)

실제 서비스에서는 HTTPS, 세션 만료, 비밀번호 정책, 계정 잠금 등 추가 보안 적용

@csrf_exempt 사용 금지(특정 테스트 상황 제외)

과제 제출 체크리스트

 로그인 화면 캡처 (login 폼)

 로그인 성공(홈) 화면 캡처

 로그아웃 후 화면 캡처

 GitHub 레포지토리(코드) 링크 제출

참고자료

Django Authentication: https://docs.djangoproject.com/en/stable/topics/auth/

Django CSRF: https://docs.djangoproject.com/en/stable/ref/csrf/

Django Messages: https://docs.djangoproject.com/en/stable/ref/contrib/messages/
