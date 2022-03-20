FROM python:3
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ARG WORKDIR=/home/app
ARG REQFILE=requirements.txt
ARG USER=app
ARG GROUP=apps
# ARG DIRPATH=/home/babikhin/project/yandex/sprint2/nap/01_doker_compose/app

RUN groupadd -r ${GROUP} && useradd --no-log-init -r -g ${GROUP} ${USER}

WORKDIR ${WORKDIR}

COPY --chown=${USER}:${GROUP} ./app/${REQFILE} ./
COPY --chown=${USER}:${GROUP} ./app/02_movies_admin/ ./movies

# Consider adding this directory to PATH or, 
# if you prefer to suppress this warning, 
# use --no-warn-script-location.
ENV PATH="${WORKDIR}/.local/bin:${PATH}"

RUN chown -R ${USER}:${GROUP} ${WORKDIR}
# RUN apt update && apt install libpq-dev
USER app
RUN python3 -m venv ./venv
RUN . ./venv/bin/activate

RUN python -m pip install --upgrade pip && python -m pip install -r ./${REQFILE}
#RUN python3 ./movies/manage.py migrate
#COPY . $DIRPATH