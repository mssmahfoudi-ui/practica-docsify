# 7.4 Correo y mensajería electrónica

En cualquier entorno productivo conviven el correo electrónico (comunicación formal y asíncrona)
y la mensajería instantánea (colaboración rápida en tiempo real).

## 1. Correo electrónico vs. Mensajería instantánea

Correo electrónico (asíncrono): no exige respuesta inmediata; aporta registro formal,
asunto, adjuntos y alta trazabilidad.
Mensajería instantánea (síncrona): comunicación en tiempo real mediante chats, canales
temáticos y llamadas para coordinación ágil.

## 2. Protocolos del correo electrónico

````text
              Cliente origen                                     Servidor saliente                                          Servidor destino                              Cliente destino
                                       Envía mensaje (SMTP)                                   Transfiere entre servidores                      Sincroniza o descarga
       (Thunderbird / Outlook / Web)                             (SMTP 587 / 465)                                           (Buzón receptor)                           (IMAP 993 / POP3 995)
````

````text
Prot              Siglas                                Puerto                          Función principal
ocol                                                    cifrado
o
````

````text
SMT               Simple Mail                           587                             Envío de mensajes del cliente al servidor y entre
P                 Transfer                              (STARTTLS)                      servidores.
                  Protocol                              / 465 (TLS)
````

````text
IMA               Internet                              993                             Sincroniza mensajes y carpetas en el servidor
P                 Message                               (SSL/TLS)                       (recomendado).
                  Access
                  Protocol
Prot       Siglas                 Puerto              Función principal
ocol                              cifrado
o
````

````text
POP        Post Office            995                 Descarga mensajes al equipo local (por defecto los
3          Protocol v3            (SSL/TLS)           borra del servidor, aunque puede configurarse copia;
                                                      no sincroniza carpetas ni estados).
````

Aclaración sobre el puerto 25 y RFC 8314

RFC 8314 (IETF, 2018): declara obsoleto el acceso sin cifrar (Cleartext Considered Obsolete) para clientes de
correo (puertos 110 y 143 sin cifrar), reasigna formalmente el puerto 465 para envío con TLS implícito
(submissions) y prioriza TLS implícito (465, 993, 995) frente a STARTTLS (587) para mitigar ataques de
degradación.

Puerto 25: reservado para transferencia entre servidores (MTA a MTA, RFC 5321); suele estar bloqueado
para clientes domésticos para frenar el spam.

## 3. Clientes, organización y privacidad

Clientes habituales y organización
Webmail: acceso desde navegador (Gmail, Outlook.com, Proton Mail).
Clientes de escritorio/móvil: Mozilla Thunderbird (libre, MPL 2.0), Microsoft Outlook
(propietario), Evolution (libre, LGPL, Linux).
Carpetas vs. etiquetas: en IMAP/Outlook cada correo reside en una carpeta; en Gmail las
etiquetas permiten asignar varias categorías sin duplicar el mensaje.

Ejemplo Microsoft 365 / Exchange Online: entrada IMAP outlook.office365.com:993
(SSL/TLS) y salida SMTP smtp.office365.com:587 (STARTTLS; en cuentas personales de
Outlook.com el servidor saliente es smtp-mail.outlook.com:587). Exige autenticación
moderna (OAuth 2.0), ya que Microsoft retiró la autenticación básica (usuario y contraseña)
en IMAP/POP y la está retirando en SMTP AUTH.

````text
Destinatarios: Para, CC y CCO
Campo                          Uso recomendado                                         Visibilidad de direcciones
````

````text
Para                           Destinatarios principales que deben                     Visible para Para y CC.
                               actuar.
````

````text
CC (Copia de Carbón)           Personas que deben estar informadas                     Visible para Para y CC.
                               sin acción directa.
````

````text
CCO (Copia de Carbón           Envíos múltiples protegiendo la                         Oculta para el resto de
Oculta)                        privacidad de terceros.                                 destinatarios.
````

Privacidad y RGPD

En avisos a múltiples destinatarios externos, usa siempre CCO para no exponer sus direcciones de correo al resto:
hacerlo en Para o CC vulnera los arts. 5.1.f y 32 del RGPD y constituye una brecha de confidencialidad según las
guías y resoluciones de la AEPD.

## 4. Mensajería instantánea y colaboración

Entorno corporativo y desarrollo: Microsoft Teams (integrado en M365), Slack (canales,
bots, GitHub/Jira), Google Chat (Google Workspace).
Comunidades y uso general: Discord (servidores técnicos), Telegram (bots, adjuntos de
hasta 2 GB, o 4 GB con Telegram Premium; el cifrado extremo a extremo solo se activa en
chats secretos, no en los chats en la nube por defecto), WhatsApp.

Privacidad reforzada: Signal (código libre AGPLv3, cifrado extremo a extremo activado por
defecto mediante el Protocolo Signal).

Seguridad en mensajería

No envíes contraseñas en texto plano ni datos sensibles de clientes por cuentas personales; usa los canales
corporativos aprobados.

## Referencias

IETF — RFC 8314 (Cleartext Considered Obsolete, puertos 465, 587, 993 y 995), RFC 5321
(SMTP y puerto 25), RFC 6409 (Message Submission), RFC 9051 (IMAP4rev2) y RFC 1939
(POP3).
Microsoft Learn — Desuso de la autenticación básica en Exchange Online y POP3 e IMAP4 en
Exchange Online (verificación: noviembre de 2026).
Microsoft Learn — Test-NetConnection y OpenSSL — openssl-s_client.

EUR-Lex — Reglamento (UE) 2016/679 (RGPD) (arts. 5.1.f y 32) y AEPD — Guía para la
notificación de brechas de datos personales.

Mozilla — Mozilla Public License 2.0 (Thunderbird), Telegram — Preguntas frecuentes oficiales
(límite de 2 GB / 4 GB Premium y chats secretos; verificación: noviembre de 2026) y Signal —
Documentación oficial.
