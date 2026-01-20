# Actividad 2 — Reporte de Buenas Prácticas y Documentación de Código

**Alumno:** CruzBautistaGeovanny
**Grupo:** G3  
**Fecha:** 14 de enero  
**Unidad:** 1

## 1. Objetivo del reporte
- El objetivo de este reporte es aplicar buenas prácticas de codificación y documentación de código para mejorar la claridad, estructura y mantenimiento del software. Se presentan ejemplos prácticos que muestran la diferencia entre un código mal escrito y uno correctamente estructurado.


## 2. Buenas prácticas de codificación
### 2.1 Nombres de variables
- Reglas:
 Usar nombres claros y descriptivos.
- Evitar abreviaturas innecesarias.
- Mantener un estilo consistente.
- El nombre debe reflejar su propósito.

- Ejemplo correcto:
int totalUsuarios;
double promedioCalificaciones;

Ejemplo incorrecto:
int x;
double a;

### 2.2 Comentarios
- Cuándo comentar:
Para explicar partes complejas del código.
Para describir métodos o funciones.
Cuando la lógica no es evidente.
- Qué evitar:
Comentarios obvios.
Comentarios repetitivos.
Comentarios desactualizados.

### 2.3 Estructura del código
- Indentación:
Mantener indentación consistente.
Evitar líneas demasiado largas.
- Modularidad:
Dividir el código en métodos pequeños.
Cada método debe cumplir una sola función.
- Evitar duplicidad:
Reutilizar código mediante funciones.
Evitar copiar y pegar bloques similares.

## 3. Documentación del código
### 3.1 Estándares
- Estándar elegido:
JavaDoc
- Elementos recomendados:
Descripción del método o clase.
Parámetros.
Valor de retorno.
Excepciones.

### 3.2 Herramientas / enfoque
- README / generadores / extensiones:
README.md
JavaDoc
Visual Studio Code
- Ventajas:
Facilitan la comprensión del proyecto.
Mejoran la colaboración.
Ayudan al mantenimiento del código.

## 4. Ejemplos prácticos
### 4.1 Antes / Después (Ejemplo 1)
**Antes:**
int a = 5;
int b = 10;
int c = a + b;

**Después**
int numeroInicial = 5;
int numeroFinal = 10;
int sumaTotal = numeroInicial + numeroFinal;

### 4.2 Antes / Después (Ejemplo 2)

**Antes:**
public void f() {
    System.out.println("Hola");
}

**Después**
public void mostrarSaludo() {
    System.out.println("Hola");
}

### 4.3 Ejemplo de documentación
/**
 * Muestra un mensaje de bienvenida al usuario.
 */
public void mostrarBienvenida() {
    System.out.println("Bienvenido al sistema");
}

## 5. Recomendaciones finales

Usar nombres claros y descriptivos.
Comentar solo cuando sea necesario.
Mantener el código limpio y ordenado.
Documentar correctamente el código.
Revisar el código antes de entregarlo.

## 6. Fuentes consultadas
Oracle Java Documentation – https://docs.oracle.com/en/java/
Robert C. Martin – Clean Code
Markdown Guide – https://www.markdownguide.org/