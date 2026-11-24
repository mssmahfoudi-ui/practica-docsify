# 7.2 Necesidades de software en entornos productivos

Elegir software para producción exige verificar que funciona de forma fiable, se integra con la
infraestructura existente y cumple los requisitos legales y económicos de la organización.

````text
1. Requerimientos antes de elegir software
Ámbito            Qué comprobar                                                      Qué evitar
````

````text
Hardware          CPU, RAM, almacenamiento (capacidad/IOPS),                         Dimensionar solo con
                  GPU (si hay diseño/IA) y red.                                      requisitos mínimos sin
                                                                                     margen de crecimiento.
````

````text
Software          SO compatible, versiones, dependencias, BBDD                       Conflictos de versiones o
y red             y si exige Internet permanente o solo para                         formatos incompatibles.
                  activar/actualizar.
````

````text
Organizac         Nº de usuarios, licencia (pago único/perpetuo                      Mirar solo el precio inicial
ión y             o suscripción), TCO, formación, soporte y                          ignorando costes ocultos o
coste             RGPD.                                                              legales.
````

Conceptos clave de análisis

Mínimos vs. recomendados: los mínimos solo permiten arrancar; en producción planifica siempre sobre los
recomendados más margen de crecimiento.

TCO (Total Cost of Ownership): suma de licencia, hardware, implantación, formación, soporte y
mantenimiento.

RGPD (Reglamento UE 2016/679): su art. 32 exige medidas técnicas y organizativas adecuadas al riesgo
(seudonimización, cifrado, confidencialidad, integridad, disponibilidad, resiliencia y capacidad de restaurar los
datos mediante copias), y el Capítulo V (arts. 44–49) regula las transferencias internacionales fuera del
Espacio Económico Europeo (EEE).

Requerimientos funcionales vs. no funcionales
Según los estándares de ingeniería de requisitos (ISO/IEC/IEEE 29148) y calidad del producto
software (ISO/IEC 25010):

Funcionales (qué hace el sistema): funciones y tareas del sector que debe ejecutar la
aplicación (emitir facturas, controlar stock, gestionar tickets).
No funcionales (cómo se comporta y qué restricciones cumple): atributos de calidad como
seguridad, usabilidad (capacidad de interacción), compatibilidad, eficiencia de rendimiento,
fiabilidad (disponibilidad), mantenibilidad y portabilidad/flexibilidad.

2. «Estable primero, rápido después»
En producción, una caída tras actualizar cuesta tiempo y dinero. Por ello se prioriza la estabilidad:

````text
Sistema /           Canal        Duración oficial de soporte
Software            estable
````

````text
Ubuntu LTS          Rama         5 años gratis (Main), 10 años con Ubuntu Pro (ESM, gratis para uso
(p. ej. 24.04       LTS          personal hasta 5 equipos) y hasta 15 años con Legacy Support Add-
LTS / 26.04         (cada 2      on (24.04 LTS hasta mayo de 2039; 26.04 LTS hasta mayo de 2041).
LTS)                años)
````

````text
Debian              Rama         5 años totales (~3 años de soporte de seguridad principal + ~2 años
Stable              Stable       adicionales del equipo Debian LTS).
````

````text
Windows             Canal        5 años en Windows 11 Enterprise LTSC 2024 y Windows 10 Enterprise
Enterprise          LTSC         LTSC 2021; 10 años en Windows 11 IoT Enterprise LTSC 2024,
LTSC                             Windows 10 IoT Enterprise LTSC 2021 y Windows 10 Enterprise LTSC
                                 2019 (fin de soporte: enero de 2029).
````

(Datos de ciclo de vida verificados en las fuentes oficiales en noviembre de 2026).

````text
Flujo seguro de actualización y prevención
       Desarrollo        Pruebas (Staging)                    Copia previa              Producción
       (Cambios)         (Validar parches)                 (Backup / Snapshot)   (Ventana mantenimiento)
````

Actualizar con método: probar parches en staging y hacer backup/snapshot antes de tocar
producción.
Medir: monitorizar tiempos de respuesta, CPU, RAM, disco y usuarios simultáneos.

Prever fallos: copias de seguridad, redundancia (RAID, réplicas) y escalado (vertical u
horizontal).

## 3. Adecuación según tamaño y sector

Según tamaño de la empresa
Autónomos y microempresas: software estándar en la nube (SaaS); bajo coste inicial y sin
servidores propios.
Pymes: sistemas modulares adaptables (facturación, almacén, CRM).

Grandes empresas e industria: ERP corporativos (SAP, Odoo Enterprise, Dynamics) o
software a medida.

Según sector productivo
Oficina y administración: suites ofimáticas, correo, navegador y gestión documental.

Comercio / tienda: TPV (Terminal Punto de Venta), stock en tiempo real y facturación
electrónica.

Fábrica / industria: planificación de producción, CAD/CAM y sistemas SCADA de control de
planta.

Diseño y multimedia: edición de imagen, vídeo y 3D (Photoshop, Premiere/DaVinci, Blender)
con alta GPU y RAM.
Servicios, desarrollo e informática: gestión de proyectos, helpdesk, IDE, Git, máquinas
virtuales y contenedores.

````text
4. Comprobación de requisitos en terminal
 # En Linux: CPU, memoria RAM, espacio en disco y versión exacta del SO
 # LC_ALL=C mantiene las etiquetas en inglés para que grep funcione en cualquier idioma
 LC_ALL=C lscpu | grep -E "Architecture|Model name|CPU\(s\)"
 free -h
 df -h
 cat /etc/os-release
````

````text
 # En Windows (PowerShell): SO, procesador, RAM (en bytes) y espacio libre en
 volúmenes
 $info = Get-ComputerInfo
 $info | Select-Object OsName, OsVersion, CsTotalPhysicalMemory
 $info.CsProcessors | Select-Object Name, NumberOfCores, NumberOfLogicalProcessors
 Get-Volume | Select-Object DriveLetter, FileSystemLabel, SizeRemaining, Size
````

## Referencias

Canonical — The Ubuntu lifecycle and release cadence (soporte estándar de 5 años, Ubuntu
Pro de 10 años y Legacy Support Add-on de 15 años; verificación: noviembre de 2026).

Debian Project — Debian Security FAQ y Debian Long Term Support (LTS) (ciclo de ~3 años
estándar + ~2 años LTS; verificación: noviembre de 2026).

Microsoft Learn — Windows 11 Enterprise LTSC 2024, Windows 11 IoT Enterprise LTSC 2024,
Windows 10 Enterprise LTSC 2021 y Windows 10 Enterprise LTSC 2019 (verificación:
noviembre de 2026).
EUR-Lex — Reglamento (UE) 2016/679 (RGPD) (art. 32 sobre seguridad del tratamiento y
Capítulo V sobre transferencias internacionales).
ISO / IEC / IEEE — Catálogo oficial de normas ISO: ISO/IEC/IEEE 29148 (ingeniería de
requisitos) e ISO/IEC 25010 (modelo de calidad de producto software para requisitos no
funcionales).

Microsoft Learn — Get-ComputerInfo y Get-Volume.
Linux man-pages / freedesktop.org — lscpu(1), free(1), df(1) y os-release(5).
