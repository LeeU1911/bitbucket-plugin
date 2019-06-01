bitbucket-plugin
================

Temporary fix of *Bitbucket* webhook push to Jenkins failures.

Until https://github.com/jenkinsci/bitbucket-plugin/pull/64 PR is merged and released officially.

## How to use it:
1. Download hpi file: https://github.com/LeeU1911/bitbucket-plugin/blob/generated-hpi/bitbucket.hpi
2. Manually upload it to Jenkins: "Manage Jenkins" -> "Manage Plugins" -> "Advanced" tab -> Upload plugin
3. Plugin should be uploaded and overwrite the previous version of Bitbucket plugin. 

### Error: "413 Request Entity Too Large" 
I personally faced this issue due to Nginx config restriction in Jenkins server.
Fix it by:
1. Adding this line `client_max_body_size 12M;` (bitbucket plugin hpi file size is 10.5M, hence `12M`) under `http` block in `/etc/nginx/nginx.conf` file
2. `sudo service nginx reload`
Read more: https://www.cyberciti.biz/faq/linux-unix-bsd-nginx-413-request-entity-too-large/
