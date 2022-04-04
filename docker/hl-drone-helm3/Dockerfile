FROM python:3.9

ENV HELM_VERSION="v3.8.0"

RUN apt-get update && \
    apt-get install bash curl ca-certificates openssl

RUN curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip -o awscliv2.zip
RUN unzip awscliv2.zip
RUN ./aws/install -i /usr/local/aws-cli -b /usr/local/bin

RUN curl -Lo /usr/local/bin/kubectl \
    https://amazon-eks.s3.us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/kubectl \
    && chmod +x /usr/local/bin/kubectl \
    && kubectl version --short --client

RUN curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > get_helm.sh \
    && chmod +x ./get_helm.sh \
    && ./get_helm.sh -v $HELM_VERSION \
    && helm help

CMD ["/bin/sh"]