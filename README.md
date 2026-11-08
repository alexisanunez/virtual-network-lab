# Lab de Virtualización y Redes

Implementación de un entorno virtualizado con Oracle VirtualBox 7.2, utilizando Windows Server 2025 como Domain Controller y servidor de red, junto con dos clientes Windows 11 LTSC unidos al dominio.

![](https://i.imgur.com/QAACm60.png)

## Topología de Red

El servidor utiliza dos interfaces de red:
- **External:** conexión NAT para acceder a Internet y permitir conexión a Internet a los clientes mediante RRAS.
- **Internal** (IP asignada manualmente): comunicación con los clientes.

<p align="center">
  <img src="https://i.imgur.com/YfL6qjE.png" width="33%">
  <img src="https://i.imgur.com/jVbt82g.png" width="33%">
  <img src="https://i.imgur.com/x50ieja.png" width="33%">
</p>

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
