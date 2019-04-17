---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-28"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, infrastructure, {{site.data.keyword.baremetal_short}}, SAP-certified infrastructure, deployment, BYOL,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 2. Configuración de la infraestructura
{: #set_up_infrastructure}

En la siguiente sección se describe cómo configurar los {{site.data.keyword.baremetal_long}} de SAP HANA, red, seguridad, almacenamiento y sistema operativo. Póngase en contacto con el [Soporte de {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) si tiene alguna pregunta.

## Realización del pedido de servidor
{: order-server}

Utilice los siguientes pasos para realizar el pedido de {{site.data.keyword.baremetal_short}}. Encontrará información adicional en [Creación de un servidor nativo personalizado](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server).

1. Inicie sesión en el [portal de clientes de la infraestructura de {{site.data.keyword.cloud_notm}} ![Icono de enlaceexterno](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com){: new_window} con sus credenciales exclusivas.

2. Pulse **Cuenta** > **Realizar un pedido** en la página Resumen de la cuenta.
3. Pulse el enlace **Mensual** en {{site.data.keyword.baremetal_short}} en la página Dispositivos. Aparecerá la lista de servidores; los servidores certificados por SAP están en la parte superior de la lista.
4. Pulse el hiperenlace de **Precio inicial al mes** para seleccionar el servidor adecuado y pasar a la página de configuración y pedido. Los servidores certificados por SAP HANA se identifican con **-H** bajo el Modelo de CPU.  

Los servidores BI.S3.H2192 y BI.S3.H238 también están disponibles para la facturación **por horas**.
{: note}

5. Escriba el número de servidores del pedido que realiza en el campo **Cantidad** y seleccione su **Centro de datos**.
6. Las opciones de **Servidor**, **RAM** y almacenamiento privado se establecen de forma predeterminada en función de la selección de servidor y no se pueden modificar. El pedido de {{site.data.keyword.blockstorageshort}} de {{site.data.keyword.IBM_notm}} para {{site.data.keyword.cloud_notm}} o {{site.data.keyword.filestorage_full_notm}} y el almacenamiento adjunto en red (NAS) se realiza después del pedido de servidor.
7. Seleccione el **Sistema operativo** de Red Hat o SUSE y seleccione el sistema operativo específico o hipervisor VMware para su servidor.

Si trae su propia licencia (BYOL) para el sistema operativo, seleccione **Otro** > **Sin sistema operativo**. Para obtener más información, consulte [Traiga su propia licencia](#byol).
{ :note}

## Selección de las opciones de servidor
{: #select_options}

En el siguiente paso, seleccionará el tipo y el número de discos que desea añadir a la configuración. También puede seleccionar distintas opciones para grupos de almacenamiento de RAID (matriz redundante de discos independientes) y diseños de particiones sobre grupos de almacenamiento de RAID. Para obtener más información, consulte [Acerca de RAID](/docs/bare-metal?topic=bare-metal-about-raid#about-raid) o
[Soporte de {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

1. En **Servidores certificados de SAP**, realice la selección sobre la base de cómo tenga previsto utilizar el servidor. Consulte la herramienta [Design Decision Tool
![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool){: new_window} (desplácese hacia abajo hasta la herramienta) o
[Soporte de {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) para obtener más información
2. Pulse **Añadir a pedido** en la parte inferior de la página.

## Ajuste de las configuraciones avanzadas del sistema
{: #adv_config}

1. Siga las directrices de [Configuración avanzada del sistema](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server) para obtener ayuda con los valores de la ventana **Configuración avanzada del sistema**.

Los nombres de host de SAP deben constar de un máximo de 13 caracteres alfanuméricos. Para obtener más información sobre el nombre de host SAP, consulte [Notas de SAP 611361 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/611361){: new_window} y
[129997 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/129997){: new_window}.

## Confirmación de las selecciones
{: #confirm_selections}

1. Confirme las selecciones en la página de pago y marque **Términos de los servicios en la nube** y **Acuerdo de software de terceros**.
2. Desplácese a Crear cuenta: Datos de facturación y especifique el **Tipo de pago, Nombre, Tarjeta** y **Vencimiento** (fecha) de la tarjeta de crédito que se utilizará para la facturación.
3. Pulse **Enviar pedido**. Se le redirigirá a una página con el número de pedido. Puede imprimir la página, ya que también es su recibo del pedido.

Se le enviará un correo electrónico de confirmación con el asunto _Se ha aprobado el pedido número ## de {{site.data.keyword.cloud_notm}}_ a la dirección de correo electrónico de su perfil. Este correo electrónico es un aviso de que el servidor ha sido aprobado y está en proceso de ser desplegado. Una vez desplegado, se envía otro aviso notificando que el servidor está disponible y puede gestionarse a través del [portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}}
![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com){: new_window}.

## Traiga su propia licencia
{: #byol}

Si tiene su propia licencia del sistema operativo, instálelo en el {{site.data.keyword.baremetal_short}} según las instrucciones del proveedor. Para obtener más información, consulte [La opción sin SO](/docs/bare-metal?topic=bare-metal-bm-no-os#bm-no-os).

## Siguientes pasos

Ahora está listo para empezar a gestionar los {{site.data.keyword.baremetal_short}}. Consulte [Gestión del entorno SAP HANA](/docs/infrastructure/sap-hana?topic=sap-hana-manage_environment#manage_environment) para conocer los pasos a seguir.
