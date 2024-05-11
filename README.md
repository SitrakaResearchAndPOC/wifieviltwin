# wifievilportal
# Installing Docker engine over ubuntu
## Add Docker's official GPG key:
```  
apt update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```  
```  
sudo apt-get update
```  

```  
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
```  
xhost +
```  
```  
docker image pull ubuntu:20.04
```  
```  
docker run -tid --privileged -v /dev/bus/usb:/dev/bus/usb -v /tmp/.X11-unix:/tmp/.X11-unix:ro -v $XAUTHORITY:/home/user/.Xauthority:ro --net=host --env="DISPLAY=$DISPLAY" --env="LC_ALL=C.UTF-8" --env="LANG=C.UTF-8" --name wifieviltwin ubuntu:20.04
```  
```  
docker exec -ti wifieviltwin /bin/bash
```  
```  
apt update
```  
```  
apt install nano wireshark net-tools tcpdump  bridge-utils hostapd dnsmasq make git iproute2 mousepad gedit tshark
```
```
ip addr add  192.168.1.1/24 dev wlx001c50b41782
```
or
```
ifconfig wlx001c50b41782 192.168.1.1 255.255.255.0
```
```
git clone https://github.com/oblique/create_ap
```
```
cd create_ap/
```
```
make install
```
```
exit
```

for my connexion internet : wlp3s0 </br>
for sharing internet : wlx001c50b41782 </br>
</br>
</br>
first parameter of create_ap is the wifi interface </br>
second parameter of create_ap is the internet interface </br>
third parameter of create_ap is the name of acces point </br>
fourth parameter of create_ap is password </br>
```  
docker exec -ti wifieviltwin bash create_ap/create_ap wlx001c50b41782 wlp3s0 MyAccessPoint
```
```
xhost +
```
```
docker exec -ti wifieviltwin wireshark
```  
# SAVING

```  
docker ps
```  
for having <id>
```  
docker commit <id> wifieviltwin
```  
```  
docker save wifieviltwin -o wifieviltwin.tar.gz
```


# LOAD AND RUN
```
docker image -i wifieviltwin.tar.gz
```
```
xhost +
```
```  
docker run -tid --privileged -v /dev/bus/usb:/dev/bus/usb -v /tmp/.X11-unix:/tmp/.X11-unix:ro -v $XAUTHORITY:/home/user/.Xauthority:ro --net=host --env="DISPLAY=$DISPLAY" --env="LC_ALL=C.UTF-8" --env="LANG=C.UTF-8" --name wifieviltwin wifieviltwin
```
```
ifconfig
```
for my connexion internet : wlp3s0 </br>
for sharing internet : wlx001c50b41782 </br>
</br>
</br>
first parameter of create_ap is the wifi interface </br>
second parameter of create_ap is the internet interface </br>
third parameter of create_ap is the name of acces point </br>
fourth parameter of create_ap is password </br>
```  
docker exec -ti wifieviltwin bash create_ap/create_ap wlx001c50b41782 wlp3s0 MyAccessPoint
```
