# Lab de Virtualización y Redes

Implementación de un entorno virtualizado con Oracle VirtualBox 7.2, utilizando Windows Server 2025 como Domain Controller y servidor de red, junto con dos clientes Windows 11 LTSC unidos al dominio.

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
    <td colspan="2" align="center">
      <img src="https://i.imgur.com/IavbFIA.png" width="85%">
      <br>
      <em>NICs del servidor y configuración IP de la NIC interna.</em>
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">
      <img src="https://i.imgur.com/gixQexu.png" width="85%">
      <br>
      <em>Activación de NAT en la NIC Externa.</em>
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">
      <img src="https://i.imgur.com/ZOCxQiA.png" width="85%">
      <br>
      <em>Verificación de las configuraciones de las NICs del server.</em>
    </td>
  </tr>
</table>

## Implementación de Servicios

- Instalación del rol **Active Directory Domain Services (AD DS)** en Windows Server 2025.
- Promoción del servidor a **Domain Controller** y creación del dominio `mydomain.com`.
- Configuración de **DNS** para la resolución de nombres dentro del dominio.
- Instalación y configuración de **DHCP**, incluyendo la creación del ámbito y la asignación automática de direcciones IP.

<table width="100%">
  <tr>
    <td align="center" width="42%">
      <img src="https://i.imgur.com/KVTHLg7.png" width="100%">
      <br>
      <em>Servidor promovido a DC y dominio creado.</em>
    </td>
    <td align="center" width="42%">
      <img src="https://i.imgur.com/QXH8Nep.png" width="100%">
      <br>
      <em>Zona DNS del dominio.</em>
    </td>
  </tr>
</table>

<table width="100%">
    <td align="center" width="42%">
      <img src="https://i.imgur.com/IpVttYK.png" width="100%">
      <br>
      <em>Creación del DHCP Scope.</em>
    </td>
    <td align="center" width="42%">
      <img src="https://i.imgur.com/bznJgXv.png" width="100%">
      <br>
      <em>Configuración de DHCP Options.</em>
    </td>
</table>

- Unión de los dos clientes Windows 11 LTSC al dominio.


## Habilidades Técnicas

VirtualBox · Windows Server · Active Directory · TCP/IP · DNS · DHCP · NAT · Network Troubleshooting
