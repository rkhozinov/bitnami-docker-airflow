FROM bitnami/minideb-extras:stretch-r354
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    BITNAMI_PKG_EXTRA_DIRS="/opt/bitnami/airflow/dags" \
    HOME="/"

# Install required system packages and dependencies
RUN install_packages libbsd0 libbz2-1.0 libc6 libcomerr2 libedit2 libffi6 libgcc1 libgssapi-krb5-2 libicu57 libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 liblzma5 libmariadbclient18 libncurses5 libnss-wrapper libreadline7 libsasl2-2 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 libxml2 libxslt1.1 zlib1g
RUN bitnami-pkg install python-3.6.8-2 --checksum 2eb057ee7701667327f6bcc1fc8765abe5d9d003a64124e5f8505fa692e71eb8
RUN bitnami-pkg install postgresql-client-10.7.0-1 --checksum a351a3ea00d4443bdc6892e5f9d45aaf2fbbdf7c2aa40ab6cf423c78d535cca1
RUN bitnami-pkg unpack airflow-1.10.3-1 --checksum dc5698b27cb686f71dba2c06dd8bbfdc48734c3392243080487bcf87b41d8fc8

COPY rootfs /
ENV AIRFLOW_BASE_URl="" \
    AIRFLOW_DATABASE_HOST="postgresql" \
    AIRFLOW_DATABASE_NAME="bitnami_airflow" \
    AIRFLOW_DATABASE_PASSWORD="bitnami1" \
    AIRFLOW_DATABASE_PORT_NUMBER="5432" \
    AIRFLOW_DATABASE_USERNAME="bn_airflow" \
    AIRFLOW_DATABASE_USE_SSL="no" \
    AIRFLOW_EMAIL="user@example.com" \
    AIRFLOW_EXECUTOR="SequentialExecutor" \
    AIRFLOW_FERNET_KEY="" \
    AIRFLOW_FIRSTNAME="Firstname" \
    AIRFLOW_HOME="/opt/bitnami/airflow" \
    AIRFLOW_HOSTNAME_CALLABLE="" \
    AIRFLOW_LASTNAME="Lastname" \
    AIRFLOW_LOAD_EXAMPLES="yes" \
    AIRFLOW_PASSWORD="bitnami" \
    AIRFLOW_REDIS_USE_SSL="no" \
    AIRFLOW_USERNAME="user" \
    AIRFLOW_WEBSERVER_HOST="127.0.0.1" \
    AIRFLOW_WEBSERVER_PORT_NUMBER="8080" \
    BITNAMI_APP_NAME="airflow" \
    BITNAMI_IMAGE_VERSION="1.10.3-debian-9-r6" \
    LD_LIBRARY_PATH="/opt/bitnami/python/lib/:/opt/bitnami/airflow/venv/lib/python3.6/site-packages/numpy/.libs/:$LD_LIBRARY_PATH" \
    LD_PRELOAD="/usr/lib/libnss_wrapper.so" \
    LNAME="airflow" \
    NAMI_PREFIX="/.nami" \
    NSS_WRAPPER_GROUP="/opt/bitnami/airflow/nss_group" \
    NSS_WRAPPER_PASSWD="/opt/bitnami/airflow/nss_passwd" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/postgresql/bin:/opt/bitnami/airflow/bin:/opt/bitnami/airflow/venv/bin:$PATH" \
    REDIS_HOST="redis" \
    REDIS_PASSWORD="" \
    REDIS_PORT_NUMBER="6379" \
    REDIS_USER=""

EXPOSE 8080

USER 1001
ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "/run.sh" ]
