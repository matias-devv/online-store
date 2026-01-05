![Online Store Cover](./assets/onlinestore.png)

# 🛒 Online Store

## Descripción General

Este proyecto es una **tienda online de electrodomésticos** desarrollada utilizando una **arquitectura de microservicios**.  
Simula el backend de una plataforma de e-commerce real, permitiendo la gestión de usuarios, productos, carritos de compra y ventas.

El objetivo principal del proyecto es demostrar el diseño y la implementación de un **sistema distribuido**, aplicando buenas prácticas y patrones utilizados en entornos profesionales.

Este repositorio funciona como un **punto de entrada general** al sistema.  
Cada microservicio cuenta con su propio repositorio y documentación detallada.

> 📌 El proyecto corresponde exclusivamente al **backend** y se ejecuta en un **entorno local**.

---

## Arquitectura General

El sistema está compuesto por múltiples **microservicios independientes**, cada uno responsable de una capacidad de negocio específica y dueño de su propia base de datos.

Características principales de la arquitectura:
- Comunicación **100% REST**
- **Service Discovery & Registry** con Eureka
- **Configuración centralizada** mediante Spring Cloud Config Server
- **API Gateway** como punto de acceso único
- Patrón **Database per Service**
- Ejecución local mediante **Docker Compose**

![Architecture Diagram](./assets/arquitectura.png)

---

## Microservicios

| Microservicio | Responsabilidad | Repositorio |
|---------------|-----------------|-------------|
| users-service | Gestión de usuarios | 🔗 [link](https://github.com/matias-devv/online-store-users-service) |
| products-service | Catálogo de productos | 🔗 [link](https://github.com/matias-devv/online-store-products-service) |
| shopping-cart-service | Gestión de carritos de compra | 🔗 [link](https://github.com/matias-devv/online-store-shopping-carts-service) |
| sales-service | Procesamiento de ventas | 🔗 [link](https://github.com/matias-devv/online-store-sales-service) |
| api-gateway | Enrutamiento de solicitudes | 🔗 [link](https://github.com/matias-devv/online-store-api-gateway) |
| eureka-server | Registro y descubrimiento de servicios | 🔗 [link](https://github.com/matias-devv/online-store-eureka-server) |
| config-server | Configuración centralizada | 🔗 [link](https://github.com/matias-devv/online-store-config-server) |

Cada microservicio posee su propio repositorio con documentación técnica detallada.

---

## API Gateway

El **API Gateway** actúa como el **punto de entrada único** al sistema.

Funcionalidades actuales:
- Enrutamiento de URLs hacia los microservicios correspondientes
- Resolución de servicios a través de Eureka

Ejemplo de acceso:
http://localhost:8080/products-service/products/find-all


En esta etapa, el gateway se utiliza únicamente para enrutamiento, dejando abierta la posibilidad de futuras mejoras.

---

## Tecnologías Utilizadas

- **Java 17**
- **Spring Boot**
- **Spring Cloud**
  - Eureka Server
  - Config Server
  - API Gateway
- **REST APIs**
- **MySQL**
- **Docker & Docker Compose**

---

## Gestión de Configuración

La configuración de los microservicios se maneja de forma centralizada mediante **Spring Cloud Config Server**.

- Cada microservicio cuenta con su propio archivo de configuración en formato YAML
- La configuración se mantiene en un repositorio independiente
- Permite escalabilidad y consistencia entre servicios

---

## Ejecución Local

El sistema completo puede ejecutarse de manera local utilizando **Docker Compose**.

Este enfoque permite levantar toda la arquitectura de microservicios de forma integrada, incluyendo:

- API Gateway  
- Eureka Server (Service Discovery & Registry)  
- Config Server  
- Microservicios de negocio  
- Bases de datos asociadas a cada microservicio  

### Requisitos previos

- Docker
- Docker Compose

### Ejecución del sistema

Desde la raíz de este repositorio, ejecutar:

```bash
docker-compose up --build
