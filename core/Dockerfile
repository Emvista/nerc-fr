FROM maven:3-jdk-10

ENV MVN_REPO=/usr/src/app
RUN mkdir -p $MVN_REPO
WORKDIR $MVN_REPO

# add pom.xml only here, and download dependency
ADD pom.xml $MVN_REPO
RUN ["/usr/local/bin/mvn-entrypoint.sh", "mvn", "verify", "clean", "--fail-never"]

# now we can add all source code and start compiling
ADD . $MVN_REPO
EXPOSE 8888

CMD ["java", "-jar", "./target/original-opennlp-tools-custom-0.0.1.jar"]