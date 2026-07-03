# Diccionario de Datos - Ejercicios del Modelo Relacional
---

## Ejercicio 1 - Paciente / Expediente

### 4. Diccionario de Datos

**Tabla: Pciente** *(así aparece escrito en la imagen; el nombre correcto sería "Paciente")*

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumPaciente | INT | - | PK, NN | Identificador único del paciente |
| Nombre | VARCHAR | 20 | NN | Nombre del paciente |
| Apellido1 | VARCHAR | 20 | NN | Primer apellido del paciente |
| Apellido2 | VARCHAR | 20 | NN | Segundo apellido del paciente |
| FechaNaci | DATE | - | NN | Fecha de nacimiento del paciente |

**Tabla: Expediente**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumExp | INT | - | PK, NN | Identificador único del expediente |
| FechaApertura | DATE | - | NN | Fecha de apertura del expediente |
| TipoDeSangre | CHAR | 3 | NN | Tipo sanguíneo del paciente |
| IdPaciente | INT | - | FK, NN | Referencia al paciente asociado |

### 5. Relaciones entre Tablas

| Relación | Cardinalidad | Descripción |
| :--- | :---: | :--- |
| Paciente → Expediente | 1:1 | Cada paciente tiene un único expediente y cada expediente pertenece a un único paciente (Min Max 1,1 en ambos extremos según el diagrama E-R) |

### 6. Matriz de Claves Foráneas

| Tabla | Campo FK | Referencia |
| :--- | :--- | :--- |
| Expediente | IdPaciente | Pciente (NumPaciente) |

### 7. Integridad Referencial

| Regla | Descripción |
| :--- | :--- |
| IR-01 | No se puede registrar un expediente para un paciente inexistente |
| IR-02 | No puede existir un paciente sin expediente |

### 8. Reglas del Negocio

| Código | Regla |
| :--- | :--- |
| RN-01 | Cada paciente debe tener exactamente un expediente médico |
| RN-02 | Cada expediente médico pertenece a un único paciente |

### 9. Diagramas

**Diagrama E-R**

![Ejercicio 1 ER]

**Modelo Relacional**

![Ejercicio 1 Relacional](img/Ejercicio1_Relacional.png)

---

## Ejercicio 2 - Profesor / Curso / Especialidad

### 4. Diccionario de Datos

**Tabla: Profesor**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| Nombre | INT | - | FK, NN | *(así aparece en la imagen; por el tipo INT y la marca FK, este campo parece ser en realidad el identificador "NumProfesor" mal rotulado como "Nombre")* |
| Nombre | VARCHAR | 30 | NN | Nombre del profesor |
| Apellido | VARCHAR | 20 | NN | Primer apellido del profesor |
| Apellido2 | VARCHAR | 20 | - | Segundo apellido del profesor |

**Tabla: Curso**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumCurso | INT | - | PK, NN | Identificador único del curso |
| NombreCurso | VARCHAR | 20 | NN | Nombre del curso |
| Creditos | INT | - | NN | Créditos asignados al curso |
| NumProf | INT | - | NN | Profesor que imparte el curso |

**Tabla: Especialidad**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumEsp | INT | - | FK, PK, NN | Identificador de la especialidad *(la imagen la marca como FK y PK a la vez)* |
| NumProf | INT | - | NN | Profesor asociado a la especialidad |
| Nombre | VARCHAR | 30 | NN | Nombre de la especialidad |

### 5. Relaciones entre Tablas

| Relación | Cardinalidad | Descripción |
| :--- | :---: | :--- |
| Profesor → Curso | 1:1 (según etiquetas "1"/"1" del diagrama relacional) | Un profesor imparte un curso |
| Profesor → Especialidad | 1:N | Un profesor puede tener varias especialidades |

### 6. Matriz de Claves Foráneas

| Tabla | Campo FK | Referencia |
| :--- | :--- | :--- |
| Curso | NumProf | Profesor |
| Especialidad | NumEsp / NumProf | Profesor |

### 7. Integridad Referencial

| Regla | Descripción |
| :--- | :--- |
| IR-01 | No se puede registrar un curso con un profesor inexistente |
| IR-02 | No se puede registrar una especialidad para un profesor inexistente |

### 8. Reglas del Negocio

| Código | Regla |
| :--- | :--- |
| RN-01 | Un profesor puede impartir varios cursos |
| RN-02 | Un curso solo puede ser impartido por un profesor |
| RN-03 | Puede existir un profesor que actualmente no imparta cursos |
| RN-04 | Todo curso debe estar asignado a un profesor |

### 9. Diagramas

**Diagrama E-R**

![Ejercicio 2 ER](img/Ejercicio2_ER.png)

**Modelo Relacional**

![Ejercicio 2 Relacional](img/Ejercicio2_Relacional.png)

---

## Ejercicio 3 - Alumno / Materia / Inscribe

### 4. Diccionario de Datos

**Tabla: Alumno**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| IdAlumno | INT | - | NN | Identificador único del alumno |
| Matricula | VARCHAR | 10 | NN | Matrícula institucional |
| Nombre | VARCHAR | 30 | NN | Nombre del alumno |
| Apellido2 | VARCHAR | 20 | NULL | Segundo apellido *(la imagen solo muestra este campo de apellido)* |
| Semestre | INT | - | NN, CK | Semestre actual del alumno |

**Tabla: Matricula** *(así aparece rotulada la tabla en la imagen; por su contenido corresponde a "Materia")*

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| IdMateria | INT | - | NN | Identificador único de la materia |
| NombreMat | VARCHAR | 20 | NN | Nombre de la materia |
| Creditos | INT | - | NN, CK | Créditos asignados a la materia |

**Tabla: Inscribe**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| IdMateria | INT | - | FK, NN | Materia inscrita |
| IdAlumno | INT | - | FK, NN | Alumno inscrito |
| FechaInscripcion | DATE | - | - | Fecha de inscripción |
| CalFinal | DECIMAL | - | - | Calificación final obtenida |

### 5. Relaciones entre Tablas

| Relación | Cardinalidad | Descripción |
| :--- | :---: | :--- |
| Alumno → Inscribe | 1:N | Un alumno puede realizar muchas inscripciones |
| Materia → Inscribe | 1:N | Una materia puede tener muchos alumnos inscritos |

### 6. Matriz de Claves Foráneas

| Tabla | Campo FK | Referencia |
| :--- | :--- | :--- |
| Inscribe | IdAlumno | Alumno (IdAlumno) |
| Inscribe | IdMateria | Materia (IdMateria) |

### 7. Integridad Referencial

| Regla | Descripción |
| :--- | :--- |
| IR-01 | No se puede registrar una inscripción para un alumno inexistente |
| IR-02 | No se puede registrar una inscripción para una materia inexistente |

### 8. Reglas del Negocio

| Código | Regla |
| :--- | :--- |
| RN-01 | Un alumno puede inscribirse en varias materias |
| RN-02 | Una materia puede tener muchos alumnos inscritos |
| RN-03 | Puede existir una materia sin alumnos inscritos |
| RN-04 | Todo alumno debe estar inscrito en al menos una materia |
| RN-05 | De cada inscripción se almacena: fecha de inscripción y calificación final |

### 9. Diagramas

**Diagrama E-R**

![Ejercicio 3 ER](img/Ejercicio3_ER.png)

**Modelo Relacional**

![Ejercicio 3 Relacional](img/Ejercicio3_Relacional.png)

---

## Ejercicio 4 - Cliente / Pedido / Producto

### 4. Diccionario de Datos

**Tabla: Cliente**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| Identificador | - | - | PK | Identificador único del cliente |
| Cliente | - | - | - | Campo "Cliente" (subrayado en la imagen) |
| Nombre | - | - | - | Nombre del cliente |

