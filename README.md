1) Install Git and Docker
       In Instance   give the below command
⦁	       sudo su && sudo apt updrages
⦁	       sudo apt install git -y
⦁	       sudo apt install docker.io
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/0145eb708feeefa5cbeb4926698a9694cfe6ba52/screenshots%20of%20netdata/Screenshot%202025-08-15%20140528.jpg

2) Run Netdata container (recommended, with Docker monitoring + persisted logs/config)
      This command mounts required host paths so Netdata can read host metrics and docker metrics, and persists its library/cache/logs:
      docker run -d --name=netdata \
      -p 19999:19999 \
      -v netdata_lib:/var/lib/netdata \
      -v netdata_cache:/var/cache/netdata \
      -v /var/log/netdata:/var/log/netdata \
      -v /etc/passwd:/host/etc/passwd:ro \
      -v /etc/group:/host/etc/group:ro \
      -v /proc:/host/proc:ro \
      -v /sys:/host/sys:ro \
      -v /var/run/docker.sock:/var/run/docker.sock:ro \
      --cap-add SYS_PTRACE \
      --security-opt apparmor=unconfined \
      --restart unless-stopped \
      netdata/netdata
   
3) Confirm it’s running & troubleshoot common issues
       docker ps --filter name=netdata

4) Access the dashboard
      Local instance (browser on the instance): http://localhost:19999
      and take the screenshots of CPU, Memory, Disk usage,Docker cointainer etc


