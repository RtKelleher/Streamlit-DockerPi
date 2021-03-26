FROM python:3.9.2 AS base
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    POETRY_HOME="/opt/poetry" \
    POETRY_VIRTUALENVS_IN_PROJECT=true \
    POETRY_NO_INTERACTION=1
ENV PATH="/opt/poetry/bin:/opt/app/.venv/bin:$PATH"

# Stage/Builder
FROM base AS stage
WORKDIR /opt/app
RUN curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py \
    | python && cd /usr/local/bin && \
    ln -s POETRY_HOME/bin/poetry
COPY ./app/pyproject.toml ./app/poetry.lock* ./

# Install Poetry from Curl, If desired set DEV to true for Dev packages
ARG INSTALL_DEV=false
RUN bash -c "if [ $INSTALL_DEV == 'true' ] ; then poetry install --no-root ; else poetry install --no-root --no-dev --ansi; fi"

# Production
FROM base AS prod
WORKDIR /app
COPY --from=stage $POETRY_HOME $POETRY_HOME
COPY --from=stage /opt/app /opt/app
COPY --from=stage /opt/poetry /opt/poetry