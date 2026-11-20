<p align="center"> <picture> <source media="(prefers-color-scheme: dark)" srcset="sitio/logo.svg"> <img src="sitio/logo.svg" alt="Ruta Local" height="80"> </picture> </p>

# Ruta Local · Catálogo digital


> **Caso simulado.** Ruta Local S.A.S. es una organización ficticia creada para el Reto EstudIA (Nube e infraestructura · Capa 2). Todo el contenido es ficticio y no contiene datos personales, credenciales ni información de clientes.
 
Este repositorio publica el catálogo de experiencias de Ruta Local en **una sola dirección estable**, con control de versiones, aprobación de cambios y respaldo recuperable.
 
**Sitio publicado:** 

---
 
## El problema que resolvemos
 
El catálogo circulaba como archivos por correo y WhatsApp. Había varias versiones, nadie sabía cuál era la vigente y no existía forma de recuperar una versión anterior después de un error.
 
## La solución en una frase
 
El sitio vive en este repositorio, se publica con **GitHub Pages**, cada cambio pasa por un **pull request** aprobado por la coordinación, **GitHub Actions** valida y publica automáticamente, y cada versión oficial queda guardada como **release** con un zip de respaldo.
 
---
 
## Estructura del repositorio
 
```
ruta-local/
├── sitio/                    ← el catálogo (lo que se publica)
│   ├── index.html
│   └── estilos.css
├── .github/
│   └── workflows/
│       ├── validar.yml       ← revisa cada pull request
│       ├── publicar.yml      ← publica en GitHub Pages después del merge
│       └── respaldo.yml      ← crea el zip de cada release
└── README.md
```
 
## Roles y permisos
 
| Rol | Quién | Permiso en GitHub | Qué puede hacer |
|---|---|---|---|
| Visitantes y aliados | Cualquier persona | Ninguno (sin cuenta) | Ver el catálogo en la URL |
| Editor | Equipo de contenido | Write | Proponer cambios con pull requests |
| Coordinación | Coordinación de operaciones | Maintain / Admin | Aprobar, hacer merge, crear releases y restaurar |
 
Reglas que aplican a todos:
 
- Nadie publica directamente en `main`: todo cambio entra por un pull request con **1 aprobación** de otra persona.
- La validación automática (`validar`) debe estar en verde antes de aceptar un cambio.
- Todos los miembros de la organización tienen **2FA** (verificación en dos pasos) activado.
---
 
## Cómo actualizar el catálogo
 
1. Abre `sitio/index.html` y toca el lápiz (*Edit this file*).
2. Haz el cambio.
3. Toca *Commit changes* → elige **Create a new branch for this commit and start a pull request** → *Propose changes*.
4. Escribe un título claro (ej. "Actualiza horario del Recorrido Centro") y toca *Create pull request*.
5. Espera el ✓ verde de la validación y pide la revisión a la coordinación.
6. La coordinación revisa en *Files changed*, aprueba y hace *Merge pull request*.
7. En 1 a 2 minutos el cambio aparece en la URL. Verifícalo en una ventana de incógnito.
   
## Cómo se marcan las versiones oficiales
 
Una **release** marca una versión oficial del catálogo (v1, v2…). **La crea solo la coordinación y solo cuando hay un hito**, por ejemplo un catálogo nuevo; no se crea por cada cambio pequeño.
 
1. *Releases* → *Draft a new release*.
2. *Choose a tag* → escribir la versión (ej. `v2`) → *Create new tag*.
3. Escribir título y notas → *Publish release*.
4. En cerca de un minuto, el workflow de respaldo adjunta `ruta-local-v2.zip` a la release.
   
## Cómo restaurar una versión anterior
 
Si se publicó algo incorrecto, hay tres caminos. Usa el primero que funcione:
 
1. **Revert del pull request:** abre el PR que causó el problema → botón *Revert* → aprueba y haz merge del nuevo PR.
2. **Volver a publicar una versión oficial:** pestaña *Actions* → *Publicar sitio* → *Run workflow* → escribe la versión buena (ej. `v1`) → aprobar.
3. **Descargar el respaldo:** en *Releases*, descarga el zip de la versión buena.
Después de restaurar, verifica en una ventana de incógnito que el pie de página muestre la versión esperada.
 
---
 
## Automatización (GitHub Actions)
 
| Workflow | Se activa cuando… | Qué hace |
|---|---|---|
| `validar.yml` | Se abre un pull request | Revisa que exista `index.html`, que el HTML esté bien escrito y que no haya enlaces rotos. Si falla, no se puede hacer merge |
| `publicar.yml` | Hay merge a `main`, o alguien toca *Run workflow* | Escribe la versión y la fecha en el pie de página, publica en GitHub Pages y verifica que el sitio responda |
| `respaldo.yml` | Se publica una release | Crea el zip de esa versión y lo adjunta a la release |
 
## Costos
 
**USD 0.** El repositorio es público, GitHub Pages es gratuito para repositorios públicos y GitHub Actions no tiene costo en repositorios públicos. No se compró dominio ni ningún servicio.
 
## Seguridad
 
- No se guardan contraseñas, llaves de acceso ni archivos con secretos en este repositorio.
- 2FA obligatorio para todos los miembros de la organización.
- Los workflows usan permisos mínimos (bloque `permissions:` de cada archivo).
---
 
## Equipo
 
| Rol en el equipo | Responsabilidad en el proyecto |
|---|---|
| Coordinadora | Organización, repositorio, workflows y aprobaciones |
| Investigador | Costos, límites, seguridad y segundo aprobador |
| Diseñador | Contenido y versiones del catálogo |
| Documentador | Bitácora, evidencias y runbooks |
| Comunicador | Presentación y pruebas como visitante |
 
## Estado
 
- [ ] v1 publicada
- [ ] Workflows funcionando
- [ ] Reglas de protección de `main` activas
- [ ] v2 publicada mediante pull request
- [ ] Restauración probada y documentada en la bitácora
      
Al terminar el reto, el repositorio se archivará y GitHub Pages se desactivará, como indican las condiciones de uso.
 
