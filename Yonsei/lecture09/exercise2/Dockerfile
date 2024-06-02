# 베이스 이미지
FROM nginx:latest

# 소프트웨어 패키지 설치
RUN apt update && apt install -y python3-full

# 작업 디렉토리 지정
WORKDIR /flaskapp

# 가상 환경 생성
RUN python3 -m venv /flaskapp/venv

# 패키지 설치 목록 복사
COPY requirements.txt ./

# 패키지 설치
RUN /flaskapp/venv/bin/pip install -r requirements.txt

# 응용 스크립트 복사
COPY app.py ./

# 웹 서버 설정 파일 복사
COPY site.conf /etc/nginx/sites-available/flaskapp.conf

# 심볼릭 링크를 생성
RUN ln -s /etc/nginx/sites-available/flaskapp.conf /etc/nginx/conf.d

# (이전의) 디폴트 웹 서버 설정이 적용되지 않도록 설정
RUN mv /etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf.bak

# 서버 구동 스크립트 복사 및 실행
COPY start.sh ./
RUN chmod +x /flaskapp/start.sh
ENTRYPOINT ["/bin/bash", "/flaskapp/start.sh"]

