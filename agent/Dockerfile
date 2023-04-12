FROM python:3.9.0b4-alpine3.12

COPY ./agent/requirements.txt .
COPY ./agent/SnmpTrapGen.exe ./root/SnmpTrapGen.exe
COPY ./agent/trapAgent.py ./bin/trapAgent.py
COPY ./agent/root /var/spool/cron/crontabs/root
COPY . .

RUN /usr/local/bin/python -m pip install --upgrade pip
RUN pip install -r requirements.txt

RUN chmod +x /bin/trapAgent.py
RUN chmod +x /root/SnmpTrapGen.exe

CMD crond -l 3 -f