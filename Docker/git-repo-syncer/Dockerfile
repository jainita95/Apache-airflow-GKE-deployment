FROM bitnami/git

# create a dummy user that will match User in Security Context of value.yaml
RUN useradd -u 1001 -ms /bin/bash helper
USER helper
WORKDIR /home/helper

# Add ssh config params for GitHub; 
# substitute deploy-key name in IdentityFile path as needed
RUN mkdir .ssh
RUN touch .ssh/config
RUN echo "Host deploy-key\n  Hostname github.com\n  User git\n  IdentityFile /home/helper" >> .ssh/config;
RUN ssh-keyscan -H github.com >> ~/.ssh/known_hosts;