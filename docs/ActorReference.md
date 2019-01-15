
Un actor es un contenedor para:
 + Estado.
 + Comportamiento. 
 + Buzón.
 + Hijos.
 + Estrategia de Supervisión. 
 
Todo esto está encapsulado dentro de una referencia de actor. Un aspecto notable es que los actores tienen un ciclo de vida explícito, no se destruyen automáticamente cuando ya no son referenciados; después de haber creado uno, es su responsabilidad asegurarse de que también terminará, lo que también le da control sobre cómo se liberan los recursos cuando termina un actor.

 ![actores](https://getakka.net/images/actor.png)

Un objeto actor debe estar protegido del exterior para poder beneficiarse del modelo de actor. Por lo tanto, los actores se representan en el exterior utilizando referencias de actores, que son objetos que se pueden pasar libremente y sin restricción. Esta división en objeto interno y externo permite la transparencia para todas las operaciones deseadas: 
 + Reiniciar un actor sin necesidad de actualizar las referencias en otro lugar.
 + Colocar el objeto real del actor en hosts remotos.
 + Enviar mensajes a los actores en aplicaciones completamente diferentes. 

Pero el aspecto más importante es que no es posible mirar dentro de un actor y obtener su estado desde el exterior, a menos que el actor publique esta información de manera imprudente.
