# 7.3 Documentación técnica y herramientas ofimáticas

Documentar es inseparable del trabajo de sistemas y desarrollo: lo que no queda documentado
obliga a repetir la investigación desde cero ante cada incidencia o relevo.

## 1. Principios y tipos de documentación técnica

Cinco reglas de oro
1. Debe evolucionar: actualizarse con cada cambio de versión, ruta o comando.

2. Bien organizada: índices claros, jerarquía lógica y separación entre teoría y práctica.
3. Lenguaje claro: sin ambigüedades; distinguir pasos obligatorios y comandos de
administrador (root).
4. Sencilla de entender: adaptada al lector (usuario final frente a técnico).

5. Consistente: misma terminología, formato de comandos y estilo en todo el documento.

Tipos habituales
Manual de usuario: guía paso a paso para el usuario final y preguntas frecuentes.

Manual de administración: requisitos, despliegue, red, copias de seguridad y recuperación.
README / Wiki técnica: visión rápida del proyecto, estructura de carpetas y arranque en
local.
Registro de cambios (changelog): historial cronológico de novedades, mejoras y
correcciones relevantes entre versiones de un proyecto.
Registro de incidencias (postmortem): qué falló, causa raíz, solución aplicada y fecha para
evitar recurrencias.

````text
2. Ofimática tradicional, texto plano y Markdown
Enfoque         Cómo funciona                                Ventajas                         Cuándo elegirlo
````

````text
Ofimática       What You See Is What You Get:                Intuitiva para                   Actas,
(WYSIWY         editas directamente el aspecto               maquetación, informes            presupuestos,
G)              visual final.                                y presentaciones.                informes
                                                                                              corporativos.
````

````text
Texto           Sin formato visual (Bloc de                  Universal, instantáneo y         Notas rápidas,
plano           notas, Notepad++, VS Code,                   ligero.                          logs, ficheros
(.txt)          nano).                                                                        .conf/.csv.
````

````text
Markdow         Texto plano con marcas simples               Ideal para código, Git y         Manuales, wikis,
n (.md)         (#, *, `) compilado a web/PDF.               documentación técnica.           README.md,
                                                                                              portafolios.
````

Suites ofimáticas y equivalencias

````text
Función              Microsoft        LibreOffice (MPL                    Google                 Formatos
                     365              2.0)                                Workspace
````

````text
Texto                Word             Writer                              Documentos             .odt, .docx,
                                                                                                 .pdf
````

````text
Hoja de              Excel            Calc                                Hojas de cálculo       .ods, .xlsx,
cálculo                                                                                          .csv
````

````text
Presentacione        PowerPoint       Impress                             Presentaciones         .odp, .pptx,
s                                                                                                .pdf
````

````text
BBDD                 Access           Base                                (sin equivalente)      .accdb, .odb
escritorio
      Aclaraciones de formato y compatibilidad
````

Estándares abiertos ISO: ODF (.odt, .ods, .odp) corresponde al estándar ISO/IEC 26300 (OASIS) y OOXML
(.docx, .xlsx, .pptx) a ISO/IEC 29500 (habitualmente en variante Transitional en Microsoft Office); para
entregar documentos terminados sin desajustes visuales, exporta siempre a PDF (ISO 32000).

Compatibilidad Office ↔ LibreOffice: ambos abren los formatos del otro, pero en documentos complejos
(tablas avanzadas o macros) puede haber diferencias visuales.

Access / Base: útiles para prototipos o bases locales pequeñas; en entornos multiusuario o aplicaciones web
se usan SGBD dedicados (PostgreSQL, MariaDB/MySQL, SQL Server).

## 3. Guía práctica de Markdown

Markdown (.md) es el estándar de facto en repositorios (GitHub, GitLab) y generadores de
documentación (Docsify, MkDocs, Starlight).
Figura 1. Edición de Markdown en texto plano con previsualización en tiempo real. Autoría:
Omphalosskeptic, licencia CC BY-SA 3.0.

## Sintaxis esencial

````text
  # Título H1
  ## Sección H2
  ### Subsección H3
````

Texto en **negrita**, *cursiva* y `comando inline`.

- Viñeta principal
- Subviñeta
1. Paso uno
2. Paso dos

[Enlace](https://ejemplo.org) · ![Descripción](ruta/imagen.png)
> Nota o cita destacada.

## Bloques de código y tablas

````text
  ```bash
  sudo apt update && sudo apt install -y nginx
  ```
````

````text
  | Parámetro | Valor | Descripción |
  |---|---|---|
  | Puerto | `443` | Tráfico HTTPS cifrado |
````

````text
Vista previa y conversión
En Visual Studio Code puedes abrir la vista previa en la pestaña actual con Ctrl + Shift + V, o la
vista previa lateral (pantalla dividida) con Ctrl + K V (pulsa Ctrl + K, suelta y pulsa V). También
puedes convertir ficheros .md a Word/HTML con Pandoc:
 # Convertir un manual en Markdown a .docx o HTML
 pandoc manual-instalacion.md -o manual-instalacion.docx
 pandoc manual-instalacion.md -s -o manual-instalacion.html
````

## Referencias

The Document Foundation — LibreOffice Licenses (licencia MPL 2.0).

OASIS / ISO — OASIS Standards (ODF) y Catálogo oficial de normas ISO (ISO/IEC 26300 ODF,
ISO/IEC 29500 OOXML y ISO 32000-2 PDF 2.0).

PDF Association — ISO 32000-2 (PDF 2.0).
CommonMark — CommonMark Specification y GitHub — GitHub Flavored Markdown Spec.

Visual Studio Code — Markdown editing with Visual Studio Code (atajos Ctrl + Shift + V y
Ctrl + K V).

Pandoc — Pandoc User’s Guide (conversión de Markdown a .docx y HTML).

Keep a Changelog — Keep a Changelog 1.1.0 (estructura y propósito de un registro de
cambios).
