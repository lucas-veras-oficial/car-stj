FROM wso2/wso2mi:4.3.0

USER root

COPY ./tecnisys/UserSyncService_1.0.0.car $WSO2_SERVER_HOME/repository/deployment/server/carbonapps/
COPY ./mssql-jdbc-7.1.4.jre11-preview.jar $WSO2_SERVER_HOME/lib/

RUN chmod -R 755 $WSO2_SERVER_HOME/repository/deployment/server/carbonapps/ \
    && chmod -R 755 $WSO2_SERVER_HOME/lib/

RUN echo "\
[[custom_message_formatters]]\n\
content_type = \"application/scim+json\"\n\
class = \"org.wso2.micro.integrator.core.json.JsonStreamFormatter\"\n\
\n\
[[custom_message_builders]]\n\
content_type = \"application/scim+json\"\n\
class = \"org.wso2.micro.integrator.core.json.JsonStreamBuilder\"\n\
" >> $WSO2_SERVER_HOME/conf/deployment.toml

RUN chown -R wso2carbon:wso2 $WSO2_SERVER_HOME
