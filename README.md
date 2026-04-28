# Pages CMS

CMS Git-based con interfaz web alojada en `app.pagescms.org`. No requiere ningún servidor propio ni Docker. El contenido se guarda como archivos Markdown en este repositorio de GitHub.

## Arquitectura

```
Navegador → app.pagescms.org (plataforma SaaS)
app.pagescms.org → GitHub API → commits a docs/
GitHub Pages → Jekyll → frontend público
```

## Dependencia de GitHub

**El administrador necesita GitHub.** Los colaboradores con rol de escritura también. Sin embargo, Pages CMS tiene un sistema de invitación propio donde usuarios sin cuenta de GitHub pueden acceder con email.

## Puesta en marcha

### No requiere Docker ni servidor propio

El panel ya está disponible en:

**https://app.pagescms.org/cainmartinez/pages_cms/main/collection/posts**

El frontend (sitio público) se despliega automáticamente en GitHub Pages:

**https://cainmartinez.github.io/PAGES_CMS/**

## Login y acceso

### Administrador

1. Ir a https://app.pagescms.org
2. **"Sign in with GitHub"** → autorizar Pages CMS
3. Seleccionar el repo `PAGES_CMS`
4. Ya se puede editar

El admin debe tener permisos de escritura en el repo.

### Colaboradores (sin cuenta de GitHub)

Pages CMS permite invitar colaboradores que **no tienen cuenta de GitHub**:

1. En el panel → `Settings → Collaborators`
2. Invitar por email
3. El colaborador recibe un link y accede con email/contraseña directamente en `app.pagescms.org`

Esto es la principal ventaja sobre Decap y Sveltia — no todos los editores necesitan saber qué es GitHub.

## Forma de trabajo

1. Editor accede a https://app.pagescms.org
2. Crea o edita un artículo desde el panel visual
3. Al guardar, Pages CMS hace un commit al repo con el mensaje configurado en `.pages.yml`
4. GitHub Pages detecta el push → construye el Jekyll → actualiza el sitio (~1 min)

## Contenido

Los artículos viven en `docs/` como archivos `.md`:

```
docs/
  2026-04-28-nombre-del-articulo.md
```

Las imágenes se guardan en `assets/images/`.

## Campos disponibles en el editor

- Título, Fecha de publicación, Última modificación
- Estado: `draft` / `review` / `published`
- Destacado (boolean)
- Etiquetas (lista)
- Resumen (excerpt)
- Imagen de portada
- Autor (nombre + avatar)
- Contenido (rich-text con editor visual)

## Configuración

- Panel CMS: `.pages.yml`
- Jekyll (frontend): `_config.yml`
- Deploy: branch `main` → raíz del repo (configurado en `Settings → Pages`)

## Ventaja principal

Es el único de los CMSes comparados que permite editores **sin cuenta de GitHub**. Ideal para equipos donde solo el técnico gestiona el repo y el resto solo edita contenido.