FROM python:3.4-alpine
ADD . /code
WORKDIR /code
RUN pip install -r requirements.txt
RUN pip install -U flask-cors
CMD ["python", "webapp.py"]
