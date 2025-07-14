# xashds_public_server-vps-_tutorial
All steps to do on vps linux to open xash3d public server (root without usr )


# this script show u how to install xash3d public server on vps linux with addons and fastdl

 ( this example tutorial for classic server  )
 
# example:
   for this tutorial i use xash folder inside them cstrike and valve games (xash/cstrike/...)  
   game directory in
   home/xash

# test it on vps:
> ubuntu 20.04 LTS x64

> 1gb ram 

> 1core 

> 20gb storage

# SSH useage:
JuiceSSH
 
<img src="https://github.com/happyhere-TN/xashds_public_server-vps-_tutorial/blob/main/juiceicon.png?raw=true" width="50"/>
is batter to use it for any shell or cli hostes with more good things (download the apk from google not acces on playstore)

# //--Install softweres and libs root without user. (pls copy line by line cods)
    apt update -y 
    dpkg --add-architecture i386
    apt install lib32gcc-s1 lib32stdc++6 libc6-i386 libcurl4-gnutls-dev:i386 libsdl2-2.0-0:i386
    add-apt-repository multiverse
    cd && apt install steamcmd
    apt install unzip -y
    apt intall wget -y
    apt install apache2
    apt update

 
 # //--Login to steamcmd and install hlds files. (pls copy line by line cods)
    steamcmd
    force_install_dir /home/xash/ 
    login anonymous
    app_update 90 validate
    exit

# //-- Install xashds libs new ongine only. (pls copy line by line cods)
    cd && cd /home/xash && rm filesystem_stdio.so
    wget https://github.com/FWGS/xash3d-fwgs/releases/download/continuous-vbo-fix/xashds-linux-i386.tar.gz
    tar -zxf xashds-linux-i386.tar.gz && cd xashds-linux-i386 && cp -rf * /home/xash && cd .. && rm xashds-linux-i386.tar.gz && rm -rf xashds-linux-i386 && chmod +x * && cd && cd /home/xash

---- Now if u want open server but classic mod (without addons) Below you will find an command that starts with screen... just copy it to vps.
---- if u wont addons and fastdll dont open the server with screen..  and And follow the rest of the explanation


# //--install amxmod 1.9-with metamod. (pls copy line by line cods)
    cd && cd /home/xash/cstrike && rm liblist.gam && rm gameinfo.txt && rm -rf addons && cd ..
    wget https://github.com/happyhere-TN/xashds_public_server-vps-_tutorial/raw/refs/heads/main/addons_for_xashds.zip
    unzip addons_for_xashds.zip && rm addons_for_xashds.zip

# //--Fastdl configerate. (pls copy line by line cods)
    cd && cd /var/www/html && mkdir cstrike 
    cd && cd .. && cd /home/xash/cstrike
    cp -rf models /var/www/html/cstrike
    cp -rf sound /var/www/html/cstrike
    cp -rf gfx /var/www/html/cstrike
    cp -rf maps /var/www/html/cstrike
    cp -rf sprites /var/www/html/cstrike
    cd && cd .. && cd ..  && cd /var/www/html
    chmod -R 777 *

# //-- configerate server.cfg: (pls copy line by line cods)
    cd && cd /home/xash/cstrike && nano server.cfg
    hostname "set-ur-server-name"
    sv_allow_download "1"
    sv_allow_upload "1"
    sv_downloadurl "http://my-vps-ip/cstrike/"

# ---save the change configer on mobile press"[ctrl] and [x] and [y] and [entr]

   <img src="https://github.com/happyhere-TN/xashds_public_server-vps-_tutorial/blob/main/server_confugerate_save.jpg?raw=true" width="300"/>

# //--from here ur server ready to open with latest updates plus fastdl to run server: (pls copy line by line cods)
    cd && cd /home/xash
    screen ./xash3d -game cstrike +maxplayers 32 +map de_dust2 +port 27015

---to close server tipe: exit

---(about how to add plugins and add mods like zp or ze ...  its need more time to set tutorial if u want that ask me on issues)

