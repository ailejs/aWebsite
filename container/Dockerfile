FROM python:3.9

WORKDIR /st-projecti

COPY requirements.txt .
COPY ./src ./src

RUN pip install -r requirements.txt

CMD ["python", "./src/main"]

