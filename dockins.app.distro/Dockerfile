FROM alpine

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# set root password
RUN echo 'root:password123' | chpasswd

# install necessary packages
RUN apk add --update wget openjdk7-jre

# Dowload Liferay Portal 6.2.x Enterprise Edition
RUN wget -O apache-tomcat-7.0.63.tar.gz http://apache.mesi.com.ar/tomcat/tomcat-7/v7.0.63/bin/apache-tomcat-7.0.63.tar.gz

# Unzip the Portal Tomcat Bundle
RUN tar -zxvf apache-tomcat-7.0.63.tar.gz

# Add applications to the webapps directory
ADD target/dockins.tomcat7-apps/*.war apache-tomcat-7.0.63/webapps

# Remove the bundle
RUN rm apache-tomcat-7.0.63.tar.gz

# Tomcat setenv.sh
VOLUME ["/apache-tomcat-7.0.63/bin/setenv.sh"]

WORKDIR /apache-tomcat-7.0.63

# Expose the ports ssh | HTTP
EXPOSE 22 8080 

# Start Liferay
ENTRYPOINT ["bin/catalina.sh"]
CMD ["run"]

