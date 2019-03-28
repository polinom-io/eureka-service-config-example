# Service Config

Este repositorio contiene las configuraciones centralizadas de los microservicios disponibles para genera

 service-config

Repository containing different service configuration examples to be used by Spring Config Server

Este repositorio contiene diferentes configuraciones de ejemplo para ser utilizadas con Spring Cloud Config Server. Dichas configuraciones pueden estar escritas en formato YAML `.yml` o como archivo de propiedades `.properties`

## Enabled configurations

* [eureka-service](eureka-service.yml): Servicio de registro y descubrimiento de servicios
* [integration-service](integration-service.yml): Cliente .NET Core utilizando Eureka

## Security Considerations

* [Encryption Decryption](https://cloud.spring.io/spring-cloud-config/single/spring-cloud-config.html#_encryption_and_decryption)

Spring Cloud config ofrece la posibilidad de encriptar y desencriptar información exponiendo dos endpoints `/encrypt` y `/decrypt`

* [Key Management](https://cloud.spring.io/spring-cloud-config/single/spring-cloud-config.html#_key_management)

Se recomienda la utilización de la variable de entorno `ENCRYPT_KEY` para habilitar la característica en el Servicio de Configuración Spring Cloud Config. La alternativa a este método implica la utilización de la propiedad `encryption.key` en el archivo `bootstrap.yml` , sin embargo debido a que esto involucra almacenar sin cifrar este valor en el archivo, se recomienda la alternativa con variable de entorno. Si no se realizan estos pasos, la respuesta de los endpoints de encriptacion arrojará algoritmo inválido.

**Caso Fallido:**

```
curl localhost:8888/encrypt -d mysecret
{"description":"The encryption algorithm is not strong enough","status":"INVALID"}
```
**Caso Exitoso:**

```
curl localhost:8888/encrypt -d mysecret
04275bf5f40e0f0cecbde6ef8798c57b9adb5e4d99f04ccbdc6f3cde56e7d790
```

## Referencias: 

1. [Spring Cloud Config Server](https://cloud.spring.io/spring-cloud-config/multi/multi__spring_cloud_config_server.html)