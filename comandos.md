# Comandos de docker que te pueden servir

## 1. inspect

Para saber en que ip se esta ejecutando un determinado contenedor

```bash
$ docker inspect container_id
```

# Comandos de redis

## 1. CLI redis

Para entrar al CLI de redis en donde puedes hacer debuguear y monitorear la base de datos

```bash
$ redis-cli -h 192.168.0.7 # Conecta a redis

```

## 2. Estadísticas de uso del Nodo.

Permite monitoriar cantidades de claves, memoria, clientes, peticiones etc.

```bash
$ redis-cli -h 172.17.0.2 -a password123 --stat

------- data ------ --------------------- load -------------------- - child -
keys       mem      clients blocked requests            connections
2          828.77K  2       0       22 (+0)             6
2          828.77K  2       0       23 (+1)             6
2          828.77K  2       0       24 (+1)             6
2          828.77K  2       0       25 (+1)             6
2          828.77K  2       0       26 (+1)             6
2          828.77K  2       0       27 (+1)             6
2          828.77K  2       0       28 (+1)             6
2          828.77K  2       0       29 (+1)             6
```

## 3. Ver informacion almacenada

Podemos ver las claves almacenadas en la base de datos

```bash
$ redis-cli -h 172.17.0.2 -a password123 --scan

nelson
github
devTeam504
```

## 4. Filtro

Podemos buscar por texto la información

```bash
$ redis-cli -h 172.17.0.2 -a password123 --scan --pattern '*nel*'

nelson
```

## 4. Monitor

Podemos ver en pantalla todos los comandos que llegan al Nodo.

```bash
$ redis-cli -h 172.17.0.2 -a password123 --scan --pattern '*nel*'

1511798824.960750 [0 172.17.0.1:41126] "set" "zz111" "9955d239"
1511798829.839087 [0 172.17.0.1:41126] "get" "zz111"
```

## 4. Latencia

```bash
$ redis-cli -h 172.17.0.2 -a password123 --latency-dist
---------------------------------------------
. - * #          .01 .125 .25 .5 milliseconds
1,2,3,...,9      from 1 to 9     milliseconds
A,B,C,D,E        10,20,30,40,50  milliseconds
F,G,H,I,J        .1,.2,.3,.4,.5       seconds
K,L,M,N,O,P,Q,?  1,2,4,8,16,30,60,>60 seconds
From 0 to 100%:
---------------------------------------------
.-*#123456789ABCDEFGHIJKLMNOPQ?
.-*#123456789ABCDEFGHIJKLMNOPQ?
.-*#123456789ABCDEFGHIJKLMNOPQ?
.-*#123456789ABCDEFGHIJKLMNOPQ?
.-*#123456789ABCDEFGHIJKLMNOPQ?

```


## 4. Información de la replicación

```bash
$ redis-cli -h 172.17.0.3 -a password123 info replication
```
