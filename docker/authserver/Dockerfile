FROM ubuntu:bionic
# install the required dependencies to run the authserver
RUN apt update && apt install -y libmysqlclient-dev libssl-dev libace-6.* libace-dev net-tools libreadline7

HEALTHCHECK --interval=5s --timeout=15s --start-period=30s --retries=3 CMD netstat -lnpt | grep :3724 || exit 1

## Copy binary
COPY --from=acbuilder:latest /azeroth-server/bin/authserver /azeroth-server/bin/authserver
COPY . /azeroth-server/ 
# run the authserver located in the directory "docker/authserver/bin" of the host machine
CMD ["/azeroth-server/bin/authserver"]
