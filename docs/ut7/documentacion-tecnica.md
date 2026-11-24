# 7.6 Búsqueda y fiabilidad de documentación técnica

Sustituir búsquedas genéricas por métodos sistemáticos sobre fuentes oficiales ahorra tiempo y
evita aplicar soluciones obsoletas o inseguras.

## 1. Flujo de búsqueda en cuatro pasos

````text
            1. Error exacto      2. Ayuda local                    3. Docs oficiales    4. Verificar fecha,
            + versión y SO      (man / Get-Help)                     o GitHub / IA     versión y seguridad
````

1. Describe el problema: copia el código o mensaje de error literal (preferiblemente en inglés).
2. Añade contexto: programa, versión exacta y sistema operativo.

3. Prioriza fuentes oficiales: manual local, documentación del fabricante o repositorio oficial.
4. Verifica antes de aplicar: comprueba fecha, versión y qué hace cada comando.

## 2. Fuentes técnicas de referencia

Ayuda integrada offline (exacta para tu versión)

````text
  # En Linux: manual oficial, búsqueda por palabra y ayuda rápida
  man scp
  apropos compress
  tar --help
 # En Windows (PowerShell y CMD): ejemplos locales y manual online
 Get-Help Test-NetConnection -Examples
 Get-Help Get-ComputerInfo -Online
 robocopy /?
````

Documentación oficial, GitHub y comunidades
Documentación oficial y estándares: Microsoft Learn, Ubuntu/Debian/Red Hat Docs,
ArchWiki, MDN Web Docs, especificaciones RFC (ietf.org).

GitHub: archivos README.md y pestaña Wiki como manuales; pestaña Issues cerrados para
errores ya resueltos.

Foros técnicos: Stack Overflow, Super User y comunidades especializadas (revisar votos,
fecha y respuesta aceptada; evitar hilos genéricos sin fuente como respuestas antiguas de
Quora).

````text
 # Buscar en GitHub issues cerrados de un repositorio y filtrar por lenguaje
 repo:docsifyjs/docsify is:issue is:closed "loadSidebar"
 language:powershell sftp
````

Cómo formular una buena pregunta

Incluye siempre cuatro datos: qué intentas hacer, SO y versión, comando o código ejecutado y error completo.

Asistentes de IA como apoyo técnico
Uso recomendado: ChatGPT, Claude, Copilot o Gemini ayudan a explicar conceptos,
resumir manuales y depurar errores usando prompts claros (SO, versión y error exacto).
Precaución (alucinaciones): pueden inventar comandos, parámetros o rutas; contrasta
siempre con man, Get-Help o la documentación oficial antes de ejecutar.

## 3. Buscadores web y operadores reales

Aclaración: ¿Qué es Googlebot?

Un robot / spider / crawler como Googlebot es el programa interno del buscador que rastrea e indexa la web
previamente.

No es un comando que ejecute el usuario al buscar; el usuario consulta ese índice mediante palabras clave y
operadores.

Aclaración: Operadores web frente a redes sociales

Operadores como since:, until:, near:, within: o filter:links pertenecen a redes sociales (como X/Twitter) y
no son los operadores recomendados para documentación técnica en Google, Bing o DuckDuckGo. En Google, el
filtrado por fechas se realiza con before:AAAA-MM-DD / after:AAAA-MM-DD o desde el menú Herramientas.

````text
Operador             Para qué sirve                                              Ejemplo técnico
web
````

````text
"frase               Coincidencia literal del mensaje o error.                   "Connection refused" port 22
exacta"                                                                          ssh
````

````text
site:domin           Restringe a una web oficial.                                site:learn.microsoft.com
io                                                                               "Test-NetConnection"
````

````text
-término             Excluye ruido o versiones antiguas.                         ubuntu ip estatica -18.04
                                                                                 -16.04
````

````text
OR                   Busca cualquiera de dos alternativas                        linux backup tar OR rsync
                     (debe ir en mayúsculas).
````

````text
filetype:e           Filtra por tipo de documento.                               filetype:pdf "ISO 27001" guía
xt
````

````text
intitle:té           Exige el término en el título.                              intitle:SFTP FileZilla
rmino                                                                            configuración
````

````text
4. Lista de verificación: ¿es fiable?
✅ Comprueba                                  ❌ Desconfía
````

````text
Autoría: fabricante oficial o                Comandos sin explicar: no aclaran qué modifican.
repositorio del proyecto.
````

````text
Actualización: fecha reciente.               Páginas desconocidas: clones automáticos sin
                                             contexto.
````

````text
Versión: coincide con tu SO y                Enlaces sospechosos: acortadores o descargas
software.                                    externas.
````

````text
Contraste: otra fuente fiable coincide.      Atajos inseguros: chmod 777, desactivar firewall o curl
                                             ... | bash sin leer.
````

## Referencias

Google Search Central — What is Googlebot? y Overview of Google Search operators.

Ayuda de la Búsqueda de Google — Perfeccionar búsquedas en la Web (operadores "",
site:, -, OR, filetype: e intitle:).

GitHub Docs — Buscar incidencias y solicitudes de extracción y Sintaxis de búsqueda de
código en GitHub.

Microsoft Learn — Get-Help y robocopy.

Linux man-pages — man(1) y apropos(1).
Portales técnicos oficiales citados — Microsoft Learn, Ubuntu Documentation, Debian
Documentation, ArchWiki, MDN Web Docs e IETF RFC Editor.
