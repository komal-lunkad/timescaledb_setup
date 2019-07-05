FROM ubuntu:18.04
RUN apt-get update
RUN apt-get install etcd -y
RUN apt-get install systemd -y
COPY startup.sh startup.sh
RUN chmod +x startup.sh
# CMD ["/bin/bash", "startup.sh"]
CMD ["etcd"]