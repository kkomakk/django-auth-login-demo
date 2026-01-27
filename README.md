# 🔐 Django Auth Login Demo

Django의 **내장 인증 모듈 (`django.contrib.auth`)**을 활용하여  
기본적인 **로그인 · 로그아웃 · 세션 기반 인증 흐름**을 구현하고 실습하는 예제 프로젝트입니다.

---

## 🎯 학습 목표

- `authenticate()`, `login()`, `logout()`의 동작 원리 이해
- **세션 기반 인증 흐름** 실습
- `@login_required` 데코레이터를 통한 접근 제어
- 템플릿에서 `{% csrf_token %}` 사용
- Django **Messages Framework** 연동 및 사용자 피드백 처리

---

## 🧩 요구 환경

- **Python** 3.8 이상  
- **Django** 4.x / 5.x (수업 환경에 맞춰 선택)
- 가상환경 사용 권장 (`venv`)

---

## ⚙️ 주요 기능

| 기능 | 설명 |
|----|----|
| 로그인 | `/login/` — 사용자 인증 처리 (POST) |
| 로그아웃 | `/logout/` — 세션 삭제 후 리다이렉트 |
| 인증 페이지 | `/home/` — `@login_required` 적용 |
| 관리자 | `/admin/` — 슈퍼유저로 데이터 확인 |

---

## 🗂 프로젝트 구조 (예시)

django-auth-login-demo/
├── manage.py
├── project_name/
│   ├── settings.py
│   ├── urls.py
│   └── ...
├── accounts/
│   ├── views.py
│   ├── urls.py
│   ├── templates/
│   │   └── accounts/
│   │       ├── login.html
│   │       └── home.html
│   └── ...
└── requirements.txt

---

## 🚀 설치 및 실행

1️⃣ 가상환경 생성 및 활성화
python -m venv venv
source venv/bin/activate      # macOS / Linux
venv\Scripts\activate       # Windows

2️⃣ Django 설치
pip install django

3️⃣ 마이그레이션 및 관리자 계정 생성
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser

4️⃣ 개발 서버 실행
python manage.py runserver
