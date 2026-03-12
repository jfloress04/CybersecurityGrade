<div align="center">

<!-- BANNER VISUAL -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1a1f2e,100:00ff88&height=200&section=header&text=Linux%20Hardening%20/%20Bastionado%20Linux&fontSize=34&fontColor=00ff88&fontAlignY=38&desc=Hardening%20de%20Sistemas%20Linux%20para%20Ciberseguridad&descAlignY=58&descSize=16&descColor=8b949e" width="100%"/>

<!-- LANGUAGE TOGGLE -->
<a href="#english-version">
  <img src="https://img.shields.io/badge/🇬🇧_English-Read%20in%20English-0d6efd?style=for-the-badge&labelColor=0d1117"/>
</a>
&nbsp;
<a href="#version-espanol">
  <img src="https://img.shields.io/badge/🇪🇸_Español-Leer%20en%20Español-dc3545?style=for-the-badge&labelColor=0d1117"/>
</a>

<br/><br/>

<!-- BADGES -->
![Platform](https://img.shields.io/badge/Domain-System%20Security-557C94?style=flat-square&logo=linux&logoColor=white)
![Category](https://img.shields.io/badge/Category-Linux%20Hardening-00ff88?style=flat-square&logo=shieldsdotio&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)
![Framework](https://img.shields.io/badge/Framework-SSH%20%7C%20UFW%20%7C%20AIDE%20%7C%20Lynis-blueviolet?style=flat-square&logo=bookstack&logoColor=white)
![Lang](https://img.shields.io/badge/Lang-EN%20%7C%20ES-orange?style=flat-square)

</div>

---

<!-- ============================================================ -->
<!--                     ENGLISH VERSION                          -->
<!-- ============================================================ -->

<a name="english-version"></a>

<div align="center">
<h1>🔒 Task 2 — Topic 1: Linux System Hardening</h1>
<p><i>Hardening of Linux Systems Following Security Hardening Policy Guidelines</i></p>
</div>

### 📋 Overview

> **Linux System Hardening** is a comprehensive set of security measures applied to Linux operating systems to increase their resilience against cyber threats and unauthorised access. In an accelerating digital landscape, securing the infrastructure layer is paramount for any organisation handling sensitive data or critical services. This practical exercise covers the implementation of industry-standard hardening techniques aligned with security best practices and regulatory compliance frameworks.

---

### 🖥️ Project Profile

<div align="center">

| Parameter | Value |
|:---:|:---:|
| 🖥️ System | `Linux (Debian/Ubuntu-based)` |
| 🎯 Objective | `Maximum security hardening` |
| 💼 Scope | `Server infrastructure protection` |
| ⚠️ Context | `Production-ready · Compliance-driven · Zero-trust` |
| 📋 Deliverable | `Comprehensive Linux Hardening Guide` |

</div>

---

### 🎯 Objectives

- [x] Implement secure user and password management practices
- [x] Configure SSH for secure remote access with cryptographic authentication
- [x] Deploy automatic security updates to maintain patch compliance
- [x] Establish firewall rules using UFW (Uncomplicated Firewall)
- [x] Enforce strong password policies using libpam-pwquality
- [x] Monitor file integrity with AIDE (Advanced Intrusion Detection Environment)
- [x] Disable unnecessary services and kernel modules to reduce attack surface
- [x] Conduct comprehensive security audits using Lynis
- [x] Validate hardening measures through security testing

---

### 🔐 The Eight Hardening Pillars

<details>
<summary><b>Pillar 1 — User and Password Management</b></summary>
<br/>

> [!IMPORTANT]
> **Implement the principle of least privilege** — users should only have the minimum permissions required to perform their tasks.

**Key actions for Linux hardening:**

- Create non-root user accounts for daily administrative tasks
- Disable the root account or restrict its access strictly
- Implement sudo with granular permission controls
- Audit user accounts and remove unnecessary system accounts
- Monitor and log all administrative access
- Enforce password complexity and expiration policies
- Secure sensitive files (/etc/passwd, /etc/shadow, /etc/sudoers)

**Tools:**
```bash
useradd, userdel, usermod, sudo, lastlog, w, audit
```

</details>

<details>
<summary><b>Pillar 2 — SSH Secure Configuration</b></summary>
<br/>

> [!IMPORTANT]
> **SSH is the critical entry point** — misconfigurations can expose the entire system. Secure it with cryptographic keys and restrictive policies.

**Key actions for Linux hardening:**

- Change SSH port from default 22 to a non-standard port
- Disable root login via SSH (`PermitRootLogin no`)
- Implement public key authentication (RSA 4096-bit or Ed25519)
- Disable password authentication (`PasswordAuthentication no`)
- Configure session timeouts to prevent idle connections
- Restrict SSH access by user/group (`AllowUsers` / `AllowGroups`)
- Deploy SSH banners for legal warnings
- Integrate Fail2ban for brute-force attack prevention
- Enable verbose logging for audit trails
- Configure strong cipher suites (AES-256-GCM, ChaCha20)

**Key configuration (sshd_config):**
```bash
Port 2222
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
X11Forwarding no
MaxAuthTries 3
ClientAliveInterval 300
ClientAliveCountMax 0
```

</details>

<details>
<summary><b>Pillar 3 — Automatic Security Updates</b></summary>
<br/>

> [!IMPORTANT]
> **Patches are your first line of defence** — vulnerability disclosures happen constantly. Automate updates to ensure zero-day risk mitigation.

**Key actions for Linux hardening:**

- Enable unattended-upgrades for automatic security patches
- Configure automatic kernel updates with safe restart policies
- Subscribe to security repositories (Debian-security, Ubuntu-security)
- Set up email notifications for failed or problematic updates
- Test updates in a staging environment first
- Define maintenance windows for non-critical updates
- Monitor update logs and verify successful installations
- Implement rollback procedures for failed updates

**Key configuration (apt):**
```bash
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
Unattended-Upgrade::Automatic-Reboot "true";
Unattended-Upgrade::Automatic-Reboot-Time "03:00";
```

</details>

<details>
<summary><b>Pillar 4 — Firewall Configuration (UFW)</b></summary>
<br/>

> [!IMPORTANT]
> **Default-deny, explicit-allow** — the firewall should reject all traffic by default and only permit what is explicitly needed.

**Key actions for Linux hardening:**

- Enable UFW and set default policy: DENY incoming, ALLOW outgoing
- Open only essential ports (SSH, HTTP/HTTPS if applicable)
- Implement stateful firewall rules (SYN-only, established connections)
- Use UFW application profiles for predefined service rules
- Restrict access by source IP when possible
- Implement rate limiting to prevent DoS attacks
- Enable UFW logging to audit firewall decisions
- Regularly review and remove unused rules
- Configure IPv6 firewall rules separately
- Integrate with Fail2ban for dynamic blocking

**Key rules:**
```bash
ufw default deny incoming
ufw default allow outgoing
ufw allow 2222/tcp    # SSH on custom port
ufw allow 80/tcp      # HTTP (if needed)
ufw allow 443/tcp     # HTTPS (if needed)
```

</details>

<details>
<summary><b>Pillar 5 — Password Policy Enforcement (PAM-PWQuality)</b></summary>
<br/>

> [!IMPORTANT]
> **Strong passwords are non-negotiable** — implement libpam-pwquality to enforce complexity, length, and history requirements.

**Key actions for Linux hardening:**

- Install and configure libpam-pwquality
- Define minimum password length (14+ characters recommended)
- Require character diversity: uppercase, lowercase, digits, symbols
- Prevent password reuse (history check)
- Set password expiration policies (90 days for privileged users)
- Implement account lockout after failed login attempts
- Use real-time password validation
- Exclude privileged accounts (e.g., root) from certain restrictions if necessary
- Audit all password changes and failed login attempts
- Test policies regularly to ensure effectiveness

**Key configuration (common-password):**
```bash
password requisite pam_pwquality.so retry=3 minlen=14 dcredit=-1 ucredit=-1 lcredit=-1 ocredit=-1
password [success=1 default=ignore] pam_unix.so obscure use_authtok try_first_pass yescrypt sha512 rounds=5000
password requisite pam_deny.so
password required pam_permit.so
password required pam_unix.so remember=5 use_authtok try_first_pass yescrypt
```

</details>

<details>
<summary><b>Pillar 6 — File Integrity Monitoring (AIDE)</b></summary>
<br/>

> [!IMPORTANT]
> **Detect tampering early** — AIDE continuously monitors system files for unauthorised modifications, alerting administrators to potential breaches.

**Key actions for Linux hardening:**

- Install AIDE and create an initial baseline database
- Configure AIDE rules to monitor critical system files
- Define a monitoring schedule (daily, weekly, or real-time)
- Generate integrity reports and alerts on changes
- Investigate all critical file modifications immediately
- Store AIDE database and reports offsite or read-only
- Exclude temporary files and log directories
- Optimise database size for performance
- Integrate AIDE with centralised logging (SIEM)
- Implement automated response to detected changes

**Key configuration (aide.conf):**
```bash
/bin			R+b+sha512
/sbin			R+b+sha512
/usr/bin		R+b+sha512
/usr/sbin		R+b+sha512
/lib			R+b+sha512
/lib64			R+b+sha512
/etc			R+b+sha512
!/etc/ssl/private
!/var/log
!/var/cache
```

</details>

<details>
<summary><b>Pillar 7 — Disable Unnecessary Services & Kernel Modules</b></summary>
<br/>

> [!IMPORTANT]
> **Reduce attack surface** — every service running is a potential vulnerability. Disable anything not explicitly required.

**Key actions for Linux hardening:**

- Audit all installed packages and running services
- Document which services are essential for operations
- Disable unnecessary daemons (cups, avahi, bluetooth, etc.)
- Disable unnecessary kernel modules (USB, firewire, bluetooth, etc.)
- Use systemctl to mask services permanently
- Blacklist kernel modules in /etc/modprobe.d/
- Test functionality after each removal
- Maintain a change log for rollback purposes
- Monitor system performance post-hardening
- Verify no critical dependencies are broken

**Common services to disable:**
```
cups (printing)
avahi-daemon (mDNS)
bluetooth
iscsid (iSCSI)
rpcbind (NFS)
snmpd (SNMP)
```

**Common kernel modules to disable:**
```
usb-storage
firewire
bluetooth
binfmt_misc (optional)
```

</details>

<details>
<summary><b>Pillar 8 — Comprehensive Security Audit (Lynis)</b></summary>
<br/>

> [!IMPORTANT]
> **Measure to improve** — Lynis provides a holistic security assessment, identifying gaps and prioritising remediation efforts.

**Key actions for Linux hardening:**

- Install Lynis from official repositories
- Run full system audit in detailed mode
- Review all warnings, suggestions, and informational findings
- Calculate Hardening Index score (higher is better)
- Address critical and high-priority findings first
- Schedule quarterly or bi-annual Lynis audits
- Track Hardening Index improvement over time
- Integrate Lynis into CI/CD pipelines for baseline validation
- Generate audit reports for management and compliance
- Use Lynis output to validate implementation of hardening measures

**Lynis audit command:**
```bash
sudo lynis audit system --quiet --quick
sudo lynis audit system --forensics
sudo lynis generate report
```

</details>

---

### 📂 Document Structure

```
TAREA-2-TEMA-1-Bastionado-Linux/
├── 📄 README.md                                ←  This document
├── 📂 1-Introduccion/
│   ├── introduction_hardening.md
│   └── key_concepts.md
├── 📂 2-Gestion-Usuarios-Contrasenas/
│   ├── user_management.md
│   ├── password_policy.md
│   └── scripts_usuarios.sh
├── 📂 3-Configuracion-SSH/
│   ├── ssh_hardening.md
│   ├── sshd_config_seguro
│   └── ssh_banner.txt
├── 📂 4-Actualizaciones-Automaticas/
│   ├── automatic_updates.md
│   └── unattended_upgrades.conf
├── 📂 5-Cortafuegos-UFW/
│   ├── ufw_configuration.md
│   └── ufw_rules.sh
├── 📂 6-PAM-PWQuality/
│   ├── pam_pwquality_setup.md
│   └── common_password_config
├── 📂 7-AIDE/
│   ├── aide_installation.md
│   ├── aide.conf
│   └── verify_integrity.sh
├── 📂 8-Desactivacion-Servicios/
│   ├── services_to_disable.md
│   └── disable_services.sh
├── 📂 9-Lynis/
│   ├── lynis_guide.md
│   └── lynis_audit.sh
└── 📂 10-Scripts-Automatizacion/
    ├── hardening_complete.sh
    └── security_verification.sh
```

---

### 📖 Key Concepts

> [!NOTE]
> **Hardening** — The process of configuring an operating system or application with security best practices to reduce vulnerabilities and attack surface.

> [!NOTE]
> **Principle of Least Privilege** — Users and services should only have the minimum permissions necessary to perform their intended functions.

> [!NOTE]
> **SSH (Secure Shell)** — Cryptographic network protocol for secure remote login and command execution, replacing insecure protocols like Telnet.

> [!NOTE]
> **UFW (Uncomplicated Firewall)** — A user-friendly interface to iptables, designed to simplify firewall configuration on Linux systems.

> [!NOTE]
> **AIDE (Advanced Intrusion Detection Environment)** — File integrity monitoring tool that detects unauthorised modifications to system files.

> [!NOTE]
> **Lynis** — Comprehensive security auditing tool that identifies vulnerabilities and misconfigurations in Linux systems.

---

### ✅ Expected Deliverables

A complete Linux hardening implementation must include:
- ✅ Secure user and password management configuration
- ✅ SSH hardened configuration with key-based authentication
- ✅ Automatic security update mechanism activated
- ✅ UFW firewall with restrictive rulesets deployed
- ✅ PAM-PWQuality password policy enforced
- ✅ AIDE baseline database created and monitoring active
- ✅ Unnecessary services and modules disabled with documentation
- ✅ Lynis audit completed with Hardening Index score
- ✅ Security testing validation results
- ✅ Comprehensive documentation and runbooks

---

### ⚠️ Important Notes

- **Test in a non-production environment first** — hardening changes can impact functionality
- **Maintain physical or console access** — avoid being locked out of SSH
- **Document all changes** — enable easy rollback if issues arise
- **Automate where possible** — use scripts to ensure consistency across multiple systems
- **Monitor continuously** — hardening is not a one-time activity; adapt to new threats
- **Compliance matters** — ensure hardening aligns with RGPD, ENS, and ISO 27001 requirements

---

---

<!-- ============================================================ -->
<!--                    VERSIÓN EN ESPAÑOL                        -->
<!-- ============================================================ -->

<a name="version-espanol"></a>

<div align="center">
<h1>🔒 Tarea 2 — Tema 1: Bastionado de Sistemas Linux</h1>
<p><i>Bastionado de Sistemas Linux siguiendo Guías de Políticas de Segurización</i></p>
</div>

### 📋 Descripción General

> **Bastionado de Sistemas Linux** es un conjunto integral de medidas de seguridad aplicadas a sistemas operativos Linux para aumentar su resiliencia frente a amenazas cibernéticas y acceso no autorizado. En un panorama digital acelerado, asegurar la capa de infraestructura es fundamental para cualquier organización que maneje datos sensibles o servicios críticos. Este ejercicio práctico cubre la implementación de técnicas de bastionado alineadas con las mejores prácticas de seguridad y marcos normativos de cumplimiento.

---

### 🖥️ Perfil del Proyecto

<div align="center">

| Parámetro | Valor |
|:---:|:---:|
| 🖥️ Sistema | `Linux (basado en Debian/Ubuntu)` |
| 🎯 Objetivo | `Máxima seguridad de bastionado` |
| 💼 Alcance | `Protección de infraestructura de servidores` |
| ⚠️ Contexto | `Listo para producción · Cumplimiento normativo · Zero-trust` |
| 📋 Entregable | `Guía Completa de Bastionado Linux` |

</div>

---

### 🎯 Objetivos

- [x] Implementar prácticas seguras de gestión de usuarios y contraseñas
- [x] Configurar SSH para acceso remoto seguro con autenticación criptográfica
- [x] Desplegar actualizaciones automáticas de seguridad para mantener cumplimiento de parches
- [x] Establecer reglas de cortafuegos usando UFW (Uncomplicated Firewall)
- [x] Reforzar políticas de contraseña usando libpam-pwquality
- [x] Monitorear integridad de ficheros con AIDE (Advanced Intrusion Detection Environment)
- [x] Desactivar servicios y módulos innecesarios para reducir superficie de ataque
- [x] Realizar auditorías exhaustivas de seguridad usando Lynis
- [x] Validar medidas de bastionado mediante pruebas de seguridad

---

### 🔐 Los Ocho Pilares de Bastionado

<details>
<summary><b>Pilar 1 — Gestión de Usuarios y Contraseñas</b></summary>
<br/>

> [!IMPORTANT]
> **Implementar el principio de mínimo privilegio** — los usuarios deben tener solo los permisos mínimos necesarios para realizar sus tareas.

**Acciones clave para bastionado Linux:**

- Crear cuentas de usuario no-root para tareas administrativas diarias
- Desactivar la cuenta root o restringir su acceso estrictamente
- Implementar sudo con controles de permisos granulares
- Auditar cuentas de usuario y eliminar cuentas del sistema innecesarias
- Monitorear y registrar todos los accesos administrativos
- Enforcer políticas de complejidad y expiración de contraseña
- Asegurar ficheros sensibles (/etc/passwd, /etc/shadow, /etc/sudoers)

**Herramientas:**
```bash
useradd, userdel, usermod, sudo, lastlog, w, audit
```

</details>

<details>
<summary><b>Pilar 2 — Configuración Segura de SSH</b></summary>
<br/>

> [!IMPORTANT]
> **SSH es el punto de entrada crítico** — las misconfigurations pueden exponer todo el sistema. Asegúralo con claves criptográficas y políticas restrictivas.

**Acciones clave para bastionado Linux:**

- Cambiar puerto SSH del 22 por defecto a un puerto no estándar
- Desactivar login root vía SSH (`PermitRootLogin no`)
- Implementar autenticación por clave pública (RSA 4096-bit o Ed25519)
- Desactivar autenticación por contraseña (`PasswordAuthentication no`)
- Configurar timeouts de sesión para prevenir conexiones idle
- Restringir acceso SSH por usuario/grupo (`AllowUsers` / `AllowGroups`)
- Desplegar banners SSH para advertencias legales
- Integrar Fail2ban para prevención de ataques de fuerza bruta
- Habilitar logging detallado para auditoría
- Configurar suites de cifrado fuertes (AES-256-GCM, ChaCha20)

**Configuración clave (sshd_config):**
```bash
Port 2222
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
X11Forwarding no
MaxAuthTries 3
ClientAliveInterval 300
ClientAliveCountMax 0
```

</details>

<details>
<summary><b>Pilar 3 — Actualizaciones Automáticas de Seguridad</b></summary>
<br/>

> [!IMPORTANT]
> **Los parches son tu primera línea de defensa** — las divulgaciones de vulnerabilidades ocurren constantemente. Automatiza actualizaciones para mitigar riesgo zero-day.

**Acciones clave para bastionado Linux:**

- Habilitar unattended-upgrades para parches de seguridad automáticos
- Configurar actualizaciones automáticas del kernel con políticas de reinicio seguro
- Suscribirse a repositorios de seguridad (Debian-security, Ubuntu-security)
- Configurar notificaciones por correo electrónico para fallos o actualizaciones problemáticas
- Probar actualizaciones en entorno de staging primero
- Definir ventanas de mantenimiento para actualizaciones no críticas
- Monitorear logs de actualización y verificar instalaciones exitosas
- Implementar procedimientos de rollback para actualizaciones fallidas

**Configuración clave (apt):**
```bash
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
Unattended-Upgrade::Automatic-Reboot "true";
Unattended-Upgrade::Automatic-Reboot-Time "03:00";
```

</details>

<details>
<summary><b>Pilar 4 — Configuración de Cortafuegos (UFW)</b></summary>
<br/>

> [!IMPORTANT]
> **Default-deny, explicit-allow** — el cortafuegos debe rechazar todo tráfico por defecto y solo permitir lo explícitamente necesario.

**Acciones clave para bastionado Linux:**

- Habilitar UFW y establecer política por defecto: DENY entrada, ALLOW salida
- Abrir solo puertos esenciales (SSH, HTTP/HTTPS si aplica)
- Implementar reglas de cortafuegos stateful (SYN-only, conexiones establecidas)
- Usar perfiles de aplicación UFW para reglas predefinidas
- Restringir acceso por IP de origen cuando sea posible
- Implementar rate limiting para prevenir ataques DoS
- Habilitar logging de UFW para auditar decisiones del cortafuegos
- Revisar regularmente y eliminar reglas no utilizadas
- Configurar reglas de cortafuegos IPv6 por separado
- Integrar con Fail2ban para bloqueo dinámico

**Reglas clave:**
```bash
ufw default deny incoming
ufw default allow outgoing
ufw allow 2222/tcp    # SSH en puerto custom
ufw allow 80/tcp      # HTTP (si es necesario)
ufw allow 443/tcp     # HTTPS (si es necesario)
```

</details>

<details>
<summary><b>Pilar 5 — Enforcing Políticas de Contraseña (PAM-PWQuality)</b></summary>
<br/>

> [!IMPORTANT]
> **Las contraseñas fuertes son innegociables** — implementa libpam-pwquality para enforcer requisitos de complejidad, longitud e historial.

**Acciones clave para bastionado Linux:**

- Instalar y configurar libpam-pwquality
- Definir longitud mínima de contraseña (14+ caracteres recomendados)
- Requerir diversidad de caracteres: mayúsculas, minúsculas, dígitos, símbolos
- Prevenir reutilización de contraseñas (verificación de historial)
- Establecer políticas de expiración de contraseña (90 días para usuarios privilegiados)
- Implementar bloqueo de cuenta tras intentos de login fallidos
- Usar validación de contraseña en tiempo real
- Excluir cuentas privilegiadas (ej. root) de ciertas restricciones si es necesario
- Auditar todos los cambios de contraseña e intentos de login fallidos
- Probar políticas regularmente para garantizar efectividad

**Configuración clave (common-password):**
```bash
password requisite pam_pwquality.so retry=3 minlen=14 dcredit=-1 ucredit=-1 lcredit=-1 ocredit=-1
password [success=1 default=ignore] pam_unix.so obscure use_authtok try_first_pass yescrypt sha512 rounds=5000
password requisite pam_deny.so
password required pam_permit.so
password required pam_unix.so remember=5 use_authtok try_first_pass yescrypt
```

</details>

<details>
<summary><b>Pilar 6 — Monitoreo de Integridad de Ficheros (AIDE)</b></summary>
<br/>

> [!IMPORTANT]
> **Detecta manipulación temprano** — AIDE monitorea continuamente ficheros del sistema para detectar modificaciones no autorizadas, alertando a administradores sobre posibles brechas.

**Acciones clave para bastionado Linux:**

- Instalar AIDE y crear base de datos baseline inicial
- Configurar reglas de AIDE para monitorear ficheros críticos del sistema
- Definir calendario de monitoreo (diario, semanal, o en tiempo real)
- Generar reportes de integridad y alertas en cambios
- Investigar inmediatamente todas las modificaciones de ficheros críticos
- Almacenar base de datos y reportes de AIDE offsite o read-only
- Excluir ficheros temporales y directorios de logs
- Optimizar tamaño de base de datos para rendimiento
- Integrar AIDE con logging centralizado (SIEM)
- Implementar respuesta automatizada a cambios detectados

**Configuración clave (aide.conf):**
```bash
/bin			R+b+sha512
/sbin			R+b+sha512
/usr/bin		R+b+sha512
/usr/sbin		R+b+sha512
/lib			R+b+sha512
/lib64			R+b+sha512
/etc			R+b+sha512
!/etc/ssl/private
!/var/log
!/var/cache
```

</details>

<details>
<summary><b>Pilar 7 — Desactivar Servicios y Módulos Innecesarios</b></summary>
<br/>

> [!IMPORTANT]
> **Reduce superficie de ataque** — cada servicio ejecutándose es una potencial vulnerabilidad. Desactiva lo que no sea explícitamente requerido.

**Acciones clave para bastionado Linux:**

- Auditar todos los paquetes instalados y servicios en ejecución
- Documentar qué servicios son esenciales para operaciones
- Desactivar daemons innecesarios (cups, avahi, bluetooth, etc.)
- Desactivar módulos innecesarios del kernel (USB, firewire, bluetooth, etc.)
- Usar systemctl para enmascarar servicios permanentemente
- Blacklist módulos del kernel en /etc/modprobe.d/
- Probar funcionalidad después de cada eliminación
- Mantener changelog de cambios para rollback
- Monitorear rendimiento del sistema post-bastionado
- Verificar que no se rompan dependencias críticas

**Servicios comunes a desactivar:**
```
cups (impresión)
avahi-daemon (mDNS)
bluetooth
iscsid (iSCSI)
rpcbind (NFS)
snmpd (SNMP)
```

**Módulos comunes del kernel a desactivar:**
```
usb-storage
firewire
bluetooth
binfmt_misc (opcional)
```

</details>

<details>
<summary><b>Pilar 8 — Auditoría Exhaustiva de Seguridad (Lynis)</b></summary>
<br/>

> [!IMPORTANT]
> **Mide para mejorar** — Lynis proporciona una evaluación holística de seguridad, identificando gaps y priorizando esfuerzos de remediación.

**Acciones clave para bastionado Linux:**

- Instalar Lynis desde repositorios oficiales
- Ejecutar auditoría completa del sistema en modo detallado
- Revisar todas las advertencias, sugerencias y hallazgos informativos
- Calcular puntuación Hardening Index (mayor es mejor)
- Abordar primero hallazgos críticos y de alta prioridad
- Programar auditorías Lynis trimestrales o biestrales
- Rastrear mejora de Hardening Index a lo largo del tiempo
- Integrar Lynis en pipelines CI/CD para validación de baseline
- Generar reportes de auditoría para management y cumplimiento
- Usar salida de Lynis para validar implementación de medidas de bastionado

**Comando auditoría Lynis:**
```bash
sudo lynis audit system --quiet --quick
sudo lynis audit system --forensics
sudo lynis generate report
```

</details>

---

### 📂 Estructura de Documentos

```
TAREA-2-TEMA-1-Bastionado-Linux/
├── 📄 README.md                                ←  Este documento
├── 📂 1-Introduccion/
│   ├── introduccion_bastionado.md
│   └── conceptos_clave.md
├── 📂 2-Gestion-Usuarios-Contrasenas/
│   ├── gestion_usuarios.md
│   ├── politica_contrasenas.md
│   └── scripts_usuarios.sh
├── 📂 3-Configuracion-SSH/
│   ├── ssh_hardening.md
│   ├── sshd_config_seguro
│   └── ssh_banner.txt
├── 📂 4-Actualizaciones-Automaticas/
│   ├── actualizaciones_automaticas.md
│   └── unattended_upgrades.conf
├── 📂 5-Cortafuegos-UFW/
│   ├── ufw_configuracion.md
│   └── reglas_ufw.sh
├── 📂 6-PAM-PWQuality/
│   ├── pam_pwquality_setup.md
│   └── common_password_config
├── 📂 7-AIDE/
│   ├── aide_instalacion.md
│   ├── aide.conf
│   └── verificacion_integridad.sh
├── 📂 8-Desactivacion-Servicios/
│   ├── servicios_desactivar.md
│   └── desactivar_servicios.sh
├── 📂 9-Lynis/
│   ├── lynis_guia.md
│   └── lynis_audit.sh
└── 📂 10-Scripts-Automatizacion/
    ├── bastionado_completo.sh
    └── verificacion_seguridad.sh
```

---

### 📖 Conceptos Clave

> [!NOTE]
> **Bastionado** — El proceso de configurar un sistema operativo o aplicación con mejores prácticas de seguridad para reducir vulnerabilidades y superficie de ataque.

> [!NOTE]
> **Principio de Mínimo Privilegio** — Los usuarios y servicios deben tener solo los permisos mínimos necesarios para realizar sus funciones previstas.

> [!NOTE]
> **SSH (Secure Shell)** — Protocolo de red criptográfico para login remoto seguro y ejecución de comandos, reemplazando protocolos inseguros como Telnet.

> [!NOTE]
> **UFW (Uncomplicated Firewall)** — Interfaz amigable para iptables, diseñada para simplificar configuración de cortafuegos en sistemas Linux.

> [!NOTE]
> **AIDE (Advanced Intrusion Detection Environment)** — Herramienta de monitoreo de integridad de ficheros que detecta modificaciones no autorizadas en ficheros del sistema.

> [!NOTE]
> **Lynis** — Herramienta exhaustiva de auditoría de seguridad que identifica vulnerabilidades y misconfigurations en sistemas Linux.

---

### ✅ Entregables Esperados

Una implementación completa de bastionado Linux debe incluir:
- ✅ Configuración segura de gestión de usuarios y contraseñas
- ✅ Configuración SSH bastionada con autenticación basada en clave
- ✅ Mecanismo de actualización automática de seguridad activado
- ✅ Cortafuegos UFW con rulesets restrictivos desplegado
- ✅ Política de contraseña PAM-PWQuality enforzada
- ✅ Base de datos baseline de AIDE creada y monitoreo activo
- ✅ Servicios y módulos innecesarios desactivados con documentación
- ✅ Auditoría Lynis completada con puntuación Hardening Index
- ✅ Resultados de validación de pruebas de seguridad
- ✅ Documentación exhaustiva y runbooks

---

### ⚠️ Consideraciones Importantes

- **Prueba en entorno no-producción primero** — los cambios de bastionado pueden impactar funcionalidad
- **Mantén acceso físico o de consola** — evita quedar bloqueado de SSH
- **Documenta todos los cambios** — habilita fácil rollback si surgen problemas
- **Automatiza donde sea posible** — usa scripts para garantizar consistencia entre múltiples sistemas
- **Monitorea continuamente** — bastionado no es una actividad puntual; adapta a nuevas amenazas
- **La cumplimentación importa** — asegura que bastionado se alinea con RGPD, ENS e ISO 27001

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00ff88,50:1a1f2e,100:0d1117&height=120&section=footer" width="100%"/>

*Master's in Cybersecurity — System Security / Linux Hardening*

*Máster en Ciberseguridad — Seguridad de Sistemas / Bastionado Linux*

</div>
