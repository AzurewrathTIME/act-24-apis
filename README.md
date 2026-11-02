# 🏫 Sistema Escolar - Primera API en C++

Implementación de rutas dinámicas (endpoints) en el servidor web para generar respuestas en tiempo real, marcando la diferencia entre servir archivos estáticos y generar datos dinámicos.

![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=c%2B%2B&logoColor=white)
![API](https://img.shields.io/badge/API-REST-blue)
![HTTP](https://img.shields.io/badge/HTTP-Endpoints-important)
![Status](https://img.shields.io/badge/status-completado-success)

---

## 📌 Descripción

El servidor ha evolucionado para dejar de ser solo un repositorio de archivos estáticos y ahora incluye una **API (Application Programming Interface)**. Esto permite que el servidor procese rutas especiales (que comienzan con `/api/`) y devuelva respuestas generadas dinámicamente por el código C++, en lugar de leer un archivo del disco.

---

## ✨ Características

- 🛣️ **Rutas dinámicas:** Endpoints bajo el prefijo `/api/`.
- ⚡ **Respuestas en memoria:** Generación de contenido al instante según la lógica del servidor.
- ⏱️ **Manejo de tiempo:** Obtención de la fecha y hora del sistema usando `<ctime>`.
- 🛡️ **Validación de métodos:** Bloqueo de peticiones no permitidas (como POST) devolviendo `405 Method Not Allowed`.
- 🚫 **Manejo de errores de API:** Si un endpoint no existe, devuelve `404 Not Found` en texto plano (no en HTML).

---

## 🛠️ Tecnologías

| Tecnología | Uso |
|------------|-----|
| C++17 | Lógica del servidor y enrutamiento de la API |
| Sockets (TCP) | Comunicación por red |
| Protocolo HTTP/1.1 | Interpretación de verbos (GET) y respuestas |
| `<ctime>` | Generación de la hora del servidor |

---

## 🛣️ Endpoints Disponibles (GET)

| Endpoint | Descripción | Respuesta esperada |
|----------|-------------|-------------------|
| `/api/hola` | Prueba de saludo | `Hola desde C++` |
| `/api/version` | Versión del backend | `Servidor v1.0.0` |
| `/api/hora` | Fecha y hora actual | `2025-01-15 10:30:00` |
| `/api/status` | Health check del servidor | `OK` |
| `/api/cualquiera` | Ruta inexistente | `404 Endpoint no encontrado` |

---

## 🧠 Conceptos aplicados

### Servir Archivos vs. Generar Respuestas Dinámicas

| Aspecto | Archivo Estático (`/`) | Respuesta Dinámica (`/api/`) |
|---------|-----------------------|------------------------------|
| **Origen** | Disco duro (`Public/`) | Memoria (Lógica C++) |
| **Contenido** | Fijo (HTML, CSS, JS) | Variable (se genera en cada petición) |
| **Cambia al...** | Modificar archivo | Cambiar el código fuente |
| **Cacheable** | Sí | No por defecto |
| **Uso típico** | Interfaz visual | Datos, cálculos, estado |

### Enrutamiento (Routing)
El servidor decide qué hacer basándose en la URL:
1. Si la ruta empieza con `/api/`, llama a la función `manejarAPI()`.
2. Si no, busca el archivo en la carpeta `Public/`.

---

## 🚀 Instalación y ejecución

1. Abre la terminal en la carpeta raíz del proyecto.
2. Compila el servidor con soporte para C++17:
   ```bash
   g++ servidor.cpp -o servidor.exe -std=c++17 -lws2_32
   ```
3. Ejecuta el servidor:
   ```cmd
   .\servidor.exe
   ```

---

## 🧪 Cómo probarlo

Puedes probar tu API de dos formas:

### 1. Desde el Navegador
Abre tu navegador y escribe directamente las rutas:
- [http://localhost:8080/api/hola](http://localhost:8080/api/hola)
- [http://localhost:8080/api/hora](http://localhost:8080/api/hora)

### 2. Desde la Terminal (usando `curl`)
Si estás en Windows (PowerShell) o Linux/macOS, puedes usar `curl` para ver las cabeceras de la respuesta HTTP:
```bash
curl -i http://localhost:8080/api/version
```

**Salida esperada:**
```text
HTTP/1.1 200 OK
Content-Type: text/plain; charset=utf-8
Content-Length: 17
Connection: close

Servidor v1.0.0
```

---

## 📁 Estructura del proyecto

```text
Sistema-Escolar/
├── servidor.cpp       <-- Código del servidor web y la API en C++
├── README.md
└── Public/            <-- Carpeta pública (archivos estáticos)
    ├── index.html
    ├── registro.html
    ├── styless.css
    ├── app.js
    └── img/
```

---

## 📄 Licencia

MIT License
