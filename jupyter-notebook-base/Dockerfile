FROM centos:7
MAINTAINER out001a shanhuanming@foxmail.com

# env
ENV USER jupyter
ENV HOME /home/$USER

# user
RUN useradd $USER
WORKDIR $HOME
RUN mkdir notes .jupyter
RUN chown -R $USER:$USER $HOME

# yum source
RUN mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
ADD source/CentOS-Base.repo /etc/yum.repos.d/
RUN yum -y makecache

RUN yum provides '*/applydeltarpm'
RUN yum -y install deltarpm
RUN yum -y install epel-release
RUN yum -y install https://mirrors.tuna.tsinghua.edu.cn/remi/enterprise/remi-release-7.rpm
RUN rpm --import /etc/pki/rpm-gpg/RPM-*
RUN yum -y update

# python 3.6
RUN yum -y install python36
RUN curl https://bootstrap.pypa.io/get-pip.py -o /tmp/get-pip.py
RUN mkdir -p $HOME/.cache/pip && python36 /tmp/get-pip.py && rm /tmp/get-pip.py
RUN mkdir -p $HOME/.config/pip && \
    echo -e "[global]\nindex-url = https://pypi.tuna.tsinghua.edu.cn/simple" > $HOME/.config/pip/pip.conf

# jupyter
RUN pip install jupyter
COPY conf/jupyter_notebook_config.py $HOME/.jupyter/

VOLUME ["$HOME/notes"]
EXPOSE 8899

# CMD ["jupyter", "notebook", "--ip", "0.0.0.0", "--port", "8899", "--allow-root", "--no-browser"]
ENTRYPOINT ["jupyter", "notebook"]
