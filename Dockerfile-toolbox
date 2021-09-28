FROM python:3.7.0
RUN apt-get -y update && apt-get -y install \
    libpq-dev build-essential less postgresql-client \
    && pip install pgcli \
    && pip install okcli \
    && curl -fsSL https://code-server.dev/install.sh | sh -s -- --method standalone 

CMD ["/root/.local/lib/code-server-3.11.1/bin/code-server","--auth", "none", "--disable-telemetry", "--bind-addr", "0.0.0.0:8080"]
