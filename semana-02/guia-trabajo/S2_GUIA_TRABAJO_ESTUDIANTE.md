# GUÍA DE TRABAJO — ESTUDIANTE
# SEMANA 2: ESPECIFICACIÓN FORMAL DE SEGURIDAD Y LOGIN SEGURO
## Programación Segura (DD281)

---

**Nombre del estudiante:** _______________________________________________

**Grupo / Sección:** _____________________________________________________

**Fecha:** ______________________________________________________________

**Instrucciones generales:**
- Completa esta guía durante la sesión de clase en los momentos indicados por el docente.
- Sección A y B: durante la primera hora.
- Sección C y D: durante la segunda hora (después del receso).
- Sección E: actividad grupal práctica.
- Sección F: cierre y metacognición.

---

# SECCIÓN A — RECUPERACIÓN DE APRENDIZAJES (Semana 1)
## Responde antes de que el docente lo explique. Luego verifica tu respuesta.

---

### A.1 LA TRIADA CIA APLICADA AL LOGIN

Completa la tabla con la aplicación de cada pilar de la triada CIA al sistema de login:

| Pilar CIA | ¿Cómo se manifiesta en un sistema de login? | Ejemplo concreto |
|---|---|---|
| **Confidencialidad** | | |
| **Integridad** | | |
| **Disponibilidad** | | |

---

### A.2 OWASP TOP 10 — RELACIÓN CON AUTENTICACIÓN

Marca con ✓ las vulnerabilidades OWASP que se relacionan directamente con un login inseguro y explica brevemente por qué:

| # | Vulnerabilidad OWASP | ¿Relacionada con login? | ¿Por qué? |
|---|---|---|---|
| A01 | Broken Access Control | ☐ Sí ☐ No | |
| A02 | Cryptographic Failures | ☐ Sí ☐ No | |
| A03 | Injection | ☐ Sí ☐ No | |
| A04 | Insecure Design | ☐ Sí ☐ No | |
| A07 | Identification/Auth Failures | ☐ Sí ☐ No | |

---

### A.3 PRINCIPIO DE MÍNIMO PRIVILEGIO

¿Cómo aplicarías el principio de Mínimo Privilegio a un sistema de autenticación? Escribe al menos 3 aplicaciones concretas:

1. _______________________________________________________________________

2. _______________________________________________________________________

3. _______________________________________________________________________

---

# SECCIÓN B — ACTIVIDAD DIAGNÓSTICA: ¿QUÉ SÉ YA?

**Instrucción:** Antes de que el docente explique el tema, responde estas preguntas con lo que ya sabes. No hay respuestas incorrectas en este momento.

### B.1 ¿Qué hace que un login sea inseguro? (Lista libre)

Escribe todo lo que se te ocurra:

1. _______________________________________________
2. _______________________________________________
3. _______________________________________________
4. _______________________________________________
5. _______________________________________________
6. _______________________________________________

*(Al final de la clase volveremos a esta lista para ver cuánto más podemos agregar)*

---

### B.2 PREGUNTAS DE DIAGNÓSTICO

Responde con lo que ya sabes (marca la opción más correcta):

**B.2.1** ¿Cómo se deben almacenar las contraseñas en una base de datos?

- ☐ a) En texto plano para facilitar la recuperación
- ☐ b) Cifradas con AES-256 para poder descifrarlas si el usuario las olvida
- ☐ c) Como hash unidireccional con sal aleatoria
- ☐ d) Codificadas en Base64 para "ofuscarlas"

**B.2.2** ¿Qué versión de TLS/SSL deben usar los servidores web en 2024?

- ☐ a) SSL 3.0 — es la versión estándar
- ☐ b) TLS 1.0 — compatible con todos los dispositivos
- ☐ c) TLS 1.2 mínimo, preferiblemente TLS 1.3
- ☐ d) La versión no importa, cualquier SSL es suficiente

