# manejoDatos

Aplicación **Vue 3 + Vite** que consume la API pública de **Rick and Morty** para listar y explorar personajes. Incluye enrutamiento con Vue Router y manejo de estado con Vuex.

## Tecnologías

- Vue 3 + Vite 7
- Vue Router 4
- Vuex 4
- ESLint + Prettier

## Requisitos

- Node.js `^20.19.0 || >=22.12.0`

## Instalación y ejecución

```sh
# Instalar dependencias
npm install

# Servidor de desarrollo con hot-reload
npm run dev

# Compilar para producción
npm run build

# Previsualizar el build de producción
npm run preview
```

Por defecto la app queda en `http://localhost:5173`.

## Calidad de código

```sh
# Linter (ESLint) con autofix
npm run lint

# Formateo (Prettier)
npm run format
```

## Estructura

```
src/
├── App.vue          # Componente raíz
├── main.js          # Punto de entrada
├── router/          # Definición de rutas
├── store/           # Estado global (Vuex)
├── views/           # Vistas por ruta
└── components/       # Componentes reutilizables (cards)
```
