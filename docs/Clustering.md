# Clustering

## ¿Qué es un "cluster"? 

Un cluster representa una red peer-to-peer de aplicaciones Akka.NET, tolerante a fallas, elástica, sin punto unico de falla o cuello de botella. Akka.Cluster es el módulo que le brinda la capacidad de crear estas aplicaciones.

## Beneficios de Akka.Cluster 
En **resumen, estos son los beneficios de un cluster adecuadamente diseñado**: 

+ **Tolerante a los fallos**: los clusteres se recuperan de los fallos (especialmente las particiones de red) con facilidad. 

+ **Elástico**: los Clusters son inherentemente elásticos y pueden escalar hacia arriba / abajo segun sea necesario. 

+ **Descentralizado**: es posible tener múltiples réplicas iguales de un microservicio o parte del estado de la aplicación que se ejecutan simultáneamente en todo un cluster 

+ **Peer-to-peer**: los nuevos nodos pueden contactar a los pares existentes, recibir notificaciones sobre otros pares e integrarse completamente en la red sin ningún cambio en la configuración. 

+ **No hay un solo punto de falla / cuello de botella**: múltiples nodos pueden atender solicitudes, lo que aumenta el rendimiento y la tolerancia a fallas.

## ¿En qué se diferencia el cluster de la comunicación remota? 
Akka.Cluster es una capa de abstracción sobre Akka.Remote, que utiliza Remoting para una estructura específica: grupos de aplicaciones. 

_Por debajo_, Akka.Remote le da poder a Akka.Cluster, por lo que cualquier cosa que pueda hacer con Akka.Remote también es compatible con Akka.Cluster. 

En general, Akka.Remote sirve como soporte para Akka.Cluster y otros módulos de "alta disponibilidad" dentro de Akka.NET. 

Por lo general, solo usaría Akka.Remote en escenarios que no requieren la elasticidad y las necesidades de tolerancia a fallas que proporciona Akka.Cluster. 

Esencialmente, Akka.Cluster extiende Akka.Remote para proporcionar la base de aplicaciones escalables.