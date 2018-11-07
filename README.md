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

# 5 Understanding ROS nodes

Es segueix el tutorial de http://wiki.ros.org/ROS/Tutorials/UnderstandingNodes

Ens demana instalar un paquet prèviament insatal·lat en l'exercici 2: ***sudo apt-get install ros-melodic-ros-tutorials***.

Ens introdueix el concepte de *Nodes* com a un executable que utilitza ROS per comunicar-se amb altres nodes. Les *Client Libraries* permeten la comunicació entre nodes escrits en diferents llenguatges de programació, com podrien ser *rospy* per la llibreria de python o *roscpp* per la llibreria de c++.

Per treballar amb ROS, la primera tasca a dur a terme és executar el ***roscore*** i deixar la finestra oberta amb el roscore executant-se, mentre obres un altre terminal on treballar.

En aquest segon terminal, es pot executar qualsevol node comprès en un paquet amb la comanda ***rosrun (package_name) (node_name)***. Per observar els nodes que s'estan executant s'utilitza la comanda ***rosnode list***.

# 6 Understanding ROS topics

Es segueix el tutorial de http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics

En aquest exercici agafem d'exemple un node executat en l'exercici anterior: ***rosrun turtlesim turtlesim_node***, on *turtlesim* és el nom del paquet i *turtlesim_node* el seu node.

A partir d'aquest executem un altre node que ens permetrà moure la tortuga que ens apareix en pantalla amb el primer node: ***tosrun turtlesim turtle_teleop_key***. El que permet que es comuniqui un amb altre és el que anomenem *Topic*.

Per visualitzar els Nodes amb els Topics que els enllacen, executem la comanda ***rosrun rqt_graph rqt_graph***. Amb aquest node, veiem la conexió amb els nodes, quin és el que actua sobre l'altre i com.

Amb ***rostopic echo (topic)*** veiem la informació plubicada en el topic especificat.

Amb ***rostopic list -v*** mostra una llista detallada de topics per publicar i subscriure's al seu tipus.

Amb ***rostopic type (topic)*** veiem el tipus de topic que ens referim. A més, amb ***rosmsg show (el topic type que et doni l'anterior comanda)*** et mostra el tipus de missatge que esta enviant.

Amb ***rostopic pub (topic) (msg_type) (args)*** es publica informació en el topic especificat.

Amb ***rostopic hz (topic)*** ens marca la velocitat amb la que la informació es publicada.

Finalment amb ***rosrum rqt_plot rqt_plot*** s'ens obra una finestra on podrem definir quin topic volem visualitzar i ens dibuixarà una gràfica de cada una de les variables del topic marcat. La visualització del nombre de variables és editable amb els botons + i -.

# 7 Understanding ROS Services and Parameters

Es segueix el tutorial de http://wiki.ros.org/ROS/Tutorials/UnderstandingServicesParams

En aquest exercici utilitzem les comandes ***rosservice*** i ***rosparam***. 

- ***rosservice list***: ens mostra els serveis que et permet fer el/s node/s que estan en execució.
- ***rosservice type (service)***: ens permet saber de quin tipus és el servei que hem seleccionat.
- ***rosservice call (service) (args)***: per cridar el servei i que es dugui a terme.

Amb el rosparam podem guardar i manipular informació en el servidor de paràmetres de ROS:

- ***rosparam list***: ens mostra els paràmetres que gestiona el/s node/s que estan en execució i que es troben en el servidor de paràmetres de ROS.
- ***rosparam set (param_name)***: per establir un valor a un paràmetre.
- ***rosparam get (param_name)***: per obtenir el valor d'un paràmetre.
- ***rosparam dump (file_name) (namespace)***: per guardar una configuració de paràmetres en un arxiu.
- ***rosparam load (file_name) (namespace)***: per carregar una configuració de paràmetres d'un arxiu.

