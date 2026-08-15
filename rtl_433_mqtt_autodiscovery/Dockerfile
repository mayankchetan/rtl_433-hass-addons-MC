ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base-python:3.12-alpine3.21
FROM ${BUILD_FROM} as builder

# rtl_433_mqtt_hass.py is vendored in this repo (merbanan/rtl_433 master
# + local rain_start mapping) — no network fetch at build time.

FROM ${BUILD_FROM}

COPY rtl_433_mqtt_hass.py .
COPY run.sh .

RUN \
    pip install \
        --no-cache-dir \
        --prefer-binary \
        paho-mqtt==1.6.1 \
    \
    && chmod a+x /run.sh

CMD [ "/run.sh" ]
