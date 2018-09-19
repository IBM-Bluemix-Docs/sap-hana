---



copyright:
  years: 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. Dimensionamiento del servidor
{: #size_the_server}

Después de decidir qué soluciones SAP tiene previsto utilizar, el siguiente paso consiste en determinar el número de {{site.data.keyword.baremetal_long}} que necesita para dar soporte a su entorno SAP y garantizar que los servidores estén correctamente dimensionados.
{: shortdesc}

## Descripción de la metodología de dimensionamiento de SAP
{: #size_method}

SAP HANA se ofrece en {{site.data.keyword.cloud_notm}} en configuraciones de un solo nodo con tamaños totales de RAM de 
  * 512 GB
  * 1024 GB (1 TB)
  * 2048 GB (2 TB)
  * 4096 GB (4 TB)
  * 8192 GB (8 TB)
  
Es una base de datos con columnas que suele requerir menos espacio para almacenar datos en comparación con un tradicional sistema de gestión de bases de datos relacionales (RDMS) basado en filas. Los datos se pueden comprimir mucho y la proporción de comprensión puede estar comprendida entre 3:1 y más de 10:1 en función de la base de datos y de los datos de origen. 

Debe dimensionar correctamente el servidor *antes* de adquirirlo, ya que el dimensionamiento es la clave del éxito del proyecto. Si se calcula mal la memoria o los requisitos de almacenamiento, será necesario realizar una actualización y migración a un servidor mayor.

## Acceso a SAP Quick Sizer
{: #quick_sizer}

La memoria principal es uno de los recursos más importantes que hay que tener en cuenta al calcular el tamaño de un dispositivo certificado de SAP HANA. El documento público [*SAP HANA Master Guide*](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf) constituye un punto de partida para consultar temas relacionados con el dimensionamiento. La información sobre [Dimensionamiento de SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) de la guía contiene instrucciones sobre cómo calcular el tamaño del sistema SAP HANA. Muestra distintos escenarios de instalación y migración para instalaciones no desarrolladas y para sistemas existentes. Contiene un enlace con la versión de SAP HANA de la herramienta SAP Quick Sizer (se necesita un ID de usuario de SAP S para acceder a la herramienta). La página también contiene las Notas de SAP relacionadas con el dimensionamiento del servidor SAP HANA. 

## Dimensionamiento de un entorno virtualizado
{: #size_virtual}

Para ver consideraciones adicionales sobre dimensionamiento al ejecutar SAP HANA en un entorno virtualizado, consulte el apartado [Despliegues de servidor VMware ESXi](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server) y el manual [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf).

## Siguientes pasos

 [5. Determinación de la configuración](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
