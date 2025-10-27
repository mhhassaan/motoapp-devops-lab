FROM python:3.9-slim-bullseye

LABEL maintainer="Project Maintainer" \
      version="1.0" \
      description="MotoPP Flask Application"

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    FLASK_APP=motopp \
    FLASK_RUN_HOST=0.0.0.0 \
    FLASK_RUN_PORT=5000 \
    ENV=prod

WORKDIR /app

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends \
        gcc \
        curl \
    && rm -rf /var/lib/apt/lists/* \
    && pip install --no-cache-dir --upgrade pip

RUN useradd -m -r appuser \
    && chown -R appuser:appuser /app

COPY --chown=appuser:appuser requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt \
    && rm -rf ~/.cache/pip/*

COPY --chown=appuser:appuser . /app/motopp

RUN if [ -f /app/motopp/run.sh ]; then \
        sed -i 's/\r$//' /app/motopp/run.sh \
        && chmod +x /app/motopp/run.sh; \
    fi

USER appuser

EXPOSE 5000

HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD curl --fail http://localhost:5000/ || exit 1

CMD [ "sh", "-c", "[ -x /app/motopp/run.sh ] && /app/motopp/run.sh || flask run" ]
