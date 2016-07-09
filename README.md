La siguiente aplicación implementa la Cola de Mensajes Rabbitmq, como ejemplo se escucha el tráfico que pasa por el dispositivo de red y se cuentan los paquetes según el filtro indicado cuando se ejecuta el script que cuenta las tramas.

Los componentes están desarrollados en JavaScript y se utilizó la aplicación nodejs para su ejecución.

/********************************************************************
A continuación de detallas los PRE-REQUISITOS (En caso de no tenerlos configurados en la máquina). Los siguientes comandos se ejecutan directamente en la cónsola y se requiere la autorización del super-usuario. Los comandos fueron probados en ambiente Linux Ubuntu/Mind

- Instalar la aplicación GIT, necesario para la instalación de algunas aplicaciones utilizadas por el ambiente para el JavaScript y para clonar las aplicaciones a ejecutar
	sudo apt-get install git-core

- Instalar el servidor de Rabbitmq, servidor de colas de mensajes
	sudo apt-get install rabbitmq-server

- Instalar la aplicación NPM en conjunto con las librerias requeridas por este programa para funciona correctamente
	sudo aptitude install npm build-essential javascript-common libssl-doc libalgorithm-merge-perl libalgorithm-diff-xs-perl

- Instalar la aplicación nodejs
	sudo aptitude install nodejs-legacy

- Instalar la libreria pcap, librería que permite escuchar el tráfico del dispositivo de red
	sudo aptitude install libpcap-dev

- Instalar los ambientes necesarios para la ejecución de los JavaScript
	sudo npm install amqp
	sudo npm install pcap
	cd node_modules/pcap
	sudo node-gyp configure build
	cd ~

/*********************************************************************
Pasos para ejecutar la aplicación:

- Clonar la aplicacion 
	sudo git clone https://github.com/amadorgarcia01/prodis01.git

- Ejecutar el programa que recibirá los mensajes de la cola de mensajes
	cd prodis01/
	sudo node consumidor.js 

- Abrir una nueva consola y ejecutar
	cd prodis01/
	sudo ./CuentaTrama "" "icmp"

Nota: con los parámetros "" "icmp" se contarán solo los paquetes de este protocolo mas sin embargo esta última aplicación podrá ejecutarse sin parámetros para contar todo lo que pase por el dispositivo de red o indicar otros filtros como por ejemplo:
	sudo ./CuentaTrama "" "tcp port 80"
	sudo ./CuentaTrama eth1 ""
	sudo ./CuentaTrama lo0 "ip proto \\tcp and tcp port 80"'