**B.2.3** ¿Qué es un certificado SSL autofirmado (self-signed)?

- ☐ a) Un certificado gratuito de Let's Encrypt
- ☐ b) Un certificado creado por uno mismo sin validación de una CA externa
- ☐ c) Un certificado de mayor seguridad que el emitido por una CA
- ☐ d) El tipo de certificado requerido en producción

---

# SECCIÓN C — CONCEPTOS CLAVE DE LA SESIÓN
## Completa durante la explicación del docente

---

### C.1 ESPECIFICACIÓN FORMAL DE SEGURIDAD

**C.1.1** Escribe con tus propias palabras qué es una especificación formal de seguridad:

_________________________________________________________________________

_________________________________________________________________________

_________________________________________________________________________

**C.1.2** ¿Cuál es la diferencia entre estas dos "especificaciones"? ¿Por qué una es formal y la otra no?

| | Ejemplo A | Ejemplo B |
|---|---|---|
| **Texto** | "El login debe ser seguro" | "Las contraseñas se almacenarán como hash bcrypt con factor de coste 12. Máximo 5 intentos antes de bloqueo de 15 min." |
| **¿Por qué es o no es una especificación formal?** | | |

**C.1.3** Completa los 7 componentes de una especificación formal de seguridad:

| # | Componente | ¿Qué define? |
|---|---|---|
| 1 | **Activos** | |
| 2 | **Sujetos** | |
| 3 | **Objetos** | |
| 4 | **Operaciones** | |
| 5 | **Condiciones** | |
| 6 | **Mecanismos** | |
| 7 | **Respuesta ante violación** | |

---

### C.2 PREGUNTAS PARA MARCAR (Selección múltiple)

Marca la respuesta correcta. Solo hay una opción correcta por pregunta.

**C.2.1** ¿Cuál es el problema de almacenar contraseñas con SHA-1 SIN SAL?

- ☐ a) SHA-1 no produce un hash — produce texto cifrado
- ☐ b) SHA-1 es reversible — se puede obtener la contraseña original
- ☐ c) Los atacantes pueden usar tablas rainbow precomputadas para romper el hash
- ☐ d) SHA-1 produce hashes demasiado cortos para ser seguros

**C.2.2** ¿Qué ventaja fundamental tiene bcrypt sobre SHA-256 para almacenar contraseñas?

- ☐ a) Bcrypt produce hashes más largos que SHA-256
- ☐ b) Bcrypt incluye automáticamente sal aleatoria y es intencionalmente lento
- ☐ c) Bcrypt es un algoritmo de cifrado, no de hash
- ☐ d) Bcrypt es más rápido que SHA-256, mejorando el rendimiento del login

**C.2.3** ¿Qué es la "sal" (salt) en el contexto del hashing de contraseñas?

- ☐ a) Un algoritmo de cifrado adicional aplicado al hash
- ☐ b) La clave secreta usada para cifrar el hash antes de almacenarlo
- ☐ c) Un valor aleatorio único por usuario que se concatena a la contraseña antes de hashear
- ☐ d) El factor de coste que determina cuántas rondas de hashing se ejecutan

**C.2.4** ¿Por qué es un error de seguridad grave que el formulario de login use el método HTTP GET?

- ☐ a) Porque GET no puede transportar datos de texto
- ☐ b) Porque los parámetros GET viajan en la URL y quedan en logs del servidor y en el historial del navegador
- ☐ c) Porque GET es más lento que POST para transferir datos
- ☐ d) Porque GET no cifra los datos antes de enviarlos

**C.2.5** ¿Qué es Perfect Forward Secrecy (PFS) en TLS?

- ☐ a) Un mecanismo que cifra el certificado del servidor con una segunda clave
- ☐ b) La capacidad del servidor de descifrar tráfico pasado si se compromete la clave privada
- ☐ c) El uso de claves de sesión efímeras para que el compromiso de la clave privada del servidor no permita descifrar tráfico pasado
- ☐ d) La verificación automática de que el certificado SSL no ha expirado