**Tabla: Pedido**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumeroPedido | - | - | PK | Identificador único del pedido |
| FechaPedido | - | - | - | Fecha del pedido |
| IdCliente | - | - | FK | Cliente que realizó el pedido |

**Tabla: Detalle de Pedido**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumeroPedido | - | - | FK | Pedido asociado |
| NumeroProducto | - | - | FK | Producto incluido |
| Cantidad | - | - | - | Cantidad vendida |
| Precio | - | - | - | Precio de venta |

**Tabla: Producto**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumProducto | - | - | PK | Identificador único del producto *(subrayado en la imagen)* |
| NumProducto | - | - | - | Campo repetido en la imagen *(probablemente debía ser "Nombre Producto")* |
| PrecioDeProducto | - | - | - | Precio del producto |

### 5. Relaciones entre Tablas

| Relación | Cardinalidad | Descripción |
| :--- | :---: | :--- |
| Cliente → Pedido | 1:N | Un cliente puede realizar muchos pedidos |
| Pedido → Detalle de Pedido | 1:M | Un pedido puede contener varios productos |
| Producto → Detalle de Pedido | 1:N | Un producto puede aparecer en muchos pedidos |

### 6. Matriz de Claves Foráneas

| Tabla | Campo FK | Referencia |
| :--- | :--- | :--- |
| Pedido | IdCliente | Cliente (Identificador) |
| Detalle de Pedido | NumeroPedido | Pedido (NumeroPedido) |
| Detalle de Pedido | NumeroProducto | Producto (NumProducto) |

### 7. Integridad Referencial

| Regla | Descripción |
| :--- | :--- |
| IR-01 | No se puede registrar un pedido para un cliente inexistente |
| IR-02 | No se puede agregar un producto inexistente a un pedido |

### 8. Reglas del Negocio

| Código | Regla |
| :--- | :--- |
| RN-01 | Un cliente puede realizar muchos pedidos |
| RN-02 | Cada pedido pertenece a un solo cliente |
| RN-03 | Un pedido contiene varios productos |
| RN-04 | Un producto puede aparecer en muchos pedidos |
| RN-05 | El detalle del pedido almacena cantidad vendida y precio de venta |

### 9. Diagramas

**Diagrama E-R**

![Ejercicio 4 ER](img/Ejercicio4_ER.png)

**Modelo Relacional**

![Ejercicio 4 Relacional](img/Ejercicio4_Relacional.png)

---

## Ejercicio 5 - Employe / Deparment / Locations / Projects / Works-on / Dependent

### 4. Diccionario de Datos

**Tabla: Employe**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| SSN | - | - | PK | Identificador del empleado *(subrayado en la imagen)* |
| Firstname | - | - | - | Nombre |
| Address | - | - | - | Dirección |
| Bodater | - | - | - | Fecha de nacimiento *(así escrito en la imagen, "Bdate")* |
| Slary | - | - | - | Salario *(así escrito en la imagen, "Salary")* |
| Sex | - | - | - | Sexo |
| Number | - | - | - | Campo "Number" *(no explícito a qué corresponde)* |
| Number | - | - | FK | Segundo campo "Number FK" *(no coincide con "Jef" del diccionario original; parece referenciar Deparment)* |

**Tabla: Deparment**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| Number | - | - | - | Identificador del departamento |
| Name | - | - | - | Nombre del departamento |
| Mannager | - | - | FK | Gerente del departamento *(así escrito, "Manager")* |
| Stardate | - | - | - | Fecha de inicio del gerente |

**Tabla: Locations**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumLocc | - | - | - | Identificador de ubicación |
| Number | - | - | - | Campo adicional "Number" |
| NumberDep | - | - | FK | Departamento asociado |
| Lucation | - | - | - | Ubicación *(así escrito, "Location")* |

**Tabla: Dependent**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| Name | - | - | - | Nombre del dependiente |
| Sex | - | - | - | Sexo |
| Rolationships | - | - | - | Relación con el empleado *(así escrito, "Relationship")* |
| Date | - | - | - | Fecha de nacimiento |

