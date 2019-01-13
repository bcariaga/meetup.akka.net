# ¿Que es Akka.NET?

## Problema

Cada vez es más común que encontremos requerimientos de aplicaciones que tienen que manejar la **concurrencia**, que puedan **escalar**, se **comuniquen contras aplicaciones**, tengan **alta disponibilidad** y ademas **tolerancia a fallos**. 

Para cumplir con esto empezamos a desacoplar los sistemas, creando módulos mas pequeños y "mantenibles", esto tiene un costo de integración mas alto. Ademas debemos crear algún soporte de fallos, mas si los sistemas se comunican a través de la red.

Esta problemática es la que busca solucionar Akka.NET.

## Akka.NET

Akka.NET es un conjunto de librerías open source para diseñar sistemas escalables y resilientes*, poniendo foco en la necesidad del negocio en lugar de escribir código a _"bajo nivel"_.

Estas librerías nos proveen:

+ Manejo _multi-thread_ sin necesidad de preocuparse por los `Thread` o usar `lock`, manejo eficiente de memoria.
+ Comunicación remota transparente entre sistemas y componentes sin necesidad de escribir código extra para estas comunicaciones.
+ Una arquitectura en clúster de alta disponibilidad que es elástica, escalable (dentro o fuera), **a pedido**.

Akka.NET usa el _modelo de actores_ para proporcionar un nivel de abstracción que facilita la escritura correcta de **sistemas concurrentes, paralelos y distribuidos**.

El _modelo de actores de Akka_ ofrece una profundidad de integración que no puede lograr seleccionando bibliotecas para resolver problemas individuales e intentando unirlas.

---

_*Resiliencia:  capacidad de un sistema tecnológico de soportar y recuperarse ante desastres y perturbaciones._