FROM python:3
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ARG WORKDIR=/home/app
ARG SRC_CODE_DIR=/app
ARG REQFILE=requirements.txt
ARG USER=app
ARG GROUP=apps
# ARG DIRPATH=/home/babikhin/project/yandex/sprint2/nap/01_doker_compose/app

WORKDIR ${WORKDIR}

# Consider adding this directory to PATH or, 
# if you prefer to suppress this warning, use --no-warn-script-location.
ENV PATH="${WORKDIR}/.local/bin:${PATH}"
RUN groupadd -r ${GROUP} && useradd --no-log-init -r -g ${GROUP} ${USER}

# COPY --chown=${USER}:${GROUP} ./${SRC_CODE_DIR}/../${REQFILE} ./
COPY --chown=${USER}:${GROUP} ${SRC_CODE_DIR} ./
# COPY --chown=${USER}:${GROUP} ./docker-entrypoint.sh ./

RUN mkdir ${WORKDIR}/static && chown -R ${USER}:${GROUP} ${WORKDIR} && apt update && apt install --yes gettext
# apt install libpq-dev
USER app
# RUN python3 -m venv ./venv
# RUN . ./venv/bin/activate
RUN python -m pip install --upgrade pip && python -m pip install -r ./${REQFILE}




