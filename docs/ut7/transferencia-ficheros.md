# 7.5 Transferencia de ficheros

El método adecuado para enviar un archivo depende de su tamaño, de si los equipos están en la
misma red, de la persistencia deseada y del nivel de seguridad.

````text
1. Métodos de transferencia según escenario
Método       Ideal para        Limitación clave                       Ejemplos
````

````text
Local        Archivos          Requiere proximidad o misma            USB, Bluetooth, SMB (v2/v3;
directa      pesados en el     LAN/VPN.                               CIFS corresponde al dialecto
(LAN/ca      mismo lugar                                              heredado SMB1, obsoleto
ble)         o red local.                                             por seguridad), NFS
````

````text
Correo       Documentos        Límite típico de 20–25 MB por          Thunderbird, Outlook, Gmail
electróni    pequeños y        envío (p. ej. 25 MB en Gmail y
co           envío formal.     35 MB por defecto en Exchange
                               Online, configurable).
````

````text
Nube         Trabajo           Depende de Internet y terceros;        Drive, OneDrive, Dropbox,
(sincroni    colaborativo y    cuidar permisos.                       iCloud, Nextcloud
zación)      acceso
             multidispositi
             vo.
````

````text
Envío        Entregas          El enlace caduca tras unos días.       WeTransfer, SwissTransfer
tempora      grandes
l            puntuales sin
             saturar la
             nube.
````

````text
Cliente-     Servidores        Requiere credenciales y                FileZilla, WinSCP, sftp, scp
servidor     web,              cliente/terminal.
             despliegues y
Método            Ideal para                Limitación clave                         Ejemplos
````

````text
(SFTP/S           automatizació
CP)               n.
````

¿Por qué falla el correo con archivos de ~20 MB?

Los adjuntos binarios se codifican en Base64 (MIME, RFC 2045), transformando cada 3 bytes en 4 caracteres, lo que
aumenta el tamaño en ~33 %: un PDF de 20 MB pasa a ~26,7 MB codificado (más cabeceras y saltos de línea) y
puede superar el límite del servidor.

## 2. Protocolos de red para transferencia

FTP (TCP 21/20)
Texto plano ❌

SFTP / SCP (TCP 22)
Túnel cifrado SSH ✅

````text
Protocol         Puerto                            Cifra         Uso recomendado
o                                                   do
````

````text
FTP              21 (control) / 20                  ❌            Usuario, clave y datos en texto plano (en modo
(RFC             (datos en modo                     No           pasivo usa puertos efímeros). Evitar.
Protocol         Puerto                           Cifra            Uso recomendado
o                                                     do
````

````text
959)             activo)
````

````text
TFTP             69 (UDP inicial)                     ❌            Sin autenticación; continúa en puertos UDP
(RFC                                                  No           efímeros. Solo en LAN aislada (PXE / firmware).
1350)
````

````text
FTPS             21 (TLS explícito) /                 ✅            FTP tradicional protegido con certificados TLS
(RFC             990 (TLS implícito,                  TLS          mediante AUTH TLS (puerto 21 estándar) o
4217)            heredado)                                         conexión directa (990).
````

````text
SFTP             22 (TCP)                             ✅            Subsistema sobre SSH en un único puerto.
                                                      SSH          Opción recomendada.
````

````text
SCP              22 (TCP)                             ✅            Copia no interactiva desde terminal sobre SSH
                                                      SSH          (ver nota sobre OpenSSH 9.0).
````

````text
HTTPS            443 (TCP; UDP en                     ✅            Descargas web, repositorios y APIs cifradas.
(RFC             HTTP/3)                              TLS
9110)
````

FTP ≠ SFTP ≠ FTPS — y cambio en scp desde OpenSSH 9.0

SFTP no es «FTP con S», sino un protocolo distinto sobre SSH (puerto 22). FTPS sí es FTP clásico envuelto en
TLS.
Desde OpenSSH 9.0 (2022), el comando scp emplea internamente el protocolo SFTP por defecto porque
el protocolo scp/rcp heredado quedó desaconsejado por motivos de seguridad (solo se usa con scp -O
frente a dispositivos antiguos sin SFTP).

## 3. Clientes gráficos, red local y terminal

Clientes gráficos habituales
FileZilla (libre, GNU GPL v2+ en cliente, multiplataforma): conexión por SFTP/FTPS/FTP
(Conexión rápida o Gestor de sitios), doble panel (local/remoto) y cola de transferencias.
WinSCP (libre, GNU GPL v3+, Windows): muy usado para SFTP y SCP.

Figura 1. Cliente FileZilla con vista en doble panel. Autoría: FileZilla Project, licencia GNU GPL v2+.

Carpetas compartidas en red local (LAN)
Rápidas y sin depender de Internet, limitadas a la red local (o VPN):

````text
  # En Windows (SMB): conectar recurso compartido \\servidor\recurso como unidad Z:
  net use Z: \\192.168.1.50\compartida /user:usuario
 # En Linux (NFS): montar un directorio exportado en red local
 # Requiere el paquete nfs-common en Debian/Ubuntu
 sudo mount -t nfs 192.168.1.50:/srv/compartida /mnt/red
````

Comandos scp y sftp (Windows OpenSSH y Linux)

````text
 # Copiar archivo o carpeta (-r) por SCP
 scp ./informe-ut7.pdf usuario@192.168.1.50:/home/usuario/documentos/
 scp -r usuario@192.168.1.50:/var/www/docs ./copia-local/
````

````text
 # Sesión interactiva SFTP (comandos internos: ls, lls, get, put, bye)
 sftp usuario@192.168.1.50
````

## 4. Compartir archivos con seguridad

Controla quién abre el enlace: evita «Cualquier persona con el enlace» en documentos
internos o personales.
Mínimo privilegio: da acceso solo a quien lo necesite y en solo lectura si no debe editar.

Protege datos privados: fija contraseña y caducidad; para ficheros sensibles, cífralos antes
(p. ej. .7z con AES-256) y envía la clave por otro canal.

## Referencias

IETF — RFC 959 (FTP), RFC 1350 (TFTP), RFC 4217 (FTPS), RFC 4251 (arquitectura SSH), RFC
2045 (MIME / Base64), RFC 9110 (HTTP) y RFC 7530 (NFSv4).
OpenSSH — OpenSSH 9.0 Release Notes (scp sobre SFTP por defecto y opción -O), Manual
de scp(1) y sftp(1).

Ayuda de Gmail — Enviar archivos adjuntos en Gmail (límite de 25 MB; verificación:
noviembre de 2026) y Microsoft Learn — Límites de Exchange Online.

Microsoft Learn — net use e Información general sobre SMB.
FileZilla Project — License (GNU GPL v2+); WinSCP — License (GNU GPL v3+); 7-Zip — 7z
Format (AES-256).
