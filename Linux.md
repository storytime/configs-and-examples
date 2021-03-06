``` mount -l``` - **mount params**

```mount -o remount,rw /path/to/ ``` - **remount /path/to/ rw**

```dd if=/dev/zero of=file1G.tmp bs=1M count=10``` - **create empty file**

```wget -r -k -l0 -p -E -nc http://site.com/``` - **wget site**

```tar xvf archive.tar.bz``` - **extract**

```tar cvf file.tar``` - **create tar**

```chown -R user:group /path/to/``` - **chmod recursive**

```serv: nc -u -l -p 40101 cl: nc -u IP 40101``` - **test ports**

```cat /etc/passwd | awk -F ':' '{ print $1 }'``` - **list users**

```find . -name *.class -type f``` - **find**

```find . -name '*.tmp' -and -size +9M #find < 9M``` - **find**

```find . -type f -mtime +60 -name '*.tmp' -exec ls -l {} \;``` - **find by time and exec**

```rsync -avz --progress user@host:/tmp /tmp``` - **rsync from remote**

```rsync -avz --progress -e ssh user@host:/tmp /tmp``` - **rsync via ssh**

```curl -v -H "Accept: application/json" -H "Content-type: application/json" -X POST -d '{"title":"test"}' http://localhost:9001/json/post``` - **post json**

```echo 2 | awk -F. -v OFS=. 'NF==1{print ++$NF}; NF>1{if(length($NF+1)>length($NF))$(NF-1)++; $NF=sprintf("%0*d", length($NF), ($NF+1)%(10^length($NF))); print}'``` - **inc num**

```for each in $(echo */ | sed "s/ /\n/g" | sed "s/\///g");  do du -hs "$each"; done;```` - **list dir size**

```netstat -tulpn``` - **show ports in use**

```sum=0; result=0; for i in `ps auxfww | egrep "PROCESS NAME" | awk '{print $6}'`; do ((sum=sum+i)); done; ((result=sum/1024)); echo $result Mb``` - **calculate summary prosess Memory**

```nice -n 19 ionice -c3 bzip2 -f /path/to/log``` - **compress logs min cpu usage min io**

```nc -u -l -p 40101 and nc -u 78.46.151.106 40101``` - **check network port**
