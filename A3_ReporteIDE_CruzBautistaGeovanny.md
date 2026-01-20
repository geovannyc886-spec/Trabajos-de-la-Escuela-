# Actividad 3 — Configuración de un Entorno de Desarrollo Integrado (IDE)

Alumno: Geovanny Cruz  
Grupo: G3 
Fecha: 15 de enero del 2026  
Unidad: 1 

## 1. IDE seleccionado
- IDE: Visual Studio Code
- Versión: 1.86.2 (versión estable)
- Sistema operativo: Windows 11

## 2. Justificación
- Criterio 1: Visual Studio Code es un IDE gratuito y multiplataforma, lo que permite utilizarlo en diferentes sistemas operativos.
- Criterio 2: Cuenta con un amplio catálogo de extensiones que permiten adaptarlo a distintos lenguajes y necesidades de desarrollo.
- Criterio 3: Integra de forma nativa herramientas de control de versiones como Git y GitHub, facilitando la gestión de proyectos.

## 3. Requisitos previos
- Sistema operativo: Windows 10 o superior.
- Permisos: Permisos de administrador para instalar software.
- Dependencias: Conexión a internet para descargar el IDE, extensiones y herramientas adicionales.

## 4. Instalación (paso a paso)
1. Accedí al sitio oficial https://code.visualstudio.com.
2. Seleccioné la versión compatible con Windows.
3. Descargué el instalador oficial.
4. Ejecuté el archivo descargado.
5. Acepté los términos y condiciones.
6. Seleccioné la opción “Agregar al PATH”.
7. Finalicé la instalación.
8. Abrí Visual Studio Code desde el menú de inicio.

### 4.1 Verificación
- ¿Cómo comprobé que funciona?  
  Se creó y guardó correctamente un archivo nuevo dentro del IDE.
- Evidencia (descripción):  
  El IDE inició sin errores y permitió editar archivos sin fallos.

## 5. Configuración inicial

### 5.1 Ajustes básicos
- Configuración del idioma a español.
- Activación del guardado automático.
- Selección de tema oscuro para mejorar la legibilidad.
- Configuración de fuente y tamaño predeterminados.

### 5.2 Extensiones / plugins

| Extensión/Plugin | Función | Por qué |
|---|---|---|
| Java Extension Pack | Soporte para Java | Facilita el desarrollo y ejecución de programas Java |
| GitHub Pull Requests | Integración con GitHub | Permite administrar repositorios desde el IDE |
| Markdown Preview | Vista previa de Markdown | Facilita la revisión del reporte |

### 5.3 Herramientas adicionales
- Compilador/intérprete: Java Development Kit (JDK 17)
- Prueba: Ejecución de un programa básico sin errores.

## 6. Prueba final (mini-ejercicio)
```txt
public class HolaMundo {
    public static void main(String[] args) {
        System.out.println("Hola Mundo desde Visual Studio Code");
    }
}

## 7. Control de versiones con Git y GitHub
Instalé Git desde https://git-scm.com
.
Configuré Git con:
git config --global user.name "Geovanny Cruz"
git config --global user.email "correo@email.com
"
Creé una carpeta de proyecto.
Inicialicé el repositorio con:
git init
Agregué archivos al stage:
git add .
Realicé el primer commit:
git commit -m "Primer commit del proyecto"
Creé un repositorio en GitHub.
Vinculé el repositorio local con GitHub.
Subí el proyecto usando:
git push origin main

### 8. Conclusiones
La correcta configuración del IDE permite trabajar de forma ordenada y eficiente.
Visual Studio Code, junto con Git y GitHub, facilita el desarrollo, la documentación y el control de versiones, cumpliendo con buenas prácticas profesionales.