FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get install -y git python3-pip python3 openslide-tools

# uncomment:
    # 1 - this additional RUN only if you are facing issues with UTF8 when running your container
    # 2 - all ENV variables in comment

    #RUN apt-get update -y \
    #    && apt-get install --reinstall -y locales \
    #    # uncomment chosen locale to enable it's generation
    #    && sed -i 's/# pl_PL.UTF-8 UTF-8/pl_PL.UTF-8 UTF-8/' /etc/locale.gen \
    #    # generate chosen locale
    #    && locale-gen pl_PL.UTF-8

    ## set system-wide locale settings 
    #ENV LANG pl_PL.UTF-8
    #ENV LANGUAGE pl_PL
    #ENV LC_ALL pl_PL.UTF-8

RUN cd /opt && git clone https://github.com/choosehappy/HistoQC.git
RUN pip3 install --upgrade pip
RUN pip3 install -r /opt/HistoQC/requirements.txt
RUN pip3 install --pre girder-slicer-cli-web girder-client

COPY . $PWD


ENTRYPOINT ["python3", "./cli_list.py"]
