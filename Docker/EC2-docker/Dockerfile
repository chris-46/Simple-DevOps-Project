# Here, I utilize the tomcat image from tomcat hub to simplify starting up my tomcat container.
FROM tomcat:latest

# This address a 404 error known in certain tomcat versions detailed here: https://forums.docker.com/t/tomcat-give-error-404/95130
RUN mv /usr/local/tomcat/webapps /usr/local/tomcat/webapps2
RUN mv /usr/local/tomcat/webapps.dist /usr/local/tomcat/webapps
ADD webapp.war /usral/tomcat/webapps/

# Allow connecting to tomcat from external ip, solving a 403 error when trying to access the tomcat webapps menu
COPY manager/context.xml $CATALINA_HOME/webapps/manager/META-INF/context.xml
COPY host-manager/context.xml $CATALINA_HOME/webapps/host-manager/META-INF/context.xml

EXPOSE 8080
CMD ["catalina.sh", "run"]
