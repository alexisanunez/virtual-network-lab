# Lab de Virtualización y Redes

Implementación de un entorno virtualizado con Oracle VirtualBox 7.2, utilizando Windows Server 2025 como Domain Controller y servidor de infraestructura de red, junto con dos clientes Windows 11 LTSC unidos al dominio.

![](https://i.imgur.com/QAACm60.png)

## Entorno

- **Hypervisor:** Oracle VirtualBox 7.2
- **Server:** Windows Server 2025
- **Clients:** Windows 11 LTSC
- **Domain:** `mydomain.com`
- **Network Services:** AD DS, DHCP, RRAS/NAT, DNS

## Topología de Red

El servidor utiliza dos interfaces de red:

- **INTERNET-NIC:** conexión NAT para acceder a Internet y permitir la conexión de los clientes mediante RRAS.
- **VNETWORK-NIC:** interfaz con IP estática para la comunicación con los clientes.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/IavbFIA.png" width="100%">
      <br>
      <em>NICs del servidor y configuración IP de la NIC interna (VNETWORK-NIC).</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/gixQexu.png" width="100%">
      <br>
      <em>Configuración de NAT mediante RRAS para proporcionar acceso a Internet a los clientes (INTERNET-NIC).</em>
    </td>
  </tr>
</table>

- **Verificaciones:** ipconfig /all en el server para revisar las configuraciones de las NICs.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/ZOCxQiA.png" width="100%">
      <br>
      <em>Verificación de las configuraciones de las NICs del server.</em>
    </td>
  </tr>
</table>

## Implementación de Servicios

- Instalación del rol **Active Directory Domain Services (AD DS)** en Windows Server 2025.
- Promoción del servidor a **Domain Controller** y creación del dominio `mydomain.com`.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/KVTHLg7.png" width="100%">
      <br>
      <em>Servidor promovido a DC y dominio creado.</em>
    </td>
  </tr>
</table>

- Configuración de **DNS** para la resolución de nombres dentro del dominio.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/QXH8Nep.png" width="100%">
      <br>
      <em>Zona DNS del dominio.</em>
    </td>
  </tr>
</table>

- Instalación y configuración de **DHCP**, incluyendo la creación del ámbito y la asignación automática de direcciones IP.

<table width="100%" align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/IpVttYK.png" width="100%">
      <br>
      <em>Creación del DHCP Scope.</em>
    </td>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/bznJgXv.png" width="100%">
      <br>
      <em>Configuración de DHCP Options.</em>
    </td>
  </tr>
</table>

- Unión de los dos clientes Windows 11 LTSC al dominio.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/aX37irq.png" width="100%">
      <br>
      <em>Configuración de nombre y dominio del cliente.</em>
    </td>
  </tr>
</table>

- Verificaciones

<table width="100%" align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/rGxAtE3.png" width="100%">
      <br>
      <em>Adición de CLIENT1 al dominio y configuración IP automática (DHCP) exitosa.</em>
    </td>
  </tr>
</table>

<table width="100%" align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/mSBFj8T.png" width="100%">
      <br>
      <em>Conectividad y resolución DNS del DC desde CLIENT1.</em>
    </td>
  </tr>
</table>

<table width="100%" align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/VC8eIZb.png" width="100%">
      <br>
      <em>Conectividad y resolución DNS de CLIENT2 desde CLIENT1.</em>
    </td>
  </tr>
</table>

<table width="100%" align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://i.imgur.com/WmHIfvT.png" width="100%">
      <br>
      <em>Conectividad IP y resolución DNS externa - Conexión a Internet.</em>
    </td>
  </tr>
</table>

## Conclusiones y problemas encontrados en el lab

La verdad que fue una progresión bastante sencilla y no surgió ningún problema. Tengo bastante experiencia en instalación de sistemas operativos y configuración de redes así que no esperaba complicaciones mayores en esta sección. Tal vez podría haber añadido un PTR record para completar la configuración de DNS pero no lo veía tan necesario para este lab. Saludos!