**C.2.6** ¿Cuál de los siguientes es el estándar de hash de contraseñas más recomendado hoy?

- ☐ a) MD5 con sal de 16 bytes
- ☐ b) SHA-512 sin sal
- ☐ c) bcrypt (factor 12+) o argon2id
- ☐ d) AES-256 con clave de 32 bytes

**C.2.7** ¿Cuál de las siguientes configuraciones de servidor web es correcta en relación a SSL?

- ☐ a) Habilitar SSL 3.0, TLS 1.0, TLS 1.1 y TLS 1.2 para máxima compatibilidad
- ☐ b) Usar solo TLS 1.3 y deshabilitar todas las versiones anteriores
- ☐ c) Deshabilitar SSL 2.0 y SSL 3.0, mantener TLS 1.0, 1.1, 1.2 y 1.3
- ☐ d) Usar TLS 1.2 y TLS 1.3, deshabilitar versiones anteriores

**C.2.8** ¿Qué es CGI (Common Gateway Interface)?

- ☐ a) Un framework de Python para desarrollo web seguro
- ☐ b) Un protocolo estándar que define cómo un servidor web pasa solicitudes a programas externos para generar respuestas dinámicas
- ☐ c) Una librería de JavaScript para crear formularios de login
- ☐ d) Un tipo de certificado SSL para servidores compartidos

**C.2.9** Un atacante ejecuta el siguiente input en el campo de usuario de un login CGI inseguro: `admin' --`. ¿Qué tipo de ataque es este y qué efecto tendría?

- ☐ a) XSS — inyecta código JavaScript en la página
- ☐ b) SQL Injection — el `'--` cierra la query y comenta el resto, posiblemente bypasseando la verificación de contraseña
- ☐ c) CSRF — falsifica una solicitud de otro dominio
- ☐ d) Path Traversal — intenta acceder a archivos del sistema

**C.2.10** ¿Cuál es el propósito del header HTTP `Strict-Transport-Security`?

- ☐ a) Obliga al servidor a responder solo con JSON
- ☐ b) Le indica al navegador que siempre use HTTPS para ese dominio, incluso si el usuario escribe HTTP
- ☐ c) Restringe el origen de las solicitudes al dominio del servidor
- ☐ d) Cifra automáticamente todos los cookies del servidor

---

### C.3 PREGUNTAS DE COMPLETAR

Completa los espacios en blanco con la palabra o frase correcta:

**C.3.1** El proceso de almacenamiento de contraseñas usa __________ (no cifrado), porque es un proceso __________ que no permite obtener el dato original.

**C.3.2** La "sal" en bcrypt es un valor __________ y __________ por usuario que elimina la posibilidad de usar __________ precomputadas.

**C.3.3** TLS 1.3 hace obligatorio el uso de __________ (siglas), lo que significa que si la clave privada del servidor se compromete, el tráfico __________ no puede ser descifrado.

**C.3.4** En CGI, los datos del formulario POST se reciben a través de la __________ estándar del script, mientras que los parámetros GET llegan en la variable de entorno __________.

**C.3.5** El código de respuesta HTTP que se debe usar para redirigir permanentemente HTTP a HTTPS es el __________.

**C.3.6** El principio de seguridad que dice que cada usuario o proceso debe tener solo los permisos mínimos necesarios se llama __________ __________.

**C.3.7** Un certificado SSL __________ (autofirmado) es apropiado para __________ y __________, pero NO para __________ porque los navegadores muestran una advertencia de seguridad.

**C.3.8** La organización OWASP clasifica como A07 los fallos de __________ y __________, que incluyen contraseñas débiles, ausencia de MFA y sesiones que no expiran.

---

# SECCIÓN D — PREGUNTAS DE ANÁLISIS

### Nivel Intermedio

