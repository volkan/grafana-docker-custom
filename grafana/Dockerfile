FROM golang:1.8

RUN curl -sL https://deb.nodesource.com/setup_6.x -o nodesource_setup.sh
RUN bash nodesource_setup.sh
RUN apt-get install nodejs bzip2 zip unzip

WORKDIR /go/src/github.com/grafana/
RUN wget https://github.com/grafana/grafana/archive/alerting-elasticsearch.zip
RUN unzip alerting-elasticsearch.zip && mv grafana-alerting-elasticsearch grafana
WORKDIR /go/src/github.com/grafana/grafana
RUN go run build.go setup
RUN go run build.go build

RUN npm install -g yarn grunt-cli
RUN yarn install --pure-lockfile
RUN npm run build