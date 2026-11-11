# Lab de Virtualización y Redes

Implementación de un entorno virtualizado utilizando Oracle VirtualBox 7.2, con Windows Server 2025 como controlador de dominio y servidor de infraestructura de red, junto con dos clientes Windows 11 LTSC unidos al dominio.

El laboratorio comprende la configuración de interfaces de red, virtualización de infraestructura, servicios de Active Directory, resolución de nombres mediante DNS, asignación dinámica de direcciones IP mediante DHCP y acceso a Internet mediante RRAS/NAT.

![](https://i.imgur.com/QAACm60.png)

## Entorno

- **Hypervisor:** Oracle VirtualBox 7.2
- **Server:** Windows Server 2025
- **Clients:** 2 × Windows 11 LTSC
- **Domain:** `mydomain.com`
- **Network Services:** AD DS, DNS, DHCP, RRAS/NAT

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/H1zv4bN.png" width="100%">
      <br>
      <em>Roles y servicios instalados en Windows Server 2025.</em>
    </td>
  </tr>
</table>

## Topología de Red

Se configuró una topología con un servidor que dispone de dos interfaces de red, separando la conexión externa de la red interna utilizada por los clientes.

- **INTERNET-NIC:** interfaz conectada a una red NAT de VirtualBox, utilizada como conexión externa para proporcionar acceso a Internet.
- **VNETWORK-NIC:** interfaz conectada a la red interna de VirtualBox, con direccionamiento IP estático, utilizada para la comunicación entre el servidor y los clientes.

El servidor utiliza RRAS para realizar NAT y permitir que los clientes accedan a Internet a través de la interfaz externa.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/IavbFIA.png" width="100%">
      <br>
      <em>Interfaces de red del servidor y configuración IP de la interfaz interna (VNETWORK-NIC).</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/gixQexu.png" width="100%">
      <br>
      <em>Configuración de RRAS/NAT, identificando INTERNET-NIC como interfaz pública.</em>
    </td>
  </tr>
</table>

### Verificación de la configuración de red

Se utilizó `ipconfig /all` para comprobar el direccionamiento IP, las interfaces de red y los parámetros de configuración del servidor.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/ZOCxQiA.png" width="100%">
      <br>
      <em>Verificación de las interfaces y parámetros de configuración IP del servidor.</em>
    </td>
  </tr>
</table>

## Implementación de Servicios de Red

### Active Directory Domain Services (AD DS)

Se instaló el rol **Active Directory Domain Services (AD DS)** y se promovió el servidor a **Domain Controller**, creando el dominio `mydomain.com`.

Este servicio centraliza la administración de identidades, equipos y recursos del entorno.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/KVTHLg7.png" width="100%">
      <br>
      <em>Servidor promovido a controlador de dominio y dominio mydomain.com creado.</em>
    </td>
  </tr>
</table>

### Domain Name System (DNS)

Se configuró DNS para proporcionar resolución de nombres dentro del dominio, permitiendo que los equipos localicen los servicios y recursos de Active Directory.

Se verificó la creación de la zona de búsqueda directa correspondiente al dominio.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/QXH8Nep.png" width="100%">
      <br>
      <em>Zona de búsqueda directa correspondiente al dominio mydomain.com.</em>
    </td>
  </tr>
</table>

### Dynamic Host Configuration Protocol (DHCP)

Se instaló y configuró el rol DHCP para asignar automáticamente parámetros de red a los clientes.

La configuración incluyó:

- Creación del ámbito (Scope) de direcciones IP.
- Definición del rango de direcciones disponibles.
- Configuración de las opciones del ámbito (Scope Options), incluyendo gateway y servidor DNS.
- Asignación dinámica de parámetros de red a los clientes.

<table width="100%" align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/IpVttYK.png" width="100%">
      <br>
      <em>Creación y configuración del ámbito DHCP.</em>
    </td>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/bznJgXv.png" width="100%">
      <br>
      <em>Configuración de las opciones del ámbito (Scope Options).</em>
    </td>
  </tr>
</table>

## Configuración de Clientes

Se configuraron dos máquinas virtuales con Windows 11 LTSC, conectadas a la red interna y configuradas para obtener automáticamente sus parámetros de red mediante DHCP.

Posteriormente, ambos equipos se incorporaron al dominio `mydomain.com`.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/aX37irq.png" width="100%">
      <br>
      <em>Configuración del nombre del equipo y unión al dominio.</em>
    </td>
  </tr>
</table>

## Verificaciones de Conectividad

Se realizaron pruebas desde los clientes para comprobar el funcionamiento de los servicios implementados.

Las verificaciones incluyeron:

- Obtención automática de parámetros de red mediante DHCP.
- Conectividad con el controlador de dominio.
- Resolución DNS de nombres internos.
- Comunicación entre los clientes.
- Acceso a Internet a través de RRAS/NAT.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/rGxAtE3.png" width="100%">
      <br>
      <em>Verificación de la incorporación de CLIENT1 al dominio y obtención automática de parámetros IP mediante DHCP.</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/mSBFj8T.png" width="100%">
      <br>
      <em>Verificación de conectividad y resolución DNS del controlador de dominio desde CLIENT1.</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/VC8eIZb.png" width="100%">
      <br>
      <em>Verificación de conectividad y resolución DNS de CLIENT2 desde CLIENT1.</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/WmHIfvT.png" width="100%">
      <br>
      <em>Verificación de conectividad IP y resolución DNS externa mediante acceso a Internet.</em>
    </td>
  </tr>
</table>

## Conclusiones y consideraciones

Tengo bastante experiencia en instalación de sistemas operativos y configuración de redes, así que no esperaba tener problemas mayores en este lab.

El laboratorio permitió implementar una infraestructura virtualizada funcional, integrando servicios de directorio, resolución de nombres, asignación dinámica de direcciones IP y enrutamiento con NAT.

Durante las pruebas se verificó la comunicación entre los equipos, la resolución de nombres internos y externos, la obtención automática de parámetros de red y el acceso a Internet desde los clientes.

Como posible mejora, se podría incorporar una zona de búsqueda inversa en DNS y sus correspondientes registros PTR, complementando la resolución de nombres directa implementada.

Este entorno constituye la base para el siguiente laboratorio, en el que se profundiza en la administración de usuarios, grupos, directivas de grupo, automatización con PowerShell y permisos sobre recursos compartidos.

---

**Próximo laboratorio:** [Active Directory Administration Lab](https://github.com/alexisanunez/active-directory-adm-lab)
