#FROM churrops/jdk8:1.3 as builder
FROM anapsix/docker-alpine-java as builder

WORKDIR /opt

RUN git clone https://github.com/maisacaceres/zuul.git \
    && cd zuul \
    && chmod +x gradlew \
    && ./gradlew clean build

FROM anapsix/docker-alpine-java

RUN mkdir /opt/zuul

WORKDIR /opt/zuul

COPY --from=builder /opt/zuul/build/libs/ .

CMD ["java","-jar","zuul-1.0.0.jar"]
