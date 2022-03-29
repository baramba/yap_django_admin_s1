FROM python:3.8
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ARG WORKDIR=/home/app
ARG SRC_CODE_DIR=./app
ARG REQFILE=requirements.txt
ARG USER=app
ARG GROUP=apps

WORKDIR ${WORKDIR}

ENV PATH="${WORKDIR}/.local/bin:${PATH}"

RUN groupadd -r ${GROUP} && useradd --no-log-init -r -g ${GROUP} ${USER} &&  \
    mkdir ${WORKDIR}/static && chown -R ${USER}:${GROUP} ${WORKDIR} && \
    apt update && apt install --yes gettext
USER app
COPY --chown=${USER}:${GROUP} ${SRC_CODE_DIR}/${REQFILE} ./
RUN python -m pip install --upgrade pip && python -m pip install -r ./${REQFILE}
COPY --chown=${USER}:${GROUP} ${SRC_CODE_DIR} ./




