FROM python:3.8

WORKDIR /usr/src/app
COPY main.py pip.txt ./
RUN pip install -r ./pip.txt

CMD [ "python", "./main.py" ]
