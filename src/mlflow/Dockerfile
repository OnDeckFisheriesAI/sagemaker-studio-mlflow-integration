FROM python:3.9.0

RUN pip install \
    mlflow==2.5.0\
    boto3 \
    psycopg2==2.9.5

RUN mkdir /mlflow/

EXPOSE 5000

CMD mlflow server \
    --host 0.0.0.0 \
    --port 5000 \
    --default-artifact-root ${BUCKET} \
    --gunicorn-opts "--log-level debug --timeout 180 --workers=2 --threads=4 --worker-class=gthread" \
    --backend-store-uri postgresql+psycopg2://${USERNAME}:${PASSWORD}@${HOST}:${PORT}/${DATABASE}
