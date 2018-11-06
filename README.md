# ROS_tutorials
Iniciació al ROS

# 1. Installing and configuring your ROS environment

En primer lloc clicarem en l'enllaç de *ROS installation instructions* que ens portarà en una nova pestanya on ens donarà a escollir entre el ROS Kinetic o el Melodic, en el meu cas escullo el Melodic. En la següent finestra escollim el nostre sistema operatiu (Ubuntu en el meu cas) i seguirem les instruccions que ens marca:

1: *sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'*
 per tal de preparar l'ordinador per acceptar paquets de software per part de ROS.

2: *sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116* per establir les claus.

3: *sudo apt update* per verificar que el Debian està al dia amb les actualitzacions.

4: *sudo apt install ros-melodic-PACKAGE* comanda que permet instalar els paquets de ROS melodic que vulguis, simplement canviant la paraula PACKAGE pel nom del paquet. Els paquets disponibles es poden visualitzar amb la comanda *apt search ros-melodic*
