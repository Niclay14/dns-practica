Práctica DNS Maestro-Esclavo

Paso a paso de la configuración

1. primer paso
utilizamos un Vagrantfile para crear y configurar dos máquinas virtuales: tierra (maestro) y venus (esclavo). Las dos  máquinas están en la misma red privada.

2. Configuración del servidor Maestro

En el archivo de configuración del servidor maestro(named.conf.local), declaramos la zona directa y inversa del dominio sistema.test y se habilita la transferencia de zona al servidor esclavo.

3. Configuración del servidor Esclavo
El servidor esclavo está configurado para obterner la zona del maestro. 

4. Transferencia de Zona
Una vez que tenemos ambos servidores configurados usariamos este comando dig @192.168.57.102 sistema.test AXFR

para comprobar si esta todo bien