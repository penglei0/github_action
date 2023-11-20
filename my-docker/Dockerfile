FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update && \
    apt upgrade --yes && apt-get install --yes \
    net-tools iproute2 python3 libatomic1 iperf3 iputils-ping python3-pip vim openssh-server sysstat

RUN pip3 install psutil matplotlib paramiko prettytable pdfkit PyPDF2 reportlab tqdm markdown python-markdown-math

WORKDIR /root
