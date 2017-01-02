from ubuntu:16.04

WORKDIR /root

RUN apt-get update && apt-get -y install software-properties-common python-software-properties

#add repositories needed
RUN add-apt-repository -y ppa:webupd8team/java 
RUN apt-add-repository ppa:ansible/ansible
RUN apt-get update 

# preaccept Oracle license
RUN echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
RUN echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections

#install java8 and ansible
RUN apt-get -y install oracle-java8-installer ansible vim

ADD http://mirrors.jenkins.io/war-stable/latest/jenkins.war .
COPY .jenkins /root/.jenkins

CMD java -jar jenkins*.war