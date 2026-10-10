<div align="center">

<img src="docs/assets/banner.svg" alt="MISTHY · Seguridad ciudadana 360° para Lima" width="100%"/>

<a href="https://github.com/CODERT0PH/MISTHY-">
  <img src="https://readme-typing-svg.demolab.com?font=Manrope&weight=700&size=22&duration=3200&pause=900&color=6D28D9&center=true&vCenter=true&width=640&lines=Como+el+Misti+vigila+Arequipa%2C+Misthy+vigila+tu+cuadra;App+m%C3%B3vil+%C2%B7+Misthy+Web+%C2%B7+Misthy+Command;Piloto%3A+Villa+El+Salvador%2C+Lima" alt="Como el Misti vigila Arequipa, Misthy vigila tu cuadra"/>
</a>

<p>
  <img src="https://img.shields.io/badge/estado-en%20dise%C3%B1o-6D28D9?style=for-the-badge" alt="Estado: en diseño"/>
  <img src="https://img.shields.io/badge/piloto-Villa%20El%20Salvador-2563EB?style=for-the-badge" alt="Piloto: Villa El Salvador"/>
  <img src="https://img.shields.io/badge/docs-Cap%C3%ADtulos%20I%E2%80%93IV-0F172A?style=for-the-badge" alt="Documentación: Capítulos I a IV"/>
</p>
<p>
  <a href="https://www.figma.com/design/MNhixqFUFzjBqxVnzp5dTJ"><img src="https://img.shields.io/badge/Figma-Product%20Design-6D28D9?style=flat-square&logo=figma&logoColor=white" alt="Figma"/></a>
  <img src="https://img.shields.io/badge/rama-develop-2563EB?style=flat-square&logo=git&logoColor=white" alt="Rama develop"/>
  <img src="https://img.shields.io/github/last-commit/CODERT0PH/MISTHY-/develop?style=flat-square&color=1E293B&label=%C3%BAltimo%20commit" alt="Último commit"/>
  <img src="https://img.shields.io/badge/autor-CODERT0PH-0F172A?style=flat-square&logo=github&logoColor=white" alt="Autor: CODERT0PH"/>
</p>

<p>
  <a href="#-qué-es-misthy">Qué es</a> ·
  <a href="#-ecosistema">Ecosistema</a> ·
  <a href="#-stack-tecnológico">Stack</a> ·
  <a href="#-documentación">Documentación</a> ·
  <a href="#-diseño">Diseño</a> ·
  <a href="#-autor">Autor</a>
</p>

</div>

---

## 🌋 Qué es MISTHY

**MISTHY** es un SaaS de seguridad ciudadana 360° para Lima, con piloto en **Villa El Salvador**. Une una app móvil para el ciudadano, **Misthy Web** para recuperar el control tras un robo y **Misthy Command**, el dashboard para municipalidades y serenazgo. No es otra app de botón de pánico: es la capa de datos y respuesta en tiempo real entre ciudadano, comunidad y autoridades.

<table>
  <tr>
    <td align="center" width="25%">📱<br/><b>Robo al paso</b><br/><sub>Rastreo persistente por red Mesh, alarma, bloqueo y wipe remoto</sub></td>
    <td align="center" width="25%">🔐<br/><b>Asalto con coacción</b><br/><sub>PIN de coacción que abre una bóveda señuelo y alerta en silencio</sub></td>
    <td align="center" width="25%">🚶‍♀️<br/><b>Persecución y acoso</b><br/><sub>Falso Acompañante con IA y rutas a Puntos Misthy</sub></td>
    <td align="center" width="25%">⚖️<br/><b>Impunidad</b><br/><sub>Expediente probatorio PDF listo para la comisaría</sub></td>
  </tr>
</table>

## 🧩 Ecosistema

| Producto | Para quién | Qué hace |
|---|---|---|
| 📱 **Misthy App** | Ciudadano | Mapa Vivo, Pánico, Viaje Seguro, Anti-Robo, PIN de Coacción, Bóveda, Comunidad y Falso Acompañante (módulos M1–M8) |
| 🌐 **Misthy Web** | Ciudadano sin su celular | Acceso de emergencia con correo + LLAVE MISTHY, rastreo en vivo, Lockdown, sirena, alerta PNP y aviso a contactos |
| 🛰️ **Misthy Command** | Municipalidades y serenazgo (B2B/B2G) | Monitor en vivo, analítica e IA, gestión comunitaria, integración PNP y administración |

```text
Misthy App (Flutter) ──┐
Misthy Web (Vue) ──────┼─► API REST (Node.js) ─► SQL Server (usuarios, suscripciones, pagos)
Misthy Command (Vue) ──┘        └──► Firebase / Supabase (tiempo real)
```

## 🧰 Stack tecnológico

<div align="center">

<a href="https://skillicons.dev"><img src="https://skillicons.dev/icons?i=flutter,dart,vue,vite,nodejs,firebase,supabase,figma,git,github&theme=dark" alt="Flutter, Dart, Vue, Vite, Node.js, Firebase, Supabase, Figma, Git, GitHub"/></a>