**D.1** Lee el siguiente fragmento de código Python CGI. Identifica y describe **5 vulnerabilidades** de seguridad específicas que contiene:

```python
#!/usr/bin/env python3
import cgi
import pymysql

print("Content-Type: text/html\n")

form = cgi.FieldStorage()
user = form.getvalue("user")
pwd  = form.getvalue("pwd")

conn = pymysql.connect(host="db.empresa.com", user="admin", 
                       password="Admin@2024!", database="empresa")
cursor = conn.cursor()
sql = f"SELECT * FROM empleados WHERE usuario='{user}' AND clave='{pwd}'"
cursor.execute(sql)
row = cursor.fetchone()

if row:
    print(f"<h1>Acceso concedido a: {user}</h1>")
    print(f"<p>Datos del empleado: {row}</p>")
else:
    print(f"<h1>Acceso denegado. Usuario: {user} no existe.</h1>")
conn.close()
```

| # | Vulnerabilidad identificada | Descripción del riesgo | Cómo corregirla |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |

---

**D.2** Analiza la siguiente política de contraseñas de una empresa e identifica qué está bien y qué está mal según las guías NIST SP 800-63B:

> *"Política de contraseñas de TechCorp SA: Las contraseñas deben tener exactamente 8 caracteres. Deben incluir al menos una letra mayúscula, una minúscula, un número y un símbolo. Las contraseñas deben cambiarse obligatoriamente cada 30 días. El sistema almacena los últimos 3 passwords para no repetirlos. El campo acepta cualquier combinación de caracteres ASCII."*

| Elemento de la política | ¿Correcto o incorrecto? | ¿Por qué? |
|---|---|---|
| Exactamente 8 caracteres | | |
| Cambio obligatorio cada 30 días | | |
| Historial de 3 passwords | | |
| Complejidad obligatoria (mayus+minus+num+simb) | | |

---

### Nivel Avanzado

**D.3** Escenario profesional:

> *Eres el desarrollador líder de una startup fintech peruana que acaba de lanzar su MVP de una app de préstamos personales. El sistema tiene un módulo de login básico. La startup va a solicitar una licencia de operaciones a la SBS (Superintendencia de Banca, Seguros y AFP). La SBS exige cumplimiento con estándares mínimos de seguridad para sistemas financieros.*

**D.3.1** ¿Qué estándares internacionales de seguridad son relevantes para este contexto? Menciona al menos 3.

_________________________________________________________________________

_________________________________________________________________________

_________________________________________________________________________

**D.3.2** Diseña la especificación formal de seguridad completa para el módulo de login de esta fintech. Usa la estructura de 7 componentes vista en clase:

| Componente | Tu especificación |
|---|---|
| **Activos a proteger** | |
| **Sujetos (roles)** | |
| **Objetos (recursos controlados)** | |
| **Operaciones permitidas/denegadas** | |
| **Condiciones de acceso** | |
| **Mecanismos técnicos** | |
| **Respuesta ante violación** | |

**D.3.3** Justifica por qué elegiste bcrypt (y no MD5, SHA-256 o AES) para almacenar contraseñas en este sistema financiero. Usa argumentos técnicos y de cumplimiento normativo.

_________________________________________________________________________

_________________________________________________________________________

_________________________________________________________________________

_________________________________________________________________________

---

**D.4** Pregunta de investigación (para completar fuera de clase):

La empresa Adobe sufrió en 2013 una de las brechas de datos más analizadas académicamente, no solo por el número de afectados (153 millones de registros) sino por el **tipo de error criptográfico** cometido.

**D.4.1** Investiga: ¿cómo Adobe almacenaba las contraseñas de sus usuarios? ¿Por qué fue un error tan grave?

_________________________________________________________________________

_________________________________________________________________________

_________________________________________________________________________

**D.4.2** Explica por qué el hint de contraseña (pista de contraseña) que Adobe guardaba junto al hash **empeoró significativamente** el ataque:

_________________________________________________________________________

