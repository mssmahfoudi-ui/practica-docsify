# 7.1 Clasificación y licencias de software

Objetivo e ideas del tema

Objetivo: Elaborar documentación valorando y utilizando aplicaciones informáticas de propósito general.

a) Clasificar software en función de su licencia y propósito.

b) Analizar las necesidades específicas de software asociadas al uso de sistemas informáticos en diferentes
entornos productivos.

c) Realizar tareas de documentación mediante el uso de herramientas ofimáticas.

d) Utilizar sistemas de correo y mensajería electrónica.

e) Utilizar los servicios de transferencia de ficheros.

f) Utilizar métodos de búsqueda de documentación técnica mediante el uso de servicios de Internet.

Antes de instalar o recomendar un programa, conviene saber para qué sirve (su propósito) y qué
permite hacer legalmente (su licencia).

## 1. Clasificación según su propósito

Software de sistema: gestiona el hardware y sirve de base al resto (Windows, GNU/Linux,
controladores, UEFI/BIOS).
Software de programación: herramientas para crear, compilar, interpretar y depurar
aplicaciones (VS Code, compiladores como gcc, intérpretes como Python y depuradores).
Software de aplicación: resuelve tareas concretas del usuario o empresa (ofimática,
diseño/multimedia, navegadores, seguridad, ERP, ocio).

## 2. Licencias de software y contratos legales

Una licencia es el contrato legal que fija qué puede hacer el usuario con el programa. Cumple tres
funciones: definir derechos (instalar, copiar, modificar, redistribuir), proteger la autoría y evitar
problemas legales.

EULA (End-User License Agreement): contrato de licencia de usuario final habitual en software
comercial.
Derecho de uso ≠ propiedad: al pagar por software propietario adquieres permiso de uso
bajo condiciones, no la propiedad del código.

Libre ≠ Gratuito — y soporte profesional en ambos

Software libre refiere a las libertades del usuario, no al precio (puede venderse comercialmente).

Software gratuito (freeware) suele ser propietario y de código cerrado.

Soporte: el software libre también cuenta con soporte comercial oficial (Red Hat, Ubuntu Pro, Collabora).

2.1. Las cuatro libertades del Software Libre
1. Libertad 0: ejecutar el programa como se desee, con cualquier propósito.
2. Libertad 1: estudiar cómo funciona el programa y cambiarlo para que haga lo que se quiera
(el acceso al código fuente es condición previa).
3. Libertad 2: redistribuir copias para ayudar a otros.
4. Libertad 3: distribuir copias de las versiones modificadas a terceros, permitiendo que la
comunidad se beneficie de las mejoras.

Cuando además cumple los criterios de la Open Source Initiative (OSI), se denomina FOSS / FLOSS
(Free/Libre and Open Source Software).

2.2. Espectro de licencias: de privativo a dominio público

````text
          Privativo        Shareware / Trial             Freeware                    Libre Copyleft            Libre Permisivo      Dominio Público / CC0
      (Windows, Office)       (WinRAR)             (Chrome, Adobe Reader)          (GPL: Linux, GIMP)         (MIT, Apache, BSD)   (SQLite, The Unlicense)
````

````text
Modelo                    Có               Modificación y                                               Ejemplos
                          dig              redistribución
                          o
````

````text
Privativo                 No               Prohibidas sin permiso;                                      Windows, Microsoft Office,
                                           requiere licencia de uso.                                    Photoshop
Modelo                Có      Modificación y                             Ejemplos
                      dig     redistribución
                       o
````

````text
Shareware /           No      Prueba gratuita limitada; uso              WinRAR, versiones de evaluación
Trial                         completo de pago.
````

````text
Freeware              No      Uso gratuito; código cerrado               Google Chrome (propietario basado
                              y redistribución controlada.               en Chromium), Adobe Acrobat
                                                                         Reader, Discord (freemium
                                                                         propietario)
````

````text
Libre Copyleft         Sí     Permitidas; las obras                      Kernel Linux (GPLv2), GIMP (GPLv3+)
fuerte (GPL)                  derivadas redistribuidas
                              mantienen GPL.
````

````text
Libre Copyleft         Sí     Para bibliotecas o a nivel de              glibc (LGPL), LibreOffice y Mozilla
débil (LGPL,                  archivo; enlazables o                      Thunderbird (MPL 2.0), base de
MPL 2.0)                      integrables con software                   FFmpeg (LGPL)
                              privativo.
````

````text
Libre                  Sí     Permitidas citando autoría;                Node.js (MIT), FreeBSD (BSD-2-
Permisivo                     integrables en software                    Clause), Apache HTTP Server
(MIT, BSD,                    privativo.                                 (Apache 2.0)
Apache 2.0)
````

