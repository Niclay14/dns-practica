Práctica DNS Maestro-Esclavo

Paso a paso de la configuración

1. primer paso
utilizamos un Vagrantfile para crear y configurar dos máquinas virtuales: tierra (maestro) y venus (esclavo). Las dos  máquinas están en la misma red privada.

2. Configuración del servidor Maestro

En el archivo de configuración del servidor maestro(named.conf.local), declaramos la zona directa y inversa del dominio sistema.test y se habilita la transferencia de zona al servidor esclavo.