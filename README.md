1) Install Git and Docker
       In Instance   give the below command
⦁	       sudo su && sudo apt updrages.
⦁	       sudo apt install git -y.
⦁	       sudo apt install docker.io.
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
       docker ps --filter name=netdata.

4) Access the dashboard
   Local instance (browser on the instance): http://localhost:19999
   and take the screenshots of CPU, Memory, Disk usage,Docker cointainer etc.
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/5228864474e666695511c88c2d8f7d9479fc6ddd/screenshots%20of%20netdata/Screenshot%202025-08-15%20132608.jpg.
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/90d0acd3d27f7eee63aee657edcc5b5526bfc3d6/screenshots%20of%20netdata/Screenshot%202025-08-15%20132630.jpg.
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/721c6a07cc81283cc60e93a070688b422d071749/screenshots%20of%20netdata/Screenshot%202025-08-15%20132642.jpg.
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/f21853010811e76c4637702b131e9f2b66913c43/screenshots%20of%20netdata/Screenshot%202025-08-15%20132750.jpg.
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/472d268e6f48cec9ae427f7d0f925d067af8aaf9/screenshots%20of%20netdata/Screenshot%202025-08-15%20132844.jpg.
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/97fcfd419417398d44b9a05ad681147289886dea/screenshots%20of%20netdata/Screenshot%202025-08-15%20132904.jpg.
https://github.com/skandakumar1992/Netdata-Docker-monitor/blob/1282d50e21a90f809bd94046d9d81cbf7be46476/screenshots%20of%20netdata/Screenshot%202025-08-15%20133856.jpg.

5) Explore alerts & edit alert definitions
⦁	   docker exec -it netdata /bin/bash.
⦁	   ls -la /etc/netdata/health.d.
⦁	   ls -la /var/log/netdata.
⦁	   exit from the cointainer.

6) crate a folder
⦁	mkdir netdata project.
⦁	cd netdataa project.
⦁	touch docker-compose.yaml.
⦁	vi docker-compose.yaml.

7) create a new repo in your GitHub repositories
⦁	git init.
⦁	git add .
⦁	git commit -m "Initial: Netdata docker compose + screenshots + notes".
⦁	git remote add origin https://github.com/skandakumar1992/Netdata-Docker-monitor.git.
⦁	git push -u origin main.

