services:
  api:
    build: ./api
    ports:
      - "5000:5000"
    depends_on:
      - db
  db:
    build: ./db
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    ports:
      - "5432:5432"
    volumes:
      - db-data:/var/lib/postgresql
  web:
    build: ./web
    ports:
      - "3000:3000"
    depends_on:
      - api
volumes:
  db-data:
