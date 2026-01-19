# PC Futbol 7 Remake

## 1. Descripción del proyecto

**PC Futbol 7 Remake** es un juego de gestión de fútbol inspirado en el clásico PC Fútbol 7. El jugador asume el rol de manager de un club, encargándose de la gestión integral: plantillas, alineaciones, fichajes, economía, instalaciones y evolución histórica del club.

El juego se basa íntegramente en menús y pantallas de gestión. Los partidos no se representan gráficamente, sino que se **simulan mediante lógica estadística**, mostrando resultados, eventos y consecuencias deportivas y económicas.

El objetivo es ofrecer una experiencia profunda, offline-first, multiplataforma y extensible, permitiendo carreras de múltiples temporadas que evolucionan con el tiempo.

---

## 2. Equipo de desarrollo

El proyecto será desarrollado por un equipo de 3 personas:

* **Mapiedra** – Desarrollo principal, arquitectura, motor de simulación y decisiones técnicas
* **Benji** – Apoyo en desarrollo, datos, balanceo y validación
* **Derlis** – Apoyo en desarrollo, lógica de juego y testeo

---

## 3. Tecnología a utilizar

### Lenguaje y enfoque

* **JavaScript / TypeScript**
* Arquitectura **SPA (Single Page Application)**

### Frontend

* HTML5 + CSS3 + JavaScript
* Framework SPA (Vue / React / Svelte – a decidir)
* Estado centralizado
* Navegación sin recargas

### Plataformas objetivo (un solo desarrollo)

* **Web** (SPA)
* **PWA** (instalable, offline)
* **Desktop**: Windows, macOS y Linux mediante **Electron**
* **Mobile (opcional)**: Android / iOS mediante **Capacitor**

No se utilizarán motores gráficos ni frameworks de juegos (Unity, Godot, Phaser quedan descartados).

---

## 4. Planteamiento general de desarrollo

### Tipo de aplicación

* Juego de gestión basado en datos
* Sin simulación 3D ni renderizado gráfico
* Lógica pura + interfaces

### Simulación

* Los partidos se simulan mediante algoritmos basados en estadísticas y aleatoriedad controlada
* Los resultados afectan a jugadores, clubes, economía y palmarés

---

## 5. Datos del juego

### 5.1 Datos base (estáticos)

* Ligas, equipos, jugadores iniciales, reglas y calendarios
* Distribuidos con el juego en formato **JSON**
* Read-only durante la partida
* Cada temporada es un dataset independiente

Ejemplos:

* Temporada 2025/2026
* Temporada 2026/2027

### 5.2 Actualización de datos

* Los datos reales se obtienen desde una API externa
* Se procesan mediante una **herramienta interna exclusiva para desarrolladores**
* Frecuencia: una vez al año
* Cada actualización implica una nueva versión del juego

---

## 6. Partidas guardadas y modelo de datos

### Separación clave

* **Identidad**: datos inmutables (nombre, fecha de nacimiento, nacionalidad)
* **Estado**: datos dinámicos (edad, estadísticas, equipo, historial, economía)

Al iniciar una partida:

* El jugador selecciona una temporada
* Todos los datos base se **duplican** en el archivo de guardado
* A partir de ese momento, la partida es totalmente independiente

### Guardado

* **Web / PWA**: IndexedDB
* **Desktop / Mobile**: filesystem local

### Exportar / Importar

* Las partidas pueden exportarse a un archivo `.save`
* Formato interno: JSON comprimido (ZIP)
* Permite copias de seguridad y migración entre dispositivos

---

## 7. Publicación y distribución

### Hosting web

* **GitHub Pages**
* Hosting estático, gratuito y con HTTPS
* Ideal para SPA y PWA

### PWA

* Service Worker
* Caché offline
* Instalación como app
* Juego funcional sin conexión

### Desktop

* Empaquetado mediante **Electron**
* Acceso al sistema de archivos
* Distribución como instalador

### Mobile (fase posterior)

* Empaquetado mediante **Capacitor**
* Android e iOS

---

## 8. Gestión de tareas e incidencias

### GitHub Issues

Se utilizarán para:

* Bugs
* Nuevas funcionalidades
* Mejoras
* Balanceo
* Ideas

Uso de etiquetas para clasificación y priorización.

---

## 9. Gestión del proyecto

### GitHub como plataforma central

* Código fuente
* Documentación
* Issues
* Roadmap
* Versiones

### GitHub Projects

* Tableros tipo Kanban
* Organización por versiones y milestones

### Milestones

* v0.1 – Base jugable
* v0.2 – Economía y fichajes
* v0.3 – Varias temporadas
* v1.0 – Primera versión estable

---

## 10. Filosofía del proyecto

* Offline-first
* Data-driven
* Modular y extensible
* Multiplataforma
* Inspirado en el PC Fútbol clásico
* Preparado para crecer y evolucionar con los años
