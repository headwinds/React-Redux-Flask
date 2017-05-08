FROM python:3.4-alpine

LABEL name "blackgold"
ADD . .
WORKDIR .
RUN pip install Flask

EXPOSE 5000

CMD ["python", "app.py"]