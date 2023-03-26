## BUILDING phase
FROM alpine:3.17 AS build

RUN apk add --no-cache maven git

##Clone repo
RUN git clone https://github.com/damienMS/doodlestudent.git

WORKDIR /doodlestudent/api

RUN git checkout develop

##Compile the back
RUN mvn clean package -Dquarkus.package.type=uber-jar


## RUN phase
FROM alpine:3.17

RUN apk add --no-cache openjdk11

##Add it on the Run image and start it 
COPY --from=build /doodlestudent/api/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar /target/

CMD [ "java", "-jar", "/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar" ]
