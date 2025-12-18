# React + Vite
**Curso**: Programación Integrativa de Componentes Web – NRC 29334
**Integrantes**: 
 ---
# Página informativa en React - NexusTech Solutions

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.
## 📄 Descripción del Proyecto
Este proyecto es una **Landing Page Informativa** construida con **React** y **Vite**. 
El objetivo principal fue aplicar los conceptos de ingeniería de software aprendidos en clase, como la **componentización**, el manejo de **estado (useState)**, **efectos secundarios (useEffect)** y el paso de **props** entre componentes padres e hijos.

Currently, two official plugins are available:
La página simula el sitio web de una empresa de tecnología ("NexusTech"), permitiendo al usuario ver servicios, solicitar cotizaciones (que actualizan un contador global) y cambiar entre modo claro y oscuro.

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh
## 💻 Cómo ejecutar localmente

## React Compiler
Para correr este proyecto en tu máquina, sigue estos pasos en tu terminal:

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).
1.  **Instalar las dependencias** (asegúrate de tener Node.js instalado):
    ```bash
    npm install
    ```

## Expanding the ESLint configuration
2.  **Correr el servidor de desarrollo**:
    ```bash
    npm run dev
    ```

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.
3.  Abrir el navegador en la dirección que muestra la terminal (usualmente `http://localhost:5173`).

## 🧩 Lista de Componentes y Hooks

A continuación detallo la arquitectura de componentes que implementé, explicando qué props reciben y qué hooks utilizan.

### 1. `App` (Contenedor Principal)
Es el componente raíz que orquesta toda la aplicación.
*   **Hooks**:
    *   `useState`: Para manejar el tema (`isDarkMode`), la lista de servicios (`services`) y el contador global de cotizaciones (`totalQuotes`).
    *   `useEffect`: Para cargar los datos del JSON (`services.json`) al iniciar la página y para guardar la preferencia de tema en el `localStorage`.
*   **Props**: No recibe props, pero pasa muchas a sus hijos.

### 2. `Header`
La barra de navegación superior.
*   **Props que recibe**:
    *   `isDarkMode`: Boolean para saber qué icono mostrar (sol/luna).
    *   `onToggleTheme`: Función para cambiar el tema desde el botón.
    *   `totalQuotes`: Número entero para mostrar el contador global.
*   **Hooks**: No tiene estado propio, es puramente presentacional (stateless).

### 3. `Hero`
La sección de bienvenida con el título principal.
*   **Props**: Ninguna.
*   **Hooks**:
    *   `useState`: Usa una variable `showMore` para controlar si se muestra o no un texto adicional cuando el usuario hace clic en "Mostrar más".

### 4. `ServiceCard`
Tarjeta individual que muestra la información de cada servicio.
*   **Props que recibe**:
    *   `title`, `description`, `priceTier`, `icon`: Datos del servicio.
    *   `onRequestQuote`: Función callback para notificar al padre (`App`) que se pidió una cotización.
*   **Hooks**:
    *   `useState`:
        *   `quoteCount`: Un contador *local* para saber cuántas veces se pidió cotización de *esa* tarjeta específica.
        *   `isExpanded`: Para el botón de "Leer más" en descripciones largas.

### 5. `Stats`
Sección de estadísticas rápidas al final de la página.
*   **Props**: Ninguna.
*   **Hooks**:
    *   `useState`: Maneja un contador simple de "Likes" o interés (`likes`), independiente del resto de la app.

### 6. `Footer`
Pie de página con enlaces y contacto.
*   **Props**: Ninguna.
*   **Hooks**: Ninguno (es estático).
