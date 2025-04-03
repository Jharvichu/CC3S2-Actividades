# Actividad 2
A. Infrastructura como Código (IaC)

IaC es una forma de administrar y configurar una infrastructura de manera automatica a traves de scripts, en lugar de hacerlo de forma fisica. Utilizar IaC es un cambio de paradigma ya que permite reducir tiempo de trabajo, costes y errores asociados a la configuracion manual, ademas que permite automatizar la administracion de la infrastructura para que los desarrolladores no esten tan pendientes en administrar el entorno.

La infrastructura como codigo tiene algunas herramientas populares, como:

  1. Terraform: Es una herramienta de IaC que proporciona un flujo de trabajo de aprovisionamiento y gestion de infrastructura en cualquier nube mediante archivos declarativos en HCL.
  2. Ansible: Es una herramienta que permite gestion, configuracion de infrastructura a traves de archivos YAML.
  3. Pulumi: Es una herramienta de IaC que permite gestionar una infrastructura usando lenguajes de programacion convecionales como python o TypeScript
  4. AWS CloudFormation: Es un servicio de AWS que permite aprovisionar recursos en la nube, se usa lenguajes declarativos como JSON o YAML

En la implementacion de una infrastructura, el objetivo es no duplicar el trabajo o crear muchas plantillas con el mismo proposito, por eso los modulos de la infrastructura deben reutilizables, parametrizables y flexibles facilitando la gestion, escalabilidad y mantenimiento de la infrastructura.

Los modulos son configuraciones pequeñas y reurtilizables para multiples recursos de la infrastructura que se utilizan juntos. Un ejemplo de como se organizan los modulos en terraform es de la siguiente manera:

```plaintext
Project/
|── main.tf
|── variables.tf
|── outputs.tf
|── modulo/
|  |── network/
|  |  |── main.tf
|  |  |── variables.tf
|  |  |── outputs.tf
|  |── database/
|  |  |── main.tf
|  |  |── variables.tf
|  |  |── outputs.tf
|  |── application/
|  |  |── main.tf
|  |  |── variables.tf
|  |  |── outputs.tf
```
Se utiliza esta estructura ya que la separacion de modulos (network, database, application) facilita la reutilizacion del codigo, ademas que facilita el mantenimiento ya que cada modulo esa aislado.
