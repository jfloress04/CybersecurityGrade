<div align="center">

<!-- BANNER VISUAL -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1a1f2e,100:00ff88&height=200&section=header&text=Forensic%20Copy%20/%20Copia%20Forense&fontSize=36&fontColor=00ff88&fontAlignY=38&desc=/etc/passwd%20%E2%80%94%20Kali%20Linux&descAlignY=58&descSize=18&descColor=8b949e" width="100%"/>

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
![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)
![Category](https://img.shields.io/badge/Category-Digital%20Forensics-00ff88?style=flat-square&logo=searchengineland&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)
![Integrity](https://img.shields.io/badge/Hash%20Verified-MD5%20%7C%20SHA--256-blueviolet?style=flat-square&logo=shield&logoColor=white)
![Lang](https://img.shields.io/badge/Lang-EN%20%7C%20ES-orange?style=flat-square)

</div>

---

<!-- ============================================================ -->
<!--                     ENGLISH VERSION                          -->
<!-- ============================================================ -->

<a name="english-version"></a>

<div align="center">
<h1>🔍 Practice 1 — Forensic Copy of <code>/etc/passwd</code></h1>
<p><i>Preserving digital evidence integrity through cryptographic hashing on Kali Linux</i></p>
</div>

### 📋 Overview

> A forensic copy of `/etc/passwd` was performed on a **Kali Linux** system, following the fundamental principles of **digital chain of custody**. The process ensures that the evidence copy is a bit-for-bit exact replica of the original, verified through cryptographic hashing.

---

### 🖥️ Environment

<div align="center">

| Parameter | Value |
|:---:|:---:|
| 🐧 Operating System | `Kali Linux` |
| 📄 File Analyzed | `/etc/passwd` |
| 📁 Evidence Location | `/root/forensics/` |
| 👤 User | `root` |

</div>

---

### 🎯 Objectives

- [x] Perform a complete forensic copy of `/etc/passwd`
- [x] Verify integrity using **MD5** and **SHA-256** hashing
- [x] Document the process following chain of custody principles
- [x] Store all evidence in a controlled, dedicated directory

---

### 🛠️ Tools Used

<div align="center">

| Tool | Purpose |
|:---|:---|
| `cp` / `dd` | Forensic copy of the original file |
| `md5sum` | MD5 hash generation & verification |
| `sha256sum` | SHA-256 hash generation & verification |
| `stat` | File metadata inspection (timestamps, permissions) |
| `ls -lah` | Directory listing with file details |

</div>

---

### 📂 Evidence Structure

```
/root/forensics/
├── 📄 passwd.copy        ←  Bit-for-bit forensic copy
├── 🔑 passwd.md5         ←  MD5 hashes (original + copy)
└── 🔒 passwd.sha256      ←  SHA-256 hashes (original + copy)
```

---

### 🔬 Step-by-Step Procedure

<details>
<summary><b>Step 1 — Environment Setup</b></summary>
<br/>

```bash
# Create the evidence directory
mkdir -p /root/forensics
cd /root/forensics
```
</details>

<details>
<summary><b>Step 2 — Original File Verification</b></summary>
<br/>

```bash
# Inspect file metadata before touching it
stat /etc/passwd
ls -lah /etc/passwd

# Optional: view content for reference only
cat /etc/passwd
```
</details>

<details>
<summary><b>Step 3 — Hash the Original (before copying)</b></summary>
<br/>

```bash
# Generate MD5 hash — save to evidence folder
md5sum /etc/passwd | tee /root/forensics/passwd.md5

# Generate SHA-256 hash — save to evidence folder
sha256sum /etc/passwd | tee /root/forensics/passwd.sha256
```
</details>

<details>
<summary><b>Step 4 — Perform the Forensic Copy</b></summary>
<br/>

```bash
# Option A — Preserve all metadata (simpler)
cp --preserve=all /etc/passwd /root/forensics/passwd.copy

# Option B — Bit-by-bit copy with dd (forensically sound)
dd if=/etc/passwd of=/root/forensics/passwd.copy bs=512 status=progress
```
</details>

<details>
<summary><b>Step 5 — Verify Copy Integrity</b></summary>
<br/>

```bash
# Compare hashes: original vs copy (must be IDENTICAL)
md5sum    /etc/passwd /root/forensics/passwd.copy
sha256sum /etc/passwd /root/forensics/passwd.copy

# Save final verification to evidence files
md5sum    /etc/passwd /root/forensics/passwd.copy > /root/forensics/passwd.md5
sha256sum /etc/passwd /root/forensics/passwd.copy > /root/forensics/passwd.sha256
```
</details>

<details>
<summary><b>Step 6 — Log the Evidence Directory</b></summary>
<br/>

```bash
# Final check of all evidence files
ls -lah /root/forensics/
```
</details>

---

### ✅ Expected Results

> [!IMPORTANT]
> Both hashes **must be identical** to confirm the copy's forensic validity.

```bash
# Expected output — hashes must match exactly
d41d8cd98f00b204e9800998ecf8427e  /etc/passwd
d41d8cd98f00b204e9800998ecf8427e  /root/forensics/passwd.copy
```

A matching hash confirms:
- ✅ Exact bit-for-bit replica of the original
- ✅ No corruption or alteration during the copy process
- ✅ Evidence is forensically valid for further analysis

---

### 📖 Key Concepts

> [!NOTE]
> **Chain of Custody** — Documented record of who accessed the evidence and when, ensuring legal admissibility.

> [!NOTE]
> **Cryptographic Hash** — A unique digital fingerprint; even a 1-bit change produces a completely different hash.

> [!NOTE]
> **Forensic Copy** — Exact bit-for-bit replica of the original. The source is **never modified**.

> [!NOTE]
> **`/etc/passwd`** — Linux file storing user account info: username, UID, GID, home directory, and shell.

---

### ⚠️ Important Notes

- All operations performed with **root** privileges
- The original file was **never modified**
- Evidence stored in a **dedicated, isolated directory**
- Hashes generated **both before and after** the copy

---
---

<!-- ============================================================ -->
<!--                    VERSIÓN EN ESPAÑOL                        -->
<!-- ============================================================ -->

<a name="version-espanol"></a>

<div align="center">
<h1>🔍 Práctica 1 — Copia Forense de <code>/etc/passwd</code></h1>
<p><i>Preservando la integridad de evidencias digitales mediante hashing criptográfico en Kali Linux</i></p>
</div>

### 📋 Descripción General

> Se realizó una copia forense del archivo `/etc/passwd` en un sistema **Kali Linux**, siguiendo los principios fundamentales de la **cadena de custodia digital**. El proceso garantiza que la copia de la evidencia es una réplica exacta bit a bit del original, verificada mediante hashes criptográficos.

---

### 🖥️ Entorno

<div align="center">

| Parámetro | Valor |
|:---:|:---:|
| 🐧 Sistema Operativo | `Kali Linux` |
| 📄 Archivo Analizado | `/etc/passwd` |
| 📁 Ubicación Evidencias | `/root/forensics/` |
| 👤 Usuario | `root` |

</div>

---

### 🎯 Objetivos

- [x] Realizar una copia forense íntegra de `/etc/passwd`
- [x] Verificar la integridad con hashing **MD5** y **SHA-256**
- [x] Documentar el proceso siguiendo la cadena de custodia
- [x] Almacenar las evidencias en un directorio controlado y dedicado

---

### 🛠️ Herramientas Utilizadas

<div align="center">

| Herramienta | Propósito |
|:---|:---|
| `cp` / `dd` | Copia forense del archivo original |
| `md5sum` | Generación y verificación del hash MD5 |
| `sha256sum` | Generación y verificación del hash SHA-256 |
| `stat` | Inspección de metadatos del archivo (timestamps, permisos) |
| `ls -lah` | Listado del directorio con detalles del archivo |

</div>

---

### 📂 Estructura de Evidencias

```
/root/forensics/
├── 📄 passwd.copy        ←  Copia forense bit a bit
├── 🔑 passwd.md5         ←  Hashes MD5 (original + copia)
└── 🔒 passwd.sha256      ←  Hashes SHA-256 (original + copia)
```

---

### 🔬 Procedimiento Paso a Paso

<details>
<summary><b>Paso 1 — Preparación del Entorno</b></summary>
<br/>

```bash
# Crear el directorio de evidencias
mkdir -p /root/forensics
cd /root/forensics
```
</details>

<details>
<summary><b>Paso 2 — Verificación del Archivo Original</b></summary>
<br/>

```bash
# Inspeccionar metadatos antes de tocar el archivo
stat /etc/passwd
ls -lah /etc/passwd

# Opcional: ver contenido solo como referencia
cat /etc/passwd
```
</details>

<details>
<summary><b>Paso 3 — Hash del Original (antes de copiar)</b></summary>
<br/>

```bash
# Generar hash MD5 — guardar en carpeta de evidencias
md5sum /etc/passwd | tee /root/forensics/passwd.md5

# Generar hash SHA-256 — guardar en carpeta de evidencias
sha256sum /etc/passwd | tee /root/forensics/passwd.sha256
```
</details>

<details>
<summary><b>Paso 4 — Realizar la Copia Forense</b></summary>
<br/>

```bash
# Opción A — Copia preservando metadatos (más simple)
cp --preserve=all /etc/passwd /root/forensics/passwd.copy

# Opción B — Copia bit a bit con dd (más forense)
dd if=/etc/passwd of=/root/forensics/passwd.copy bs=512 status=progress
```
</details>

<details>
<summary><b>Paso 5 — Verificar Integridad de la Copia</b></summary>
<br/>

```bash
# Comparar hashes: original vs copia (deben ser IDÉNTICOS)
md5sum    /etc/passwd /root/forensics/passwd.copy
sha256sum /etc/passwd /root/forensics/passwd.copy

# Guardar verificación final en archivos de evidencia
md5sum    /etc/passwd /root/forensics/passwd.copy > /root/forensics/passwd.md5
sha256sum /etc/passwd /root/forensics/passwd.copy > /root/forensics/passwd.sha256
```
</details>

<details>
<summary><b>Paso 6 — Registrar el Directorio de Evidencias</b></summary>
<br/>

```bash
# Comprobación final de todos los archivos de evidencia
ls -lah /root/forensics/
```
</details>

---

### ✅ Resultados Esperados

> [!IMPORTANT]
> Ambos hashes **deben ser idénticos** para confirmar la validez forense de la copia.

```bash
# Salida esperada — los hashes deben coincidir exactamente
d41d8cd98f00b204e9800998ecf8427e  /etc/passwd
d41d8cd98f00b204e9800998ecf8427e  /root/forensics/passwd.copy
```

Un hash coincidente confirma:
- ✅ Réplica exacta bit a bit del original
- ✅ Sin corrupción ni alteración durante el proceso
- ✅ Evidencia forense válida para análisis posterior

---

### 📖 Conceptos Clave

> [!NOTE]
> **Cadena de Custodia** — Registro documentado de quién accedió a la evidencia y cuándo, garantizando su validez legal.

> [!NOTE]
> **Hash Criptográfico** — Huella digital única; cualquier cambio de 1 bit genera un hash completamente diferente.

> [!NOTE]
> **Copia Forense** — Réplica exacta bit a bit del original. La fuente **nunca se modifica**.

> [!NOTE]
> **`/etc/passwd`** — Archivo Linux con información de cuentas: usuario, UID, GID, directorio home y shell.

---

### ⚠️ Consideraciones

- Todas las operaciones realizadas con permisos de **root**
- El archivo original **no fue modificado** en ningún momento
- Evidencias almacenadas en un **directorio dedicado y aislado**
- Hashes generados **antes y después** de la copia

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00ff88,50:1a1f2e,100:0d1117&height=120&section=footer" width="100%"/>

*Master's in Cybersecurity — Ethical Hacking / Digital Forensics*

*Máster en Ciberseguridad — Ethical Hacking / Informática Forense*

</div>
