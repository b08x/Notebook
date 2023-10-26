https://docs.docker.com/compose/compose-file/compose-file-v3/#extension-fields

https://docs.docker.com/build/building/multi-stage/

```yaml
version: '3.9'
services:
  db:
    image: ankane/pgvector
    environment:
      POSTGRES_HOST_AUTH_METHOD: "trust"
      POSTGRES_DB: monadic
      POSTGRES_USER: postgres
    ports:
      - "5432:5432"
    restart: on-failure
  web:
    volumes:
      - ./log:/monadic/log
      - ./.env:/monadic/.env
    build: .
    ports:
      - "4567:4567"
    depends_on:
      - db
    restart: on-failure
    stdin_open: true
    tty: true
    command: ["sh", "/usr/local/bin/wait-for-postgres.sh", "db", "thin", "start", "-R", "config.ru", "-p", "4567"]
  proxy:
    build: ./proxy
    command: ["nginx-debug", "-g", "daemon off;"]
    volumes:
      - ./proxy/nginx.conf:/etc/nginx/nginx.conf
    ports:
      - "8082:80"
    restart: on-failure
    depends_on:
      - web

```