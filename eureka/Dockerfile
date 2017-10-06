#FROM churrops/jdk8:1.3 as builder
FROM anapsix/docker-alpine-java as builder

WORKDIR /opt

RUN git clone https://github.com/maisacaceres/eureka.git \
    && cd eureka \
    && ./gradlew clean build

FROM  anapsix/docker-alpine-java

RUN mkdir /opt/eureka

WORKDIR /opt/eureka

COPY --from=builder /opt/eureka/build/libs/ .

CMD ["java","-jar","eureka-1.0.0.jar"]