````text
Dominio                Sí     Sin derechos patrimoniales                 SQLite, código bajo CC0 / The
público /                     exclusivos vigentes.                       Unlicense
Equivalentes
````

2.3. Aclaraciones sobre modelos reales
«Código abierto» ≠ «más restrictivo»: Open Source y Software Libre comparten
prácticamente las mismas licencias (MIT, Apache, GPL). La diferencia práctica está entre
licencias copyleft y permisivas: las copyleft (como GPL) obligan a que las obras derivadas
redistribuidas mantengan la misma licencia abierta, mientras que las permisivas (como MIT o
BSD) permiten reutilizar el código incluso en software propietario citando la autoría.
Licencias duales y ecosistemas mixtos: MySQL usa licencia dual (GPLv2 o comercial de
Oracle); Android combina base abierta (AOSP bajo Apache 2.0 + kernel Linux GPLv2) con
aplicaciones propietarias (Google Mobile Services).
Plazo legal y dominio público en España (LPI, RDL 1/1996): los derechos de explotación
duran vida del autor + 70 años si es persona física, o 70 años desde su divulgación o
creación si el titular es una empresa o persona jurídica (arts. 26 y 98). Como los derechos
morales son irrenunciables (art. 14), para ceder código al dominio público se usan
dedicaciones estándar (CC0, The Unlicense); SQLite, por ejemplo, añade declaraciones
juradas al dominio público y ofrece Warranty of Title para empresas.

2.4. Licencias para documentación y contenidos: Creative
Commons (CC)
Mientras las licencias anteriores regulan software y código fuente, las seis licencias Creative
Commons cubren contenidos creativos y documentación (manuales, imágenes, diagramas,
vídeos). No están recomendadas para código fuente porque no contemplan su entrega ni
patentes y generan incompatibilidades; en cambio, CC0 (equivalente al dominio público del
espectro anterior) sí puede aplicarse a código. Combinan cuatro condiciones: BY (atribución), SA
(compartir igual), NC (no comercial) y ND (sin derivadas).

````text
Herramienta / Licencia                                  Uso             Obras         Obliga a
                                                   comercial           derivadas   compartir igual
````

````text
CC BY (Atribución)                                      ✅                 ✅               No
````

````text
CC BY-SA (Atribución-CompartirIgual)                    ✅                 ✅               ✅
````

````text
CC BY-NC (Atribución-NoComercial)                       ❌                 ✅               No
````

````text
CC BY-ND (Atribución-SinDerivadas)                      ✅                 ❌               —
````

````text
CC BY-NC-SA (Atribución-NoComercial-                    ❌                 ✅               ✅
CompartirIgual)
Herramienta / Licencia                                     Uso             Obras         Obliga a
                                                      comercial           derivadas   compartir igual
````

````text
CC BY-NC-ND (Atribución-NoComercial-                       ❌                 ❌              —
SinDerivadas)
````

````text
CC0 (dedicación al dominio público, no                     ✅                 ✅              No
licencia)
````

````text
4. Comprobación práctica de licencias
  # En Linux (Debian / Ubuntu): ver paquete y cabecera de licencia
  dpkg -s git
  cat /usr/share/doc/git/copyright | head -n 20
````

````text
  # En Windows (PowerShell): consultar licencia de un paquete en winget
  winget show VideoLAN.VLC
  winget show 7zip.7zip
````

## Referencias

Free Software Foundation / Proyecto GNU — ¿Qué es el software libre? (las cuatro libertades
y la diferencia entre software libre y gratuito).
Open Source Initiative (OSI) — The Open Source Definition (criterios de código abierto /
FOSS).
Linux Foundation / SPDX — SPDX License List (licencias GPL, LGPL, MPL-2.0, MIT, Apache-2.0
y BSD-2-Clause).
The Document Foundation — LibreOffice Licenses (licencia MPL 2.0 de LibreOffice).
SQLite — SQLite Copyright (dedicación al dominio público y License and Warranty of Title).
Android Open Source Project — AOSP Licenses (Apache 2.0 en espacio de usuario y kernel
Linux GPLv2).
RARLAB — WinRAR License / Shareware (modelo shareware de evaluación de 40 días).

Boletín Oficial del Estado (BOE) — Real Decreto Legislativo 1/1996, de 12 de abril, Ley de
Propiedad Intelectual (arts. 14, 26 y 98).
Creative Commons — About CC Licenses y Frequently Asked Questions (las seis licencias CC,
CC0 y su recomendación respecto al software).
Microsoft Learn — Comando winget show y Debian Policy Manual — Copyright information.
