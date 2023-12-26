FROM ubuntu:latest

LABEL maintainer="Sokolov Alexandr Dm"
LABEL mail="koxed@kox.com"
LABEL description="Containered WBDashboard service - platform to view all wireguard configurations and manage them in an easier way"
LABEL version="0.0"

RUN apt update && apt -y install sudo wireguard net-tools python3-pip git
WORKDIR /service
RUN useradd user01
RUN echo "user01 ALL=(ALL) NOPASSWD:ALL" | tee /etc/sudoers.d/user01
RUN chown -R user01:user01 /service
USER user01

RUN git clone -b v3.0.6 https://github.com/donaldzou/WGDashboard.git wgdashboard
WORKDIR /service/wgdashboard/src
RUN sudo chmod u+x wgd.sh
RUN sudo ./wgd.sh install
RUN sudo chmod -R 755 /etc/wireguard
CMD ["sudo", "./wgd.sh", "debug"]
