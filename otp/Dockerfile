FROM docker.io/opentripplanner/opentripplanner:2.6.0_2024-06-04T10-07

ARG PROVIDER

## need to override the data location because /var/opentripplanner/ is a volume
WORKDIR /var/otp/
COPY build-config.json otp-config.json /var/otp/
COPY router-config-${PROVIDER}.json /var/otp/router-config.json

RUN java $JAVA_OPTS -cp @/app/jib-classpath-file @/app/jib-main-class-file /var/otp/ --build --save

ENTRYPOINT java $JAVA_OPTS -cp @/app/jib-classpath-file @/app/jib-main-class-file /var/otp/ --load --serve
