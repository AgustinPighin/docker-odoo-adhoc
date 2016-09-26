FROM adhoc/odoo-oca:9.0
MAINTAINER Juan Jose Scarafia <jjs@adhoc.com.ar>

USER root

# Get repositories & add files
WORKDIR ${RESOURCES}
COPY ./adhoc-sources.txt ./
RUN mkdir -p ${EXTRA_ADDONS}
RUN python get_addons.py ${EXTRA_ADDONS} --depth=1 --sources_file=adhoc-sources.txt
WORKDIR /

# para pyafipws
RUN pip install -r https://raw.githubusercontent.com/reingart/pyafipws/master/requirements.txt
RUN pip install git+https://github.com/reingart/pyafipws@master
RUN chmod 777 -R /usr/local/lib/python2.7/dist-packages/pyafipws/

USER odoo