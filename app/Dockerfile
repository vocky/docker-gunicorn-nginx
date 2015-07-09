FROM ubuntu:14.04
MAINTAINER vocky
RUN apt-get update && apt-get install -y \
    scons \
    g++ \
    python-setuptools \
    python-pip \
    python-dev

RUN pip install gunicorn gevent

ADD timo /tmp/timo
WORKDIR /tmp/timo

RUN scons && scons install && ldconfig

ADD timorest /tmp/timorest
WORKDIR /tmp/timorest
RUN python setup.py install

WORKDIR /
RUN mkdir -p /usr/share/mendola
ENV TIMO_APPLICATION_DATA /tmp/timorest/tests/forcpp.dat
ENV TIMO_LIB_DATA_PATH /usr/share/mendola/timo_application_data.dat

ADD download.sh /tmp/download.sh

RUN mkdir -p /var/log/gunicorn

EXPOSE 5000
CMD bash /tmp/download.sh && \
    echo "starting gunicron with ${WEB_CONCURRENCY:=$(nproc)} procs" && \
    gunicorn \
    -k gevent \
    -b 0.0.0.0:5000 \
    -t 60 \
    --access-logfile=/var/log/gunicorn/access.log \
    --error-logfile=/var/log/gunicorn/error.log \
    'timorest:create_app()'
