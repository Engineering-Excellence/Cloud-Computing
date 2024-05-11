FROM ubuntu:22.04

RUN apt update && apt install -y python3
COPY hello.py .

ENTRYPOINT ["python3", "hello.py"]
