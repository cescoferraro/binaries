# kube
CoreOS &amp; Kubernetes  binaries 

Repo used by this gist
https://gist.github.com/cescoferraro/945d25a9ba310077488a

```
Transcription here

# this clone the repo at /opt/bin which is under the $PATH buy may conflict \
  with existing copies of these binaries on core os machines \
  while on a shell environment. Service files should use absolute path anyway.  \
  Keep that in mind when sshing into the servers
  
  TODO : Create a service that remove the installation binaries 
     
      - name: binaries.service
      command: start
      content: |
          [Unit]
          Description=retrieve binaries

          [Service]
          Type=forking
          User=root
          WorkingDirectory=/home/core
          ExecStart=/usr/bin/git clone https://github.com/cescoferraro/kube.git /opt/bin/
          Restart=on-failure
          SuccessExitStatus=128
          RemainAfterExit=yes
          RestartPreventExitStatus=128
          
  
```
