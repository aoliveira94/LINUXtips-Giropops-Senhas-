FROM alpine:3.18 AS GIROPOPS_SENHA

LABEL STAGE="GIROPOPS_SENHA"

ARG DOCUMENT_ROOT=/giropops-senhas
ENV REDIS_HOST=redis-giropops

SHELL ["/bin/sh", "-eux", "-c"]

COPY . ${DOCUMENT_ROOT}
WORKDIR ${DOCUMENT_ROOT}

RUN \
    apk update \
    && apk add --no-cache \
    python3 \
    py3-pip \
    curl

RUN \
    pip3 install --no-cache-dir -r requirements.txt

EXPOSE 5000

ENTRYPOINT ["flask"]

CMD ["run", "--host=0.0.0.0"]

HEALTHCHECK --timeout=2s CMD curl localhost:5000 || exit 1