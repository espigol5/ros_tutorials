# ROS_tutorials
Iniciació al ROS http://wiki.ros.org/ROS/Tutorials

# 1. Installing and configuring your ROS environment

Es segueix el tutorial de http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment

En primer lloc clicarem en l'enllaç de *ROS installation instructions* que ens portarà en una nova pestanya on ens donarà a escollir entre el ROS Kinetic o el Melodic, en el meu cas escullo el Melodic. En la següent finestra escollim el nostre sistema operatiu (Ubuntu en el meu cas) i seguirem les instruccions que ens marca:

1: ***sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'***
 per tal de preparar l'ordinador per acceptar paquets de software per part de ROS.

2: ***sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116*** per establir les claus.

3: ***sudo apt update*** per verificar que el Debian està al dia amb les actualitzacions.

4: ***sudo apt install ros-melodic-PACKAGE*** comanda que permet instalar els paquets de ROS melodic que vulguis, simplement canviant la paraula PACKAGE pel nom del paquet. Els paquets disponibles es poden visualitzar amb la comanda ***apt search ros-melodic***.

5: Abans d'utilitzar ROS, és necessariuna inicialització del rosdep ***sudo rosdep init***, en cas de que requereixi una actualització, previament executarem la comanda ***rosdep update***. Així, serà més fàcil instalar dependencies del sistema per compilar.

6: ***echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc*** per tal de posar a punt l'entorn de treball i que al iniciar una nova shell les variables d'entorn s'adhereixin en el teu bash.

Fins aquí tot el necessari per arrencar ROS i els seus paquets.

Seguidament, el tutorial ens mostra com crear un espai de treball:

- Creem una carpeta nova en l'arrel ***mkdir -p ~/catkin_ws/src*** i ens hi situem ***cd ~/catkin_ws/***. 

- Executem la comanda ***catkin_make***, necessària per treballar en espais de treball catkin. Aquesta, el primer cop que l'executes et crea diverses carpetes juntament amb un document CMakeLists.txt.

- Dins la carpeta devel, hi ha nous arxius amb terminació .sh i per establir el nou arxiu de .sh's: ***source devel/setup.bash***. Per assegurar-te de que el procés anterior s'ha realitzat correctament ***echo $ROS_PACKAGE_PATH***, hauria de sortir: /home/youruser/catkin_ws/src:/opt/ros/melodic/share


# 2. Navigating the ROS filesystem

Es segueix el tutorial de http://wiki.ros.org/ROS/Tutorials/NavigatingTheFilesystem

En aquest exercici inspeccionem comandes bàsiques dins el paquet ros-tutorials, que instal·lem amb ***sudo apt-get install ros-melodic-ros-tutorials***

En aquest ens ensenya l'ús de:
- ***rospack find [package_name]*** per trobar el camí d'on es troba el paquet dins ROS.
- ***roscd*** per canviar de directori on es troba un paquet de ROS automàticament sense necessitat de posar el camí complert.
- ***rosls*** per visualitzar el contingut d'un paquet de ROS.
- Ús del tabulador.

# 3 Creating a ROS package

Es segueix el tutorial de http://wiki.ros.org/ROS/Tutorials/CreatingPackage

Et defineix el concepte de catkin Package, així com la seva estructura, que com a mínim ha de contenir un *CMakeLists.txt* i un *package.xml*.

Es crea un directori de catkin previament en l'exercici 1 amb la comanda ***mkdir -p ~/catkin_ws/src*** i ens hi situem amb ***cd ~/catkin_ws/***. En aquest directori es crea un paquet anomenat *beginner_tutorials* amb la comanda ***catkin_create_pkg beginner_tutorials std_msgs rospy roscpp***.

A continuació, ens tornem a col·locar en la carpeta *~/catkin_ws* i executem un ***catkin_make***, per fer un build en el nostre espai de treball de catkin. Per afegir l'espai de treball en l'entorn de ROS, ***. ~/catkin_ws/devel/setup.bash***.

Amb la comanda ***rospack depends1 beginner_tutorials*** es poden veure les dependències del paquet que hem creat, que es situen en l'arxiu *package.xml*.

En aquest arxiu .xml, hi trobem descripció del paquet i de l'usuari que l'ha creat, llicències i dependències.

# 4 Building a ROS package

Es segueix el tutorial de http://wiki.ros.org/ROS/Tutorials/BuildingPackages

Es defineix com es construeixen projectes amb el catkin en comparació amb el cmake. La comanda s'ha realitzat en exercicis anteriors: ***catkin_make***. Aquesta comanda et genera automàticament les carpetes *devel* i *build*, que es sumen a la carpeta *src* en l'espai de treball de catkin.




