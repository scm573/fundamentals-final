FROM postgres:9.6
COPY pg_hba.conf /usr/share/postgresql/9.6/
COPY postgresql.conf /usr/share/postgresql/9.6/
COPY *.sql /docker-entrypoint-initdb.d/
ENV  POSTGRES_USER=gordonuser
ENV  POSTGRES_DB=ddev
