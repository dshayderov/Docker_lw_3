FROM python:3.10-slim as builder

WORKDIR /usr/src/app

RUN pip install numpy
COPY ./my-app /usr/src/app
COPY ./requirements.txt /usr/src/app

FROM python:3.10-slim as runner

WORKDIR /usr/src/app

ENV DATABASE_URL postgres://user:password@localhost:5432/database

COPY --from=builder /usr/src/app/. .

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 5000

CMD [ "python", "app.py" ]

