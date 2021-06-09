# docker01
https://tech.osteel.me/posts/docker-for-local-web-development-part-1-a-basic-lemp-stack
	linux + nginx + mysql + php (+ phpmyadmin) einrichten


restart mit einem bestimmten yml-file
	docker-compose -f docker-compose-development.yml restart
	
docker-container auflisten
	docker ps
	(oder docker container ls)
	
	CONTAINER ID   IMAGE      COMMAND                  CREATED             STATUS              PORTS                                       NAMES
	de14612e204c   mw3_fex    "/entry.sh /usr/sbin..." 4 months ago        Up 8 hours          0.0.0.0:2222->22/tcp                        mw3_fex
	f2a4ffc7e492   mw3_lb     "nginx -g 'daemon of..." 4 months ago        Up 8 hours          0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp    mw3_lb
	53d3878db4d1   mw3_test   "/usr/sbin/sshd -D"      4 months ago        Up 8 hours          0.0.0.0:2223->22/tcp                        mw3_test
	465d4a1f0bd9   mw3_cron   "cron -f"                4 months ago        Up 8 hours                                                      mw3_cron
	...
	
	-a
	zeigt auch beendete container an

auf der maschine auf der docker laeuft die bash fuer einen der container oeffnen
	docker exec -it <IMAGE> bash
	
	<IMAGE> ist die bezeichnung die beim "docker ps" unter "IMAGE" aufgelistet ist
	-it sorgt fuer den interaktiven modus (exce fuehrt im grunde nur einen befehl aus und man wuerde sonst anschliessend wofort wieder rausfliegen)

docker stop <container-id>

docker rm <name>
	container entfernen und resourcen bereinigen, alle aenderungen im containereigenen imagesystem sind damit weg

	-f	beenden erzwingen und container entfernen

docker start <name>

docker image rm <image>
	image vom lokalen computer entfernen

docker inspect <IMAGE>

docker run --user <<user>:<group>
	kommandos im container als dieser user/diese group ausfuehren
	user und group muessen als zahl angegeben werden
		docker run --user $(id -u):$(id -g)
			loest dsa problem $ id -u liefert die nummer des aktuellen users, $ id -g die der gruppe
