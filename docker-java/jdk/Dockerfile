FROM bond1982/alpine-glibc

MAINTAINER Shivanand Mutnale <shivanand.mutnale@gmail.com>

#Java Version
ENV JAVA_VERSION_MAJOR 8
ENV JAVA_VERSION_MINOR 171
ENV JAVA_VERSION_BUILD 11
ENV JAVA_PACKAG jdk

ENV JAVA_SHA256_SUM b6dd2837efaaec4109b36cfbb94a774db100029f98b0d78be68c27bec0275982
ENV JAVA_URL_ELEMENT 512cd62ec5174c3487ac17c61aaa89e8

#Download and unarchive Java

RUN apk add --update curl && \
	mkdir -p /opt && \
	curl -jkLH "Cookie: oraclelicense=accept-securebackup-cookie" -o java.tar.gz\
	http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-b${JAVA_VERSION_BUILD}/${JAVA_URL_ELEMENT}/${JAVA_PACKAG}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz &&\
	echo "$JAVA_SHA256_SUM java.tar.gz" | sha256sum -c - && \
	gunzip -c java.tar.gz | tar -xf - -C /opt && rm -f java.tar.gz &&\
	ln -s /opt/jdk1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} /opt/jdk &&\
	rm -rf /opt/jdk/*src.zip \
		/opt/jdk/lib/missioncontrol \
		/opt/jdk/lib/visualvm \
		/opt/jdk/lib/*javafx*\
		/opt/jdk/jre/lib/plugin.jar\
		/opt/jdk/jre/lib/ext/jfxrt.jar\
		/opt/jdk/jre/bin/javaws \
         	/opt/jdk/jre/lib/javaws.jar \
        	/opt/jdk/jre/lib/desktop \
	        /opt/jdk/jre/plugin \
	        /opt/jdk/jre/lib/deploy* \
        	/opt/jdk/jre/lib/*javafx* \
         	/opt/jdk/jre/lib/*jfx* \
	        /opt/jdk/jre/lib/amd64/libdecora_sse.so \
         	/opt/jdk/jre/lib/amd64/libprism_*.so \
	        /opt/jdk/jre/lib/amd64/libfxplugins.so \
	        /opt/jdk/jre/lib/amd64/libglass.so \
        	 /opt/jdk/jre/lib/amd64/libgstreamer-lite.so \
        	 /opt/jdk/jre/lib/amd64/libjavafx*.so \
        	 /opt/jdk/jre/lib/amd64/libjfx*.so &&\
	  apk del curl &&\
	  rm -rf /var/cache/apk/*
	
#Set environment
ENV JAVA_HOME /opt/jdk
ENV PATH ${PATH}:${JAVA_HOME}/bin
