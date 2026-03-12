<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,100:00ff88&height=300&section=header&text=TAREA%202%20-%20TEMA%201%20-%20Bastionado%20Linux&fontSize=40&fontColor=00ff88&desc=Hardening%20de%20Sistemas%20Linux%20para%20Ciberseguridad&descSize=16&descAlign=3&descAlignY=55" alt="Header" />

<div align="center">

[![Linux](https://img.shields.io/badge/OS-Linux%20Hardening-00ff88?style=for-the-badge&logo=linux)](.)
[![Security](https://img.shields.io/badge/Category-System%20Security-00ff88?style=for-the-badge&logo=shield)](.)
[![Master's](https://img.shields.io/badge/Level-Master's%20Studies-0d1117?style=for-the-badge&logo=graduation-cap)](.)
[![Status](https://img.shields.io/badge/Status-Complete-00ff88?style=for-the-badge&logo=checkmark)](.)

[![Tools](https://img.shields.io/badge/Tools-SSH%20|%20UFW%20|%20Lynis%20|%20AIDE-0d1117?style=for-the-badge)](.)
[![Language](https://img.shields.io/badge/Language-ES%20%7C%20EN-00ff88?style=for-the-badge)](.)

---

<a href="#english">🇬🇧 English</a> | <a href="#español">🇪🇸 Español</a>

---

</div>

---

<h2 id="español">🔒 TAREA 2 - TEMA 1: Bastionado de Sistema Linux</h2>

Documentación completa sobre las medidas de hardening (bastionado) aplicadas a un sistema Linux para incrementar su seguridad y resistencia frente a amenazas. Esta tarea cubre desde la gestión de usuarios hasta herramientas avanzadas de auditoría y monitoreo.

### 🎯 Objetivos

- [x] Aplicar medidas de bastionado en sistemas Linux
- [x] Configurar gestión segura de usuarios y contraseñas
- [x] Asegurar la conexión SSH con claves criptográficas
- [x] Implementar actualizaciones automáticas de seguridad
- [x] Configurar un cortafuegos robusto con UFW
- [x] Implementar políticas de contraseñas con libpam-pwquality
- [x] Monitorear integridad de ficheros con AIDE
- [x] Desactivar servicios y módulos innecesarios
- [x] Auditar seguridad con Lynis

---

## 📁 Estructura del Repositorio

```
TAREA-2-TEMA-1-Bastionado-Linux/
├── 📄 README.md
├── 📂 1-Introduccion/
│   ├── introduccion_bastionado.md
│   ├── conceptos_clave.md
│   └── importancia_hardening.md
├── 📂 2-Gestion-Usuarios-Contrasenas/
│   ├── gestion_usuarios.md
│   ├── politica_contrasenas.md
│   ├── scripts_usuarios.sh
│   └── audit_usuarios.md
├── 📂 3-Configuracion-SSH/
│   ├── ssh_hardening.md
│   ├── sshd_config_seguro
│   ├── generacion_claves.md
│   ├── desactivar_root_login.md
│   └── ssh_banner.txt
├── 📂 4-Actualizaciones-Automaticas/
│   ├── actualizaciones_automaticas.md
│   ├── unattended_upgrades.md
│   ├── configuracion_apt.md
│   └── monitoreo_actualizaciones.sh
├── 📂 5-Cortafuegos-UFW/
│   ├── ufw_configuracion.md
│   ├── reglas_ufw.sh
│   ├── perfiles_ufw.md
│   ├── logging_ufw.md
│   └── ufw_advanced.md
├── 📂 6-PAM-PWQuality/
│   ├── pam_pwquality_setup.md
│   ├── common_password_config
│   ├── requisitos_contrasena.md
│   ├── testing_policies.sh
│   └── audit_password_policy.md
├── 📂 7-AIDE/
│   ├── aide_instalacion.md
│   ├── aide_config_basico
│   ├── aide_config_avanzado
│   ├── inicializacion_bd.sh
│   ├── verificacion_integridad.sh
│   └── alertas_aide.md
├── 📂 8-Desactivacion-Servicios/
│   ├── servicios_innecesarios.md
│   ├── modulos_kernel_desactivar.md
│   ├── desactivar_servicios.sh
│   ├── auditoria_servicios.md
│   └── impacto_rendimiento.md
├── 📂 9-Lynis/
│   ├── lynis_guia_completa.md
│   ├── lynis_instalacion.sh
│   ├── lynis_ejecucion.md
│   ├── interpretacion_resultados.md
│   ├── lynis_hardening_index.md
│   └── reporte_lynis_ejemplo.txt
├── 📂 10-Scripts-Automatizacion/
│   ├── hardening_completo.sh
│   ├── verificacion_seguridad.sh
│   ├── monitoreo_contino.sh
│   ├── backup_configuracion.sh
│   └── rollback_cambios.sh
├── 📂 11-Testing-Validacion/
│   ├── pruebas_seguridad.md
│   ├── test_ssh_security.sh
│   ├── test_firewall.sh
│   ├── test_password_policy.sh
│   ├── nmap_port_scan.sh
│   └── resultados_testing.md
└── 📂 12-Conclusiones-Aprendizajes/
    ├── conclusiones.md
    ├── lecciones_aprendidas.md
    ├── mejoras_futuras.md
    ├── referencias_completas.md
    └── glosario_terminos.md
```

---

## 📚 Medidas de Bastionado Detalladas

### <details>
<summary><strong>1. Gestión de Usuarios y Contraseñas</strong></summary>

**Objetivo:** Implementar controles de acceso basados en principios de menor privilegio.

**Contenidos:**
- Principio de menor privilegio (Least Privilege)
- Creación y eliminación segura de usuarios
- Asignación de grupos y permisos
- Auditoría de usuarios del sistema
- Desactivación de cuentas de usuario innecesarias
- Configuración de sudo con restricciones
- Monitoreo de accesos administrativos
- Gestión de permisos de ficheros (/etc/passwd, /etc/shadow)

**Ficheros Generados:**
- `gestion_usuarios.md` - Guía completa de gestión de usuarios
- `politica_contrasenas.md` - Política de contraseñas robusto
- `scripts_usuarios.sh` - Script de automatización para gestión
- `audit_usuarios.md` - Auditoria y verificación

**Herramientas:** useradd, userdel, usermod, sudo, lastlog, w

</details>

### <details>
<summary><strong>2. Configuración Segura de SSH</strong></summary>

**Objetivo:** Asegurar el acceso remoto mediante SSH con criptografía robusta.

**Contenidos:**
- Cambio de puerto SSH (no estándar)
- Desactivación de login como root
- Autenticación por clave pública/privada
- Desactivación de autenticación por contraseña
- Configuración de timeout de sesión
- Restricción de usuarios permitidos
- Configuración de banner de seguridad
- Encriptación fuerte de conexiones
- Monitoreo de intentos de acceso fallidos
- Fail2ban para prevención de ataques de fuerza bruta

**Ficheros Generados:**
- `ssh_hardening.md` - Guía de hardening SSH
- `sshd_config_seguro` - Fichero de configuración SSH optimizado
- `generacion_claves.md` - Procedimiento de generación de claves
- `desactivar_root_login.md` - Seguridad de cuenta root
- `ssh_banner.txt` - Banner de seguridad personalizado

**Herramientas:** SSH, ssh-keygen, sshd_config, ssh-copy-id, Fail2ban

</details>

### <details>
<summary><strong>3. Actualizaciones Automáticas de Seguridad</strong></summary>

**Objetivo:** Mantener el sistema actualizado automáticamente contra vulnerabilidades conocidas.

**Contenidos:**
- Configuración de unattended-upgrades
- Actualizaciones automáticas de kernel
- Configuración de repositorios de seguridad
- Notificaciones de actualizaciones
- Reboots automáticos seguros
- Rollback de actualizaciones problemáticas
- Auditoría de cambios instalados
- Gestión de dependencias
- Planificación de ventanas de mantenimiento

**Ficheros Generados:**
- `actualizaciones_automaticas.md` - Guía de configuración
- `unattended_upgrades.md` - Configuración detallada
- `configuracion_apt.md` - Gestión de paquetes APT
- `monitoreo_actualizaciones.sh` - Script de monitoreo

**Herramientas:** apt, unattended-upgrades, apt-listchanges, needrestart

</details>

### <details>
<summary><strong>4. Configuración del Cortafuegos (UFW)</strong></summary>

**Objetivo:** Controlar el tráfico de red permitido y denegado.

**Contenidos:**
- Instalación y habilitación de UFW
- Política por defecto (DENY incoming, ALLOW outgoing)
- Apertura selectiva de puertos
- Reglas para aplicaciones específicas
- Reglas stateful y stateless
- Logging y monitoreo de UFW
- Perfiles de aplicación predefinidos
- Reglas basadas en direcciones IP
- IPv6 hardening
- Integración con fail2ban

**Ficheros Generados:**
- `ufw_configuracion.md` - Guía completa de UFW
- `reglas_ufw.sh` - Script de aplicación de reglas
- `perfiles_ufw.md` - Perfiles predefinidos
- `logging_ufw.md` - Configuración de logging
- `ufw_advanced.md` - Configuración avanzada

**Herramientas:** UFW (Uncomplicated Firewall), iptables, ufw

</details>

### <details>
<summary><strong>5. Políticas de Contraseñas con libpam-pwquality</strong></summary>

**Objetivo:** Enforcer contraseñas fuertes y políticas de complejidad.

**Contenidos:**
- Instalación de libpam-pwquality
- Requisitos mínimos de contraseña
- Complejidad (mayúsculas, minúsculas, números, símbolos)
- Longitud mínima y máxima
- Reutilización de contraseñas bloqueada
- Validación en tiempo real
- Mensajes de error informativos
- Excepción para usuarios privilegiados
- Auditoría de cambios de contraseña
- Testing de políticas

**Ficheros Generados:**
- `pam_pwquality_setup.md` - Guía de instalación
- `common_password_config` - Fichero de configuración
- `requisitos_contrasena.md` - Especificaciones de requisitos
- `testing_policies.sh` - Script de validación
- `audit_password_policy.md` - Auditoría de cumplimiento

**Herramientas:** libpam-pwquality, PAM, passwd, chpasswd

</details>

### <details>
<summary><strong>6. Monitoreo de Integridad con AIDE</strong></summary>

**Objetivo:** Detectar cambios no autorizados en ficheros del sistema.

**Contenidos:**
- Instalación y configuración de AIDE
- Creación de base de datos inicial
- Definición de ficheros a monitorear
- Verificación periódica de integridad
- Generación de reportes de cambios
- Alertas automáticas ante cambios
- Configuración de exclusiones
- Optimización de rendimiento
- Integración con sistemas de logging
- Respuesta ante detección de cambios

**Ficheros Generados:**
- `aide_instalacion.md` - Guía de instalación
- `aide_config_basico` - Configuración básica
- `aide_config_avanzado` - Configuración avanzada
- `inicializacion_bd.sh` - Script de inicialización
- `verificacion_integridad.sh` - Script de verificación
- `alertas_aide.md` - Sistema de alertas

**Herramientas:** AIDE (Advanced Intrusion Detection Environment), cron, systemd

</details>

### <details>
<summary><strong>7. Desactivación de Módulos y Servicios Innecesarios</strong></summary>

**Objetivo:** Reducir la superficie de ataque eliminando componentes no necesarios.

**Contenidos:**
- Auditoría de servicios en ejecución
- Identificación de servicios innecesarios
- Desactivación segura de servicios
- Desactivación de módulos del kernel
- Desactivación de daemons legacy
- Impacto en funcionalidad
- Documentación de cambios
- Rollback de cambios
- Monitoreo post-cambios
- Verificación de dependencias

**Ficheros Generados:**
- `servicios_innecesarios.md` - Listado y análisis
- `modulos_kernel_desactivar.md` - Módulos del kernel
- `desactivar_servicios.sh` - Script de automatización
- `auditoria_servicios.md` - Auditoría completa
- `impacto_rendimiento.md` - Análisis de impacto

**Herramientas:** systemctl, modprobe, lsmod, service, chkconfig

</details>

### <details>
<summary><strong>8. Auditoría de Seguridad con Lynis</strong></summary>

**Objetivo:** Realizar auditoría exhaustiva de seguridad del sistema.

**Contenidos:**
- Instalación de Lynis
- Ejecución de auditorías completas
- Interpretación de resultados y scoring
- Hardening Index
- Sugerencias de mejora
- Generación de reportes detallados
- Ejecución programada de auditorías
- Comparación de resultados en el tiempo
- Identificación de debilidades críticas
- Tracking de cumplimiento de estándares

**Ficheros Generados:**
- `lynis_guia_completa.md` - Guía detallada
- `lynis_instalacion.sh` - Script de instalación
- `lynis_ejecucion.md` - Procedimiento de ejecución
- `interpretacion_resultados.md` - Análisis de resultados
- `lynis_hardening_index.md` - Métricas de hardening
- `reporte_lynis_ejemplo.txt` - Reporte de ejemplo

**Herramientas:** Lynis, bash, cron, grep, awk

</details>

---

## 🔧 Scripts de Automatización

> [!NOTE]
> Se incluyen scripts bash para automatizar el proceso completo de bastionado.

### Scripts Principales:

| Script | Función | Descripción |
|--------|---------|-------------|
| `hardening_completo.sh` | Automatización total | Aplica todas las medidas en secuencia |
| `verificacion_seguridad.sh` | Validación | Verifica el estado de seguridad actual |
| `monitoreo_contino.sh` | Monitoreo | Monitorea comportamientos anómalos |
| `backup_configuracion.sh` | Respaldo | Realiza backup antes de cambios |
| `rollback_cambios.sh` | Recuperación | Revierte cambios si es necesario |

---

## ✅ Medidas de Hardening Aplicadas - Resumen

| Medida | Implementado | Prioridad | Verificado |
|--------|:-------------:|:---------:|:----------:|
| Gestión de usuarios | ✅ | CRÍTICA | ✅ |
| SSH hardening | ✅ | CRÍTICA | ✅ |
| Actualizaciones automáticas | ✅ | ALTA | ✅ |
| UFW cortafuegos | ✅ | CRÍTICA | ✅ |
| PAM PWQuality | ✅ | ALTA | ✅ |
| AIDE integridad | ✅ | MEDIA | ✅ |
| Desactivar servicios | ✅ | MEDIA | ✅ |
| Lynis auditoría | ✅ | MEDIA | ✅ |

---

## > [!IMPORTANT]
> **Antes de aplicar cambios en producción:**
> - Realizar backup completo del sistema
> - Documentar configuración actual
> - Testear en entorno de staging
> - Tener acceso físico o consola de recuperación
> - Planificar ventana de mantenimiento
> - Verificar no bloquear acceso administrativo

---

## 🔗 Herramientas y Recursos Utilizados

> [!NOTE]
> Listado de herramientas y fuentes de referencia para profundizar.

| Herramienta | Categoría | Descripción |
|-------------|-----------|-------------|
| **SSH** | Acceso Remoto | Protocolo seguro de acceso remoto |
| **UFW** | Cortafuegos | Firewall simplificado para Linux |
| **PAM** | Autenticación | Pluggable Authentication Modules |
| **AIDE** | Integridad | Advanced Intrusion Detection |
| **Lynis** | Auditoría | Herramienta de auditoría de seguridad |
| **Fail2ban** | Prevención | Prevención de ataques de fuerza bruta |
| **unattended-upgrades** | Actualizaciones | Gestor de actualizaciones automáticas |
| **Auditd** | Logging | Framework de auditoría del kernel |

---

## 💡 Competencias Desarrolladas

```
✓ Hardening de sistemas Linux
✓ Configuración segura de SSH
✓ Gestión de cortafuegos (UFW)
✓ Políticas de contraseñas
✓ Monitoreo de integridad de ficheros
✓ Automatización de seguridad
✓ Auditoría de sistemas
✓ Scripting bash para seguridad
✓ Identificación de vulnerabilidades
✓ Análisis de riesgo y mitigación
```

---

## 📊 Niveles de Hardening Alcanzados

```
Básico (Nivel 1)
├── Actualizaciones del sistema
├── Cambio de contraseña por defecto
└── Habilitación de firewall

Intermedio (Nivel 2)
├── SSH configurado
├── Usuarios adicionales sin privilegios
├── Servicios innecesarios desactivados
└── Políticas de contraseña

Avanzado (Nivel 3)
├── Monitoreo de integridad (AIDE)
├── Auditd configurado
├── Fail2ban implementado
├── Actualizaciones automáticas
└── Auditoría con Lynis ✅ ALCANZADO
```

---

<h2 id="english">🔒 TASK 2 - TOPIC 1: Linux System Hardening</h2>

Complete documentation on hardening measures applied to a Linux system to increase its security and resilience against threats. This task covers everything from user management to advanced auditing and monitoring tools.

### 🎯 Objectives

- [x] Apply hardening measures in Linux systems
- [x] Configure secure user and password management
- [x] Secure remote access using SSH with cryptography
- [x] Implement automatic security updates
- [x] Configure a robust firewall with UFW
- [x] Implement password policies with libpam-pwquality
- [x] Monitor file integrity with AIDE
- [x] Disable unnecessary services and modules
- [x] Audit security with Lynis

---

## 📁 Repository Structure

```
TASK-2-TOPIC-1-Linux-Hardening/
├── 📄 README.md
├── 📂 1-Introduction/
│   ├── introduction_hardening.md
│   ├── key_concepts.md
│   └── importance_hardening.md
├── 📂 2-User-Password-Management/
│   ├── user_management.md
│   ├── password_policy.md
│   ├── users_scripts.sh
│   └── users_audit.md
├── 📂 3-SSH-Configuration/
│   ├── ssh_hardening.md
│   ├── sshd_config_secure
│   ├── key_generation.md
│   ├── disable_root_login.md
│   └── ssh_banner.txt
├── 📂 4-Automatic-Updates/
│   ├── automatic_updates.md
│   ├── unattended_upgrades.md
│   ├── apt_configuration.md
│   └── updates_monitoring.sh
├── 📂 5-Firewall-UFW/
│   ├── ufw_configuration.md
│   ├── ufw_rules.sh
│   ├── ufw_profiles.md
│   ├── ufw_logging.md
│   └── ufw_advanced.md
├── 📂 6-PAM-PWQuality/
│   ├── pam_pwquality_setup.md
│   ├── common_password_config
│   ├── password_requirements.md
│   ├── testing_policies.sh
│   └── audit_password_policy.md
├── 📂 7-AIDE/
│   ├── aide_installation.md
│   ├── aide_config_basic
│   ├── aide_config_advanced
│   ├── initialize_db.sh
│   ├── verify_integrity.sh
│   └── aide_alerts.md
├── 📂 8-Disable-Services/
│   ├── unnecessary_services.md
│   ├── kernel_modules_disable.md
│   ├── disable_services.sh
│   ├── services_audit.md
│   └── performance_impact.md
├── 📂 9-Lynis/
│   ├── lynis_complete_guide.md
│   ├── lynis_installation.sh
│   ├── lynis_execution.md
│   ├── results_interpretation.md
│   ├── lynis_hardening_index.md
│   └── lynis_report_example.txt
├── 📂 10-Automation-Scripts/
│   ├── complete_hardening.sh
│   ├── security_verification.sh
│   ├── continuous_monitoring.sh
│   ├── backup_configuration.sh
│   └── rollback_changes.sh
├── 📂 11-Testing-Validation/
│   ├── security_tests.md
│   ├── test_ssh_security.sh
│   ├── test_firewall.sh
│   ├── test_password_policy.sh
│   ├── nmap_port_scan.sh
│   └── testing_results.md
└── 📂 12-Conclusions-Learning/
    ├── conclusions.md
    ├── lessons_learned.md
    ├── future_improvements.md
    ├── complete_references.md
    └── terminology_glossary.md
```

---

## 📚 Detailed Hardening Measures

### <details>
<summary><strong>1. User and Password Management</strong></summary>

**Objective:** Implement access controls based on least privilege principles.

**Contents:**
- Least Privilege Principle
- Secure user creation and deletion
- Group and permission assignment
- User system audit
- Disabling unnecessary user accounts
- Configuring sudo with restrictions
- Administrative access monitoring
- File permission management (/etc/passwd, /etc/shadow)

**Generated Files:**
- `user_management.md` - Complete user management guide
- `password_policy.md` - Robust password policy
- `users_scripts.sh` - Automation script
- `users_audit.md` - Audit and verification

**Tools:** useradd, userdel, usermod, sudo, lastlog, w

</details>

### <details>
<summary><strong>2. Secure SSH Configuration</strong></summary>

**Objective:** Secure remote access using SSH with robust cryptography.

**Contents:**
- SSH port change (non-standard)
- Disable root login
- Public/private key authentication
- Disable password authentication
- Session timeout configuration
- Restriction of allowed users
- Security banner configuration
- Strong encryption
- Failed access attempt monitoring
- Fail2ban for brute force prevention

**Generated Files:**
- `ssh_hardening.md` - SSH hardening guide
- `sshd_config_secure` - Optimized SSH config file
- `key_generation.md` - Key generation procedure
- `disable_root_login.md` - Root account security
- `ssh_banner.txt` - Custom security banner

**Tools:** SSH, ssh-keygen, sshd_config, ssh-copy-id, Fail2ban

</details>

### <details>
<summary><strong>3. Automatic Security Updates</strong></summary>

**Objective:** Keep system updated automatically against known vulnerabilities.

**Contents:**
- Unattended-upgrades configuration
- Automatic kernel updates
- Security repository configuration
- Update notifications
- Safe automatic reboots
- Rollback of problematic updates
- Audit of installed changes
- Dependency management
- Maintenance window scheduling

**Generated Files:**
- `automatic_updates.md` - Configuration guide
- `unattended_upgrades.md` - Detailed configuration
- `apt_configuration.md` - APT package management
- `updates_monitoring.sh` - Monitoring script

**Tools:** apt, unattended-upgrades, apt-listchanges, needrestart

</details>

### <details>
<summary><strong>4. Firewall Configuration (UFW)</strong></summary>

**Objective:** Control allowed and denied network traffic.

**Contents:**
- UFW installation and activation
- Default policy (DENY incoming, ALLOW outgoing)
- Selective port opening
- Application-specific rules
- Stateful and stateless rules
- UFW logging and monitoring
- Predefined application profiles
- IP-based rules
- IPv6 hardening
- Fail2ban integration

**Generated Files:**
- `ufw_configuration.md` - Complete UFW guide
- `ufw_rules.sh` - Rules application script
- `ufw_profiles.md` - Predefined profiles
- `ufw_logging.md` - Logging configuration
- `ufw_advanced.md` - Advanced configuration

**Tools:** UFW (Uncomplicated Firewall), iptables, ufw

</details>

### <details>
<summary><strong>5. Password Policies with libpam-pwquality</strong></summary>

**Objective:** Enforce strong passwords and complexity policies.

**Contents:**
- Libpam-pwquality installation
- Minimum password requirements
- Complexity (uppercase, lowercase, numbers, symbols)
- Minimum and maximum length
- Password reuse blocked
- Real-time validation
- Informative error messages
- Exception for privileged users
- Password change audit
- Policy testing

**Generated Files:**
- `pam_pwquality_setup.md` - Installation guide
- `common_password_config` - Configuration file
- `password_requirements.md` - Requirements specification
- `testing_policies.sh` - Validation script
- `audit_password_policy.md` - Compliance audit

**Tools:** libpam-pwquality, PAM, passwd, chpasswd

</details>

### <details>
<summary><strong>6. File Integrity Monitoring with AIDE</strong></summary>

**Objective:** Detect unauthorized changes to system files.

**Contents:**
- AIDE installation and configuration
- Initial database creation
- File monitoring definition
- Periodic integrity verification
- Change report generation
- Automatic alerts on changes
- Exclusion configuration
- Performance optimization
- Logging system integration
- Change response procedures

**Generated Files:**
- `aide_installation.md` - Installation guide
- `aide_config_basic` - Basic configuration
- `aide_config_advanced` - Advanced configuration
- `initialize_db.sh` - Initialization script
- `verify_integrity.sh` - Verification script
- `aide_alerts.md` - Alert system

**Tools:** AIDE (Advanced Intrusion Detection Environment), cron, systemd

</details>

### <details>
<summary><strong>7. Disable Unnecessary Modules and Services</strong></summary>

**Objective:** Reduce attack surface by removing unnecessary components.

**Contents:**
- Audit of running services
- Identification of unnecessary services
- Safe service deactivation
- Kernel module deactivation
- Legacy daemon disabling
- Functionality impact
- Change documentation
- Change rollback
- Post-change monitoring
- Dependency verification

**Generated Files:**
- `unnecessary_services.md` - List and analysis
- `kernel_modules_disable.md` - Kernel modules
- `disable_services.sh` - Automation script
- `services_audit.md` - Complete audit
- `performance_impact.md` - Impact analysis

**Tools:** systemctl, modprobe, lsmod, service, chkconfig

</details>

### <details>
<summary><strong>8. Security Audit with Lynis</strong></summary>

**Objective:** Perform exhaustive system security audit.

**Contents:**
- Lynis installation
- Full audit execution
- Results interpretation and scoring
- Hardening Index
- Improvement suggestions
- Detailed report generation
- Scheduled audit execution
- Results comparison over time
- Critical weakness identification
- Standards compliance tracking

**Generated Files:**
- `lynis_complete_guide.md` - Detailed guide
- `lynis_installation.sh` - Installation script
- `lynis_execution.md` - Execution procedure
- `results_interpretation.md` - Results analysis
- `lynis_hardening_index.md` - Hardening metrics
- `lynis_report_example.txt` - Example report

**Tools:** Lynis, bash, cron, grep, awk

</details>

---

## 🔧 Automation Scripts

> [!NOTE]
> Bash scripts included to automate the complete hardening process.

### Main Scripts:

| Script | Function | Description |
|--------|----------|-------------|
| `complete_hardening.sh` | Full automation | Applies all measures in sequence |
| `security_verification.sh` | Validation | Verifies current security state |
| `continuous_monitoring.sh` | Monitoring | Monitors anomalous behavior |
| `backup_configuration.sh` | Backup | Performs backup before changes |
| `rollback_changes.sh` | Recovery | Reverts changes if needed |

---

## ✅ Applied Hardening Measures - Summary

| Measure | Implemented | Priority | Verified |
|---------|:------------:|:--------:|:--------:|
| User management | ✅ | CRITICAL | ✅ |
| SSH hardening | ✅ | CRITICAL | ✅ |
| Automatic updates | ✅ | HIGH | ✅ |
| UFW firewall | ✅ | CRITICAL | ✅ |
| PAM PWQuality | ✅ | HIGH | ✅ |
| AIDE integrity | ✅ | MEDIUM | ✅ |
| Disable services | ✅ | MEDIUM | ✅ |
| Lynis audit | ✅ | MEDIUM | ✅ |

---

## > [!IMPORTANT]
> **Before applying changes in production:**
> - Perform complete system backup
> - Document current configuration
> - Test in staging environment
> - Have physical access or recovery console
> - Plan maintenance window
> - Verify not blocking administrative access

---

## 🔗 Tools and Resources Used

> [!NOTE]
> List of tools and reference sources for further learning.

| Tool | Category | Description |
|------|----------|-------------|
| **SSH** | Remote Access | Secure remote access protocol |
| **UFW** | Firewall | Simplified Linux firewall |
| **PAM** | Authentication | Pluggable Authentication Modules |
| **AIDE** | Integrity | Advanced Intrusion Detection |
| **Lynis** | Audit | Security audit tool |
| **Fail2ban** | Prevention | Brute force attack prevention |
| **unattended-upgrades** | Updates | Automatic update manager |
| **Auditd** | Logging | Kernel audit framework |

---

## 💡 Developed Competencies

```
✓ Linux system hardening
✓ Secure SSH configuration
✓ Firewall management (UFW)
✓ Password policies
✓ File integrity monitoring
✓ Security automation
✓ System auditing
✓ Bash scripting for security
✓ Vulnerability identification
✓ Risk analysis and mitigation
```

---

## 📊 Hardening Levels Achieved

```
Basic (Level 1)
├── System updates
├── Default password change
└── Firewall activation

Intermediate (Level 2)
├── SSH configured
├── Additional non-privileged users
├── Unnecessary services disabled
└── Password policies

Advanced (Level 3)
├── File integrity monitoring (AIDE)
├── Auditd configured
├── Fail2ban implemented
├── Automatic updates
└── Lynis audit ✅ ACHIEVED
```

---

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00ff88,100:0d1117&height=200&section=footer&text=Master%20en%20Ciberseguridad%202025-2026&fontSize=30&fontColor=00ff88" alt="Footer" />

<div align="center">

**Created during Master's in Cybersecurity (2025/2026)**

*Practical implementation of Linux hardening techniques*

---

### 📋 Folder Name for GitHub:

**TAREA-2-TEMA-1-Bastionado-Linux**

*or in English:*

**TASK-2-TOPIC-1-Linux-Hardening**

</div>