_________________________________________________________________________

**D.4.3** ¿Qué debió haber hecho Adobe en su lugar?

_________________________________________________________________________

_________________________________________________________________________

---

# SECCIÓN E — ACTIVIDAD COLABORATIVA: ESPECIFICACIÓN FORMAL DE SEGURIDAD

**Integrantes del grupo:**
1. ____________________________________________________________
2. ____________________________________________________________
3. ____________________________________________________________
4. ____________________________________________________________

**Sistema asignado:** ____________________________________________________________

---

### E.1 ESPECIFICACIÓN FORMAL — MÓDULO DE LOGIN

Completa esta especificación para el sistema asignado por el docente:

```
╔══════════════════════════════════════════════════════════════════════╗
║        ESPECIFICACIÓN FORMAL DE SEGURIDAD — MÓDULO LOGIN            ║
║        Sistema: ________________________________________________     ║
╠══════════════════════════════════════════════════════════════════════╣
║ ACTIVOS                                                              ║
║ (¿Qué datos se protegen en el proceso de login?)                     ║
║                                                                      ║
║ ●                                                                    ║
║ ●                                                                    ║
║ ●                                                                    ║
╠══════════════════════════════════════════════════════════════════════╣
║ SUJETOS                                                              ║
║ (¿Quiénes acceden? ¿Con qué roles diferenciados?)                   ║
║                                                                      ║
║ Rol 1: ___________________ → Permisos: _________________________     ║
║ Rol 2: ___________________ → Permisos: _________________________     ║
║ Rol 3: ___________________ → Permisos: _________________________     ║
╠══════════════════════════════════════════════════════════════════════╣
║ OBJETOS                                                              ║
║ (¿A qué recursos controla el acceso el módulo de login?)            ║
║                                                                      ║
║ ●                                                                    ║
║ ●                                                                    ║
╠══════════════════════════════════════════════════════════════════════╣
║ MECANISMOS TÉCNICOS                                                  ║
║                                                                      ║
║ Algoritmo hash: _________________ Factor/parámetros: ___________     ║
║ Protocolo TLS: __________________ Cipher suites: _______________     ║
║ Política de contraseñas:                                             ║
║   Longitud mínima: ___ Complejidad: ___________________________      ║
║ Política de bloqueo:                                                 ║
║   Máx intentos: ___ Duración bloqueo: ____ Tipo: ______________      ║
║ Expiración de sesión: inactividad ___ / máximo _____________        ║
║ MFA: ☐ No ☐ Sí → Tipo: ______________________________________       ║
╠══════════════════════════════════════════════════════════════════════╣
║ CONDICIONES DE ACCESO                                                ║
║ (Bajo qué circunstancias se permite/deniega el acceso)              ║
║                                                                      ║
║ ●                                                                    ║
║ ●                                                                    ║
╠══════════════════════════════════════════════════════════════════════╣
║ LOGGING DE SEGURIDAD                                                 ║
║ (¿Qué eventos se registran? ¿Con qué datos?)                        ║
║                                                                      ║
║ Evento 1: ___________________________________________________        ║
║ Evento 2: ___________________________________________________        ║
║ Evento 3: ___________________________________________________        ║
╠══════════════════════════════════════════════════════════════════════╣
║ RESPUESTA ANTE VIOLACIÓN                                             ║
║ (¿Qué ocurre cuando se detecta un intento de ataque?)               ║
║                                                                      ║
║ ●                                                                    ║
║ ●                                                                    ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

### E.2 JUSTIFICACIÓN DE DECISIONES DE DISEÑO

Para cada decisión técnica que tomaron en la especificación, justifiquen por qué la tomaron:

| Decisión técnica tomada | Justificación (¿por qué esta y no otra?) |
|---|---|
| Algoritmo de hash elegido | |
| Versión de TLS elegida | |
| Política de bloqueo definida | |
| Decisión sobre MFA | |

---

### E.3 CASO EXTREMO — ANÁLISIS GRUPAL

Respondan juntos: ¿Qué pasaría si un atacante obtiene acceso directo a la base de datos de su sistema (sin pasar por el login)? ¿Qué información podría obtener y qué NO podría obtener con la especificación que diseñaron?

**Lo que el atacante PODRÍA obtener:**

_________________________________________________________________________

_________________________________________________________________________

**Lo que el atacante NO PODRÍA obtener (gracias a su especificación):**

_________________________________________________________________________

_________________________________________________________________________

---

# SECCIÓN F — CIERRE Y METACOGNICIÓN

### F.1 LISTA REVISADA (Volvemos a la Sección B.1)

Vuelve a tu lista de la Sección B.1 (¿qué hace inseguro un login?). Ahora agrega todo lo que descubriste durante la clase:

**Nuevas razones identificadas durante la clase:**

7. _______________________________________________
8. _______________________________________________
9. _______________________________________________
10. _______________________________________________
11. _______________________________________________
12. _______________________________________________

---

### F.2 PREGUNTAS DE SÍNTESIS

Responde brevemente:

**F.2.1** ¿Cuál es la diferencia esencial entre hash y cifrado? ¿Por qué se usa hash para contraseñas?

_________________________________________________________________________

_________________________________________________________________________

**F.2.2** ¿Qué hace bcrypt diferente a SHA-256 para resistir ataques de fuerza bruta?

_________________________________________________________________________

_________________________________________________________________________

**F.2.3** ¿Qué versión de TLS deben usar y por qué las anteriores están descartadas?

_________________________________________________________________________

_________________________________________________________________________

**F.2.4** ¿Cuál fue el error más crítico del código CGI inseguro que analizamos hoy?

_________________________________________________________________________

_________________________________________________________________________

---

### F.3 METACOGNICIÓN PERSONAL (Solo para ti)

Responde honestamente. Nadie más verá estas respuestas:

**F.3.1** ¿Qué fue lo más sorprendente o revelador de la sesión de hoy?

_________________________________________________________________________

_________________________________________________________________________

**F.3.2** ¿Qué concepto todavía no tienes completamente claro?

_________________________________________________________________________

_________________________________________________________________________

**F.3.3** ¿Qué error de seguridad en código hoy reconoces que podrías haber cometido (o has cometido) antes de esta clase?

_________________________________________________________________________

_________________________________________________________________________

**F.3.4** ¿Cómo cambiaría tu forma de implementar un login después de esta sesión?

_________________________________________________________________________

_________________________________________________________________________

---

### F.4 TAREA PARA LA SEMANA 3 — AUDITORÍA DE LOGIN EN CAMPO

**Instrucción:** Elige un sistema real (app, sitio web, sistema universitario) y audita su formulario de login desde afuera (sin intentar acceder sin autorización). Responde:

**Sistema auditado:** ___________________________________________________________

**URL / Nombre de la app:** ______________________________________________________

| Criterio de auditoría | Resultado | Herramienta usada |
|---|---|---|
| ¿Usa HTTPS? | ☐ Sí ☐ No | |
| ¿Qué versión de TLS usa? | | SSL Labs |
| ¿Calificación SSL Labs? | A / B / C / D / F | ssllabs.com/ssltest |
| ¿Formulario usa POST o GET? | | Inspección de código |
| ¿Tiene política de bloqueo de intentos? | | Intento manual |
| ¿Ofrece MFA (2FA)? | ☐ Sí ☐ No | |
| ¿Muestra mensajes de error genéricos? | ☐ Sí ☐ No | |

**Observación más importante (¿qué encontraste?):**

_________________________________________________________________________

_________________________________________________________________________

**Recomendación de mejora:**

_________________________________________________________________________

_________________________________________________________________________

---

*Guía de Trabajo — Semana 2 | Programación Segura DD281 | Universidad Autónoma del Perú | 2026-1*