> **Nota:** la imagen no muestra el campo SSN (FK) dentro de la tabla Dependent, aunque la relación con Employe sí aparece dibujada en el diagrama.

**Tabla: Works-on**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| SSN | - | - | FK | Empleado asignado *(subrayado en la imagen)* |
| Nom pro | - | - | - | Campo adicional, posiblemente "Nombre proyecto" |
| Number Pri | - | - | FK | Proyecto asignado |
| Hours | - | - | - | Horas trabajadas |

**Tabla: Projects**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| Name | - | - | PK | Nombre del proyecto *(subrayado)* |
| Number | - | - | PK | Identificador del proyecto *(subrayado)* |
| Location | - | - | - | Ubicación del proyecto |
| Number dsp | - | - | - | Departamento responsable |
| Name Def | - | - | - | Departamento asignado |

### 5. Relaciones entre Tablas

| Relación | Cardinalidad | Descripción |
| :--- | :---: | :--- |
| Employe → Deparment | 1:1 | Un empleado administra un departamento |
| Deparment → Locations | 1:N | Un departamento puede tener varias ubicaciones |
| Deparment → Projects | 1:N | Un departamento administra proyectos |
| Employe → Works-on | N:N | Un empleado participa en varios proyectos (línea marcada N-N en el diagrama) |
| Works-on → Projects | N:1 | Varios registros de Works-on corresponden a un proyecto |
| Employe → Dependent | 1:N | Un empleado puede tener varios dependientes |

### 6. Matriz de Claves Foráneas

| Tabla | Campo FK | Referencia |
| :--- | :--- | :--- |
| Employe | Number | Deparment |
| Deparment | Mannager | Employe (SSN) |
| Locations | NumberDep | Deparment (Number) |
| Works-on | SSN | Employe (SSN) |
| Works-on | Number Pri | Projects (Number) |

### 7. Integridad Referencial

| Regla | Descripción |
| :--- | :--- |
| IR-01 | No se puede asignar un gerente inexistente |
| IR-02 | No se puede registrar horas para empleados inexistentes |

### 8. Reglas del Negocio

| Código | Regla |
| :--- | :--- |
| RN-01 | Un empleado puede participar en varios proyectos |
| RN-02 | Un departamento tiene un único gerente |
| RN-03 | Un empleado puede tener varios dependientes |

### 9. Diagramas

**Diagrama E-R**

![Ejercicio 5 ER](img/Ejercicio5_ER.png)

**Modelo Relacional**

![Ejercicio 5 Relacional](img/Ejercicio5_Relacional.png)

---

## Ejercicio 6 - Empelado / Departamento / Proyecto

### 4. Diccionario de Datos

**Tabla: Empelado** *(así escrito en la imagen; correcto sería "Empleado")*

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| SSN | - | - | PK | Identificador del empleado *(subrayado)* |
| Nombre | - | - | - | Nombre |
| Apellido | - | - | - | Apellido |
| FechaNac | - | - | - | Fecha de nacimiento |
| Salario | - | - | - | Salario |
| SexoDir | - | - | - | Campo combinado "Sexo Dir" en la imagen |
| GerenteSSN | - | - | FK | Referencia al gerente |
| NumDepto | - | - | FK | Referencia al departamento *(escrito "nUM dEOTO fk")* |

**Tabla: Departamento**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumDepto | - | - | - | Identificador del departamento |
| NombreGerenteSSN | - | - | - | Campo "Nombre Gerente ssn" |
| FechaNaci | - | - | - | Fecha |

**Tabla: Dependiente**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| SSN | - | - | PK, FK | Empleado asociado *(escrito "Emo. ssn PK FK")* |
| NombreDep | - | - | PK | Nombre del dependiente |
| Sexo | - | - | - | Sexo |
| Relacion | - | - | - | Parentesco |