<img src="https://img.shields.io/badge/Flutter-Misthy%20App-2563EB?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter"/>
<img src="https://img.shields.io/badge/Vue%203-Misthy%20Web%20%26%20Command-6D28D9?style=for-the-badge&logo=vuedotjs&logoColor=white" alt="Vue 3"/>
<img src="https://img.shields.io/badge/Node.js-API%20REST-0F172A?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js"/>
<img src="https://img.shields.io/badge/SQL%20Server-datos-1E293B?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" alt="SQL Server"/>
<img src="https://img.shields.io/badge/Firebase%20%7C%20Supabase-tiempo%20real-5B21B6?style=for-the-badge&logo=supabase&logoColor=white" alt="Firebase o Supabase"/>

</div>

## 📚 Documentación

| Capítulo | Contenido |
|---|---|
| [Capítulo I · Introducción](docs/capitulo-1/README.md) | 1.1 Startup Profile · 1.2 Solution Profile (problemática, Lean UX) · 1.3 Segmentos objetivo |
| [Capítulo II · Requirements Elicitation & Analysis](docs/capitulo-2/README.md) | 2.1 Competidores · 2.2 Entrevistas · 2.3 Needfinding · 2.4 EventStorming · 2.5 Ubiquitous Language |
| [Capítulo III · Requirements Specification](docs/capitulo-3/README.md) | 3.1 User Stories · 3.2 Impact Mapping · 3.3 Product Backlog |
| [Capítulo IV · Product Design](docs/capitulo-4/README.md) | 4.1 Style Guidelines · 4.2 Information Architecture · 4.3 Landing Page UI Design · 4.4 Web Applications UX/UI Design · 4.5 Web Applications Prototyping |

Los capítulos comparten las mismas personas (Lucía Rojas, Carlos Mendoza y Rosa Huamán), los mismos user goals (UF1–UF6) y los mismos módulos (M1–M8 de la app, Misthy Web y Misthy Command).

## 🎨 Diseño

<div align="center">
  <img src="docs/capitulo-4/img/portada.png" alt="Portada del Capítulo IV · Product Design" width="80%"/>
</div>

Los diseños viven en Figma: [MISTHY · Capítulo IV Product Design](https://www.figma.com/design/MNhixqFUFzjBqxVnzp5dTJ). Los tokens para desarrollo están en [`docs/capitulo-4/tokens.css`](docs/capitulo-4/tokens.css).

| Token | Color | Uso |
|---|---|---|
| `--brand-primary` | ![#6D28D9](https://img.shields.io/badge/-%236D28D9-6D28D9?style=flat-square) | Marca, botones principales |
| `--brand-secondary` | ![#2563EB](https://img.shields.io/badge/-%232563EB-2563EB?style=flat-square) | Acentos, enlaces, gradiente |
| `--neutral-night` | ![#0F172A](https://img.shields.io/badge/-%230F172A-0F172A?style=flat-square) | Texto principal, fondos oscuros |
| `--surface-lavender` | ![#F3EEFF](https://img.shields.io/badge/-%23F3EEFF-F3EEFF?style=flat-square) | Superficies suaves |
| `--status-emergency` | ![#DC2626](https://img.shields.io/badge/-%23DC2626-DC2626?style=flat-square) | Alertas y pánico (siempre con texto e ícono) |

Tipografía: **Manrope** · Espaciado en base 4 · Radios de 8, 12 y 16 px.

## 📂 Estructura del repositorio

```text
MISTHY-/
├── README.md
└── docs/
    ├── assets/          # banner del README
    ├── capitulo-1/      # Introducción
    ├── capitulo-2/      # Requirements Elicitation & Analysis
    ├── capitulo-3/      # Requirements Specification
    └── capitulo-4/      # Product Design (imágenes y tokens.css)
```

## 👤 Autor

<div align="center">

<a href="https://github.com/CODERT0PH"><img src="https://img.shields.io/badge/GitHub-CODERT0PH-6D28D9?style=for-the-badge&logo=github&logoColor=white" alt="GitHub de CODERT0PH"/></a>

<br/><br/>

<img height="165" src="https://github-readme-stats.vercel.app/api?username=CODERT0PH&show_icons=true&hide_border=true&bg_color=0F172A&title_color=A78BFA&icon_color=6D28D9&text_color=E4E7EC&ring_color=2563EB" alt="GitHub stats de CODERT0PH"/>
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=CODERT0PH&layout=compact&hide_border=true&bg_color=0F172A&title_color=A78BFA&text_color=E4E7EC" alt="Lenguajes más usados de CODERT0PH"/>

<img src="https://streak-stats.demolab.com?user=CODERT0PH&hide_border=true&background=0F172A&ring=6D28D9&fire=2563EB&currStreakLabel=A78BFA&sideLabels=E4E7EC&currStreakNum=FFFFFF&sideNums=FFFFFF&dates=667085" alt="Racha de contribuciones de CODERT0PH"/>

<br/>

<sub>Hecho en Lima por <b>CODERT0PH</b> · © 2026 MISTHY</sub>

</div>
