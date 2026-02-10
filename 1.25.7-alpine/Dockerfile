FROM golang:1.25.7-alpine

WORKDIR /setup
RUN apk update && apk add --no-cache curl jq gettext unzip aws-cli docker bash git
RUN KUBECTL_VERSION="$(curl -L -s https://dl.k8s.io/release/stable.txt)" \
  && curl -LO "https://dl.k8s.io/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl" \
  && curl -LO "https://dl.k8s.io/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl.sha256" \
  && echo "$(cat kubectl.sha256)  kubectl" | sha256sum -c - \
  && chmod +x kubectl \
  && mv kubectl /bin/kubectl \
  && rm kubectl.sha256

RUN go install golang.org/x/vuln/cmd/govulncheck@latest

ENTRYPOINT [ "bash" ]
