<div align="center">
<h1>Guía Técnica: Auditoría de Identidad</h1>
<h3>Despliegue de Entorno de Pruebas con HiddenEye + VTXHub</h3>
 
<br>
![Status](https://img.shields.io/badge/Estado-Completado-brightgreen?style=flat-square)
![Type](https://img.shields.io/badge/Tipo-Laboratorio%20Académico-4A90D9?style=flat-square)
![Tool](https://img.shields.io/badge/Herramienta-HiddenEye-CC2936?style=flat-square)
![Tunnel](https://img.shields.io/badge/Túnel-VTXHub%20%2F%20Vortex-7B2FBE?style=flat-square)
![Platform](https://img.shields.io/badge/OS-Kali%20Linux-557C94?style=flat-square)
 
<br>
<p><em>Laboratorio académico de ingeniería social y simulación de captura de credenciales.<br>
Entorno controlado, aislado y con fines exclusivamente educativos.</em></p>
</div>
<br>
> [!WARNING]
> Este repositorio documenta un procedimiento técnico desarrollado en un **entorno de laboratorio aislado**, con fines académicos y de investigación en ciberseguridad. El uso de estas técnicas fuera de un marco académico o profesional autorizado puede constituir un **delito informático** conforme a la legislación vigente. El autor no asume responsabilidad por usos indebidos.
 
<br>
## Tabla de Contenidos
 
- [1. Preparación del Entorno](#1-preparación-del-entorno)
- [2. Configuración de la Herramienta](#2-configuración-de-la-herramienta)
- [3. Parámetros de Simulación](#3-parámetros-de-simulación)
- [4. Integración con VTXHub y Vortex](#4-integración-con-vtxhub-y-vortex)
- [Conclusiones](#conclusiones)
<br>
---
 
## 1. Preparación del Entorno
 
La fase inicial consiste en preparar un entorno de trabajo **aislado y reproducible** para la ejecución de herramientas de auditoría. El uso de Git asegura la descarga de la versión más reciente del código desde el repositorio oficial.
 
| Paso | Descripción |
|:-----|:------------|
| **Clonación** | Descarga del repositorio con `git clone` desde la fuente oficial |
| **Entorno Virtual** | Aislamiento de dependencias con `venv` para evitar conflictos de versiones |
| **Instalación** | Carga de librerías requeridas dentro del entorno aislado |
 
<br>
### Clonar el repositorio
 
```bash
git clone https://gitlab.com/An0nUD4Y/hiddeneye.git
cd hiddeneye
```
 
<img src="Capturas - Hiddeneye/Clonacion de repositorio hiddeneye.png" alt="Clonación del repositorio" width="100%">
<sub><b>Figura 1</b> — Clonación del repositorio HiddenEye desde GitLab.</sub>
 
<br><br>
 
### Instalar dependencias
 
```bash
python3 -m venv venv
source venv/bin/activate
pip install requests
```
 
<img src="Capturas - Hiddeneye/Instalacion de dependencias HiddenEye.png" alt="Instalación de dependencias" width="100%">
<sub><b>Figura 2</b> — Instalación de dependencias dentro del entorno virtual.</sub>
 
<br>
---
 
## 2. Configuración de la Herramienta
 
Tras inicializar HiddenEye, la herramienta presenta su menú principal. Es **estrictamente necesario** aceptar los términos de uso ético antes de continuar.
 
```bash
sudo python3 HiddenEye.py
```
 
<br>
<img src="Capturas - Hiddeneye/Hiddeneye pagina de inicio.png" alt="Menú principal de HiddenEye" width="100%">
<sub><b>Figura 3</b> — Menú principal de HiddenEye con los módulos de simulación disponibles.</sub>
 
<br><br>
 
<img src="Capturas - Hiddeneye/Utilizar la herramienta solo para educacion.png" alt="Advertencia de uso ético" width="100%">
<sub><b>Figura 4</b> — Confirmación del disclaimer de seguridad y uso responsable.</sub>
 
<br>
### Módulos disponibles
 
- **Selección de objetivo** — Elegir el servicio a emular (`21` para Spotify en este laboratorio)
- **Plantilla estándar** — Página de inicio de sesión de alta fidelidad visual
- **Protecciones opcionales** — Técnicas de evasión ante medidas de seguridad del sitio objetivo
<br>
---
 
## 3. Parámetros de Simulación
 
En esta fase se definen los parámetros de recolección y el flujo de navegación del usuario objetivo dentro del entorno controlado.
 
<br>
### 3.1 Persistencia — Keylogger
 
Activación del **registro de pulsaciones en tiempo real**, permitiendo la captura de credenciales incluso antes de la confirmación del formulario.
 
<img src="Capturas - Hiddeneye/Añadir keylogger en phishing page Y.png" alt="Configuración del keylogger" width="100%">
<sub><b>Figura 5</b> — Activación del keylogger integrado en la página de phishing.</sub>
 
<br><br>
 
### 3.2 Redirección Post-Captura
 
Configuración de la **URL de destino final** hacia la que es redirigido el usuario tras interactuar, reduciendo la probabilidad de detección.
 
<img src="Capturas - Hiddeneye/Redirecting URL - En mi caso utilice spotify login.png" alt="Configuración de redirección" width="100%">
<sub><b>Figura 6</b> — Configuración de la URL de redirección al sitio legítimo de Spotify.</sub>
 
<br><br>
 
### 3.3 Despliegue Local
 
Definición del **puerto de red** e **interfaz de escucha** para el servidor de captura.
 
<img src="Capturas - Hiddeneye/Seleccionar puerto - yo uso 8080.png" alt="Selección de puerto" width="100%">
<sub><b>Figura 7</b> — Selección del puerto de escucha (<code>8080</code>).</sub>
 
<br><br>
 
<img src="Capturas - Hiddeneye/Host server selection - Local Host opcion 0.png" alt="Selección de host" width="100%">
<sub><b>Figura 8</b> — Selección del servidor local como método de despliegue (opción 0).</sub>
 
<br><br>
 
<img src="Capturas - Hiddeneye/LocalHost Server - 127.0.0.1.png" alt="Servidor localhost activo" width="100%">
<sub><b>Figura 9</b> — Servidor activo en <code>127.0.0.1:8080</code>.</sub>
 
<br><br>
 
<img src="Capturas - Hiddeneye/Login spotify - LocalHost8080.png" alt="Página de Spotify en localhost" width="100%">
<sub><b>Figura 10</b> — Página de inicio de sesión de Spotify simulada, accesible en <code>localhost:8080</code>.</sub>
 
<br>
---
 
## 4. Integración con VTXHub y Vortex
 
Para exponer el servicio hacia una red pública se utiliza **Vortex**, un cliente de túnel inverso que redirige el tráfico entrante desde un dominio público hacia el puerto local.
 
```
Internet  ──►  user3700dc4559ce41.app.vtxhub.com  ──►  127.0.0.1:8080
```
 
<br>
### 4.1 Obtención del Binario
 
```bash
unzip vortex.zip
chmod +x vortex
./vortex
```
 
<img src="Capturas - Hiddeneye/Instalar vortex shell - Descargar .zip.png" alt="Descarga de Vortex" width="100%">
<sub><b>Figura 11</b> — Descarga del archivo <code>vortex.zip</code> desde el panel de VTXHub.</sub>
 
<br><br>
 
### 4.2 Autenticación
 
<img src="Capturas - Hiddeneye/Iniciar sesion en vortex con correo temporal.png" alt="Login en Vortex" width="100%">
<sub><b>Figura 12</b> — Autenticación con correo temporal en el cliente Vortex.</sub>
 
<br><br>
 
<img src="Capturas - Hiddeneye/Iniciar sesion con el correo temporal en vortex despues de iniciarlo con .vortex.png" alt="Panel Vortex activo" width="100%">
<sub><b>Figura 13</b> — Panel de Vortex activo con el dominio público generado.</sub>
 
<br><br>
 
### 4.3 Despliegue y Verificación
 
| Parámetro | Valor |
|:----------|:------|
| **Host** | `127.0.0.1` |
| **Puerto** | `8080` |
| **Protocolo** | `http` |
| **Dominio público** | `user3700dc4559ce41.app.vtxhub.com` |
 
<br>
<img src="Capturas - Hiddeneye/Pagina de spotify ya en vortex.png" alt="Página Spotify en Vortex" width="100%">
<sub><b>Figura 14</b> — Página de Spotify simulada accesible vía dominio público de VTXHub.</sub>
 
<br><br>
 
<img src="Capturas - Hiddeneye/vortex redireccionamiento a internet..png" alt="Redireccionamiento Vortex" width="100%">
<sub><b>Figura 15</b> — Túnel activo: tráfico redirigido desde VTXHub hacia <code>127.0.0.1:8080</code>.</sub>
 
<br>
---
 
## Conclusiones
 
| Hallazgo | Implicación Defensiva |
|:---------|:----------------------|
| Alta fidelidad visual de las páginas clonadas | Verificar siempre la URL en la barra de direcciones |
| Keylogger pre-confirmación de formulario | Implementar autenticación multifactor (MFA) |
| Redirección transparente post-captura | Capacitar usuarios en detección de phishing |
| Exposición pública mediante túnel inverso | Monitorear dominios sospechosos y tráfico DNS |
 
<br>
---
 
<div align="center">
<sub>Laboratorio académico &nbsp;·&nbsp; Universidad Tecnológica de Panamá &nbsp;·&nbsp; Ciberseguridad III &nbsp;·&nbsp; 2026</sub>
</div>
 
