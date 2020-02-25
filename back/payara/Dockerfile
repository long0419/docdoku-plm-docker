# DocDoku, Professional Open Source
# Copyright 2006 - 2017 DocDoku SARL
#
# This file is part of DocDokuPLM.
#
# DocDokuPLM is free software: you can redistribute it and/or modify
# it under the terms of the GNU Affero General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# DocDokuPLM is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Affero General Public License for more details.
#
# You should have received a copy of the GNU Affero General Public License
# along with DocDokuPLM.  If not, see <http://www.gnu.org/licenses/>.
#
## DocDokuPLM server docker image dependencies
#

FROM payara/server-full:5.194

ENV POSTGRES_CONNECTOR_URL https://jdbc.postgresql.org/download/postgresql-42.2.5.jar

USER root

RUN export DEBIAN_FRONTEND=noninteractive; \
    export DEBCONF_NONINTERACTIVE_SEEN=true; \
    echo 'tzdata tzdata/Areas select Etc' | debconf-set-selections; \
    echo 'tzdata tzdata/Zones/Etc select UTC' | debconf-set-selections;

RUN \
 apt-get update -qqy && apt-get install -qqy --no-install-recommends \
 tzdata \
 freecad  \
 assimp-utils \
 libreoffice  \
 libreoffice-writer  \
 ure  \
 libreoffice-java-common  \
 libreoffice-core \
 libreoffice-common \
 fonts-opensymbol \
 hyphen-fr \
 hyphen-de \
 hyphen-en-us \
 hyphen-it \
 hyphen-ru \
 fonts-dejavu \
 fonts-dejavu-core \
 fonts-dejavu-extra \
 fonts-noto \
 fonts-dustin \
 fonts-f500 \
 fonts-fanwood  \
 fonts-freefont-ttf \
 fonts-liberation \
 fonts-lmodern  \
 fonts-lyx  \
 fonts-sil-gentium \
 fonts-texgyre  \
 fonts-tlwg-purisa

RUN \
 mkdir -p /var/lib/docdoku/vault && \
 mkdir -p /var/lib/docdoku/conversions && \
 chown -R payara:payara /var/lib/docdoku

RUN \
 wget --quiet -O /opt/payara/appserver/glassfish/domains/production/lib/postgresql-42.2.5.jar ${POSTGRES_CONNECTOR_URL} && \
 mkdir -p /opt/payara/appserver/glassfish/domains/production/lib/
RUN \
 apt-get clean && \
 rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN \
 chown -R payara:payara /opt

USER payara

