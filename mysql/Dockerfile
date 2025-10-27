FROM mysql:8.0.32

LABEL maintainer="Project Maintainer" \
      version="1.0" \
      description="MySQL Database for MotoPP Application"

ENV MYSQL_CHARSET=utf8mb4 \
    MYSQL_COLLATION=utf8mb4_unicode_ci \
    TZ=UTC

COPY ./database_motopp.sql /docker-entrypoint-initdb.d/

RUN chown -R mysql:mysql /docker-entrypoint-initdb.d/ \
    && chmod 644 /docker-entrypoint-initdb.d/*

RUN echo '\
[mysqld]\n\
character-set-server=utf8mb4\n\
collation-server=utf8mb4_unicode_ci\n\
default-authentication-plugin=mysql_native_password\n\
max_allowed_packet=128M\n\
explicit_defaults_for_timestamp=1\n\
' > /etc/mysql/conf.d/custom.cnf

HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD mysqladmin ping -h localhost -uroot || exit 1

EXPOSE 3306
