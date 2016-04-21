FROM williamyeh/ansible:centos7

COPY . /opt/autodeploy/containers/data

COPY ~/github.pem /opt/autodeploy/containers/data

WORKDIR /opt/autodeploy/containers/data
RUN ansible-playbook software-install.yml
RUN ansible-playbook download-files.yml && \ 
    ansible-playbook minimize-rhel-iso.yml && \ 
    ansible-playbook scaleio-extract.yml 	


VOLUME ["/opt/hanlon","/opt/autodeploy/resources"]


CMD ["true"]


