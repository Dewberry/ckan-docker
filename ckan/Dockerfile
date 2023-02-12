# FROM ckan/ckan-base:dev-v2.10
FROM ckan/ckan-base:2.9.7

# Set up environment variables
ENV APP_DIR=/srv/app
ENV TZ=UTC
RUN echo ${TZ} > /etc/timezone

# Make sure both files are not exactly the same
RUN if ! [ /usr/share/zoneinfo/${TZ} -ef /etc/localtime ]; then \
        cp /usr/share/zoneinfo/${TZ} /etc/localtime ;\
    fi ;

### DCAT ###
RUN  pip3 install -e git+https://github.com/ckan/ckanext-dcat.git#egg=ckanext-dcat && \
     pip3 install -r ${APP_DIR}/src/ckanext-dcat/requirements.txt && \
     pip3 install -e git+https://github.com/ckan/ckanext-geoview.git#egg=ckanext-geoview

ADD prerun.py .
RUN python3 prerun.py

EXPOSE 5000