# Proyecto SQL creacion base de datos Celulares Apple

Este proyecto se realizará a razón de tener una base de datos capaz de guardar todos los datos de creación de nuevos productos en el catálogo de iphone.

### Objetivos:

- SKU de Celulares
- Consistencia en los datos
- Consultas rápidas y hacer conexiones con los diferentes excel de las áreas administrativas.

### Diagrama de Entidad Relacion:

![](./img/entidad-relacion.png)

### Tablas:

![](./img/tablas-1.png)
![](./img/tablas-2.png)

### Script SQL

Creacion de base de datos y tabla de celulares.

```
CREATE SCHEMA IF NOT EXISTS IphoneData;

USE IphoneData;

CREATE TABLE IF NOT exists Direccion (
	id_direccion int not null auto_increment,
    direccion varchar (255) not null,
    pais varchar (255) not null,
    ciudad varchar (255) not null,
    primary key (id_direccion)
);


CREATE TABLE IF NOT exists Clientes (
	id_cliente int not null auto_increment,
    dni varchar (8) not null,
    nombres varchar (255) not null,
    apellidos varchar (255) not null,
    id_direccion int,
    primary key (id_cliente),
    foreign key (id_direccion) references Direccion(id_direccion)
);

CREATE TABLE IF NOT exists Tienda (
	id_tienda int not null auto_increment,
    nombre_sucursal varchar (255) not null,
    id_direccion int,
    primary key (id_tienda),
    foreign key (id_direccion) references Direccion(id_direccion)
);


CREATE TABLE IF NOT exists sku (
	id_sku int not null auto_increment,
    nombre_sku varchar (255) not null,
    codigo_sku varchar (255) not null,
    precio float,
    primary key (id_sku)
);

CREATE TABLE IF NOT exists Celulares(

	id_imei int not null auto_increment,
	imei varchar (15) not null,
	modelo varchar (255) not null,
	capacidad varchar (255) not null,
	color varchar (255) not null,
    id_sku int,
    primary key (id_imei),
    foreign key (id_sku) references sku(id_sku)
);

```
