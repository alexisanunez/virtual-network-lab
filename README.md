# Lab de Virtualización y Redes

Implementación de un entorno virtualizado con Oracle VirtualBox 7.2, utilizando Windows Server 2025 como Domain Controller y servidor de red, junto con dos clientes Windows 11 LTSC unidos al dominio.

![](https://i.imgur.com/QAACm60.png)

## Topología de Red

El servidor utiliza dos interfaces de red:

- **External:** conexión NAT para acceder a Internet y permitir la conexión de los clientes mediante RRAS.
- **Internal:** interfaz con IP estática para la comunicación con los clientes.

<table width="100%" align="center">
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/YfL6qjE.png" width="85%">
      <br>
      <em>Ambas NICs del servidor vistas en la GUI.</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/jVbt82g.png" width="85%">
      <br>
      <em>Configuración de la NIC externa.</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://i.imgur.com/x50ieja.png" width="85%">
      <br>
      <em>Configuración de la NIC interna.</em>
    </td>
  </tr>
</table>

## Implementación

- Creación y configuración de máquinas virtuales.
- Configuración de redes NAT e Internal Network.
- Instalación de Active Directory Domain Services (AD DS).
- Creación del dominio y unión de los clientes.
- Configuración de DNS, DHCP y NAT.

## Validación

- Verificación de la asignación automática de direcciones IP mediante DHCP.
- Pruebas de resolución DNS.
- Comprobación de conectividad entre equipos.
- Verificación del acceso a Internet desde los clientes.

## Habilidades Técnicas

VirtualBox · Windows Server · Active Directory · TCP/IP · DNS · DHCP · NAT · Network Troubleshooting