**Tabla: Trabajo en**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| SSN | - | - | PK, FK | Empleado *(escrito "Emp.ssn PK FK")* |
| ProyNum | - | - | PK, FK | Proyecto |
| Horas | - | - | - | Horas trabajadas |

**Tabla: Proyecto**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumProy | - | - | PK | Identificador del proyecto |
| Nombre | - | - | - | Campo "Nombre u" |
| ControlDeptoNum | - | - | FK | Departamento que controla el proyecto |
| LocoProy | - | - | - | Ubicación del proyecto |

**Tabla: Ubicacion Depto**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| DeptoNum | - | - | - | Departamento asociado |
| Ubicacion | - | - | - | Ubicación |

### 5. Relaciones entre Tablas

| Relación | Cardinalidad | Descripción |
| :--- | :---: | :--- |
| Empelado → Departamento | 1:N | Un empleado pertenece a un departamento; un departamento tiene varios empleados |
| Departamento → Proyecto | 1:N | Un departamento controla varios proyectos |
| Empelado → Trabajo en | 1:N | Un empleado trabaja en varios proyectos |
| Empelado → Dependiente | 1:N | Un empleado tiene varios dependientes |
| Departamento → Ubicacion Depto | 1:N | Un departamento tiene varias ubicaciones |

### 6. Matriz de Claves Foráneas

| Tabla | Campo FK | Referencia |
| :--- | :--- | :--- |
| Empelado | GerenteSSN | Empelado (SSN) |
| Empelado | NumDepto | Departamento (NumDepto) |
| Dependiente | SSN | Empelado (SSN) |
| Trabajo en | SSN | Empelado (SSN) |
| Trabajo en | ProyNum | Proyecto (NumProy) |
| Proyecto | ControlDeptoNum | Departamento (NumDepto) |
| Ubicacion Depto | DeptoNum | Departamento (NumDepto) |

### 7. Integridad Referencial

| Regla | Descripción |
| :--- | :--- |
| IR-01 | No se puede asignar un gerente inexistente |
| IR-02 | No se puede registrar un dependiente para un empleado inexistente |

### 8. Reglas del Negocio

| Código | Regla |
| :--- | :--- |
| RN-01 | Un departamento tiene un único gerente |
| RN-02 | Un empleado puede participar en varios proyectos |
| RN-03 | Un empleado puede registrar varios dependientes |

### 9. Diagramas

**Diagrama E-R**

![Ejercicio 6 ER](img/Ejercicio6_ER.png)

**Modelo Relacional**

![Ejercicio 6 Relacional](img/Ejercicio6_Relacional.png)

---

## Ejercicio 7 - Universidad (Alumno / Profesor / Materia / Proyecto)

### 4. Diccionario de Datos

**Tabla: Telefono**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| ClaveTel | - | - | - | Identificador del teléfono |
| Matricula | - | - | FK | Alumno propietario |
| Telefono | - | - | - | Número telefónico |

**Tabla: Alumno**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| Matricula | - | - | PK | Identificador único *(subrayado)* |
| NomAlumno | - | - | - | Nombre del alumno |
| Ap1Alumno | - | - | - | Primer apellido |
| Ap2Alumno | - | - | - | Segundo apellido |
| FechaNaci | - | - | - | Fecha de nacimiento |
| Correo | - | - | - | Correo electrónico |

**Tabla: Credencial**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumCredencial | - | - | PK | Número de credencial *(subrayado)* |
| FechaExpediente | - | - | - | Fecha de expedición |
| Vigencia | - | - | - | Fecha de vencimiento |
| Matricula | - | - | UQ, NN | Alumno propietario |

**Tabla: Dependent**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NonbreDepen | - | - | - | Nombre del dependiente *(así escrito, "Nombre Depen")* |
| FechaNaci | - | - | - | Fecha de nacimiento |
| Parentesco | - | - | - | Relación con el profesor |

> **Nota:** no aparece explícitamente el campo NumProf (FK) dentro de la caja de esta tabla, aunque la línea de relación hacia Profesor está marcada con "N" en el diagrama.

