FROM ubuntu
RUN apt-get update && apt-get upgrade -yq
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y curl openssh-server ca-certificates tzdata
RUN curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get install gitlab-ce -y
EXPOSE 80 443 2222
RUN echo "Port 2222" >> /etc/ssh/sshd_config
RUN cp /etc/gitlab/gitlab.rb /etc/gitlab/gitlab.bak
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 2222" >> /etc/gitlab/gitlab.rb
RUN echo "external_url 'https://10.11.4.15'" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https_port'] = 80" >> /etc/gitlab/gitlab.rb
RUN echo "letsencrypt['enable'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "#!/bin/bash\n/etc/init.d/ssh start\n/opt/gitlab/embedded/bin/runsvdir-start &\ngitlab-ctl reconfigure\ntail -f /dev/null" > /root/launch.sh && chmod +x /root/launch.sh
ENTRYPOINT ["/root/launch.sh"]

#docker run  --name gitlab --rm -p 80:80 -p 2222:2222 -p 443:443