**Tabla: Materia**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| ClaveMateria | - | - | PK | Clave de la materia *(subrayado)* |
| NombreMateria | - | - | - | Nombre de la materia |
| Creditos | - | - | - | Créditos |

**Tabla: Profesor**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumProf | - | - | PK | Número del profesor *(subrayado)* |
| Nombre | - | - | - | Nombre |
| Ap1 | - | - | - | Primer apellido |
| Ap2 | - | - | - | Segundo apellido |

**Tabla: Cursa**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| Matricula | - | - | FK | Alumno inscrito *(subrayado)* |
| ClaveMateria | - | - | FK | Materia inscrita *(subrayado)* |
| FechaInscri | - | - | - | Fecha de inscripción |
| CaliFinal | - | - | - | Calificación final |

**Tabla: Departamento**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumDepartamento | - | - | - | Identificador del departamento |
| NombreDeparta | - | - | - | Nombre del departamento |
| Edificio | - | - | - | Edificio |

**Tabla: Participa**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumProt | - | - | FK | Profesor participante *(así escrito, probablemente "Num Prof")* |
| NumProy | - | - | FK | Proyecto asignado |
| Rol | - | - | - | Rol desempeñado |

**Tabla: Proyecto**

| Campo | Tipo | Longitud | Restricción | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| NumProy | - | - | - | Identificador del proyecto |
| Nombre | - | - | - | Nombre del proyecto |
| Presupuesto | - | - | - | Presupuesto asignado |

### 5. Relaciones entre Tablas

| Relación | Cardinalidad | Descripción |
| :--- | :---: | :--- |
| Alumno → Telefono | 1:N | Un alumno puede registrar varios teléfonos |
| Alumno → Credencial | 1:1 | Cada alumno posee una única credencial |
| Alumno → Cursa | 1:N | Un alumno puede cursar varias materias |
| Materia → Cursa | 1:N | Una materia puede ser cursada por varios alumnos |
| Materia → Profesor | N:1 | Varias materias son impartidas por un profesor |
| Profesor → Departamento | N:1 | Varios profesores pertenecen a un departamento |
| Profesor → Participa | 1:N | Un profesor puede participar en varios proyectos |
| Participa → Proyecto | N:1 | Varios registros de Participa corresponden a un proyecto |
| Profesor → Dependent | 1:N | Un profesor puede tener varios dependientes |

### 6. Matriz de Claves Foráneas

| Tabla | Campo FK | Referencia |
| :--- | :--- | :--- |
| Telefono | Matricula | Alumno (Matricula) |
| Credencial | Matricula | Alumno (Matricula) |
| Cursa | Matricula | Alumno (Matricula) |
| Cursa | ClaveMateria | Materia (ClaveMateria) |
| Participa | NumProt | Profesor (NumProf) |
| Participa | NumProy | Proyecto (NumProy) |

### 7. Integridad Referencial

| Regla | Descripción |
| :--- | :--- |
| IR-01 | No puede registrarse un teléfono para un alumno inexistente |
| IR-02 | No puede existir una credencial sin un alumno asociado |
| IR-03 | No puede inscribirse un alumno en una materia inexistente |
| IR-04 | No puede registrarse la participación de un profesor en un proyecto inexistente |

### 8. Reglas del Negocio

| Código | Regla |
| :--- | :--- |
| RN-01 | Cada alumno posee una única credencial institucional |
| RN-02 | Un alumno puede registrar varios números telefónicos |
| RN-03 | Un alumno puede inscribirse en varias materias |
| RN-04 | Un profesor puede participar en varios proyectos de investigación |
| RN-05 | Un profesor puede registrar varios dependientes |

### 9. Diagrama

**Modelo Relacional** *(no se proporcionó imagen del diagrama E-R para este ejercicio)*

![Ejercicio 7 Relacional](img/Ejercicio7_Relacional.png)
