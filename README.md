# -ClinicaVeterinaria
### Preguntas de discusión Integrante 1 - Refactoring (SRP)

- **¿Cuántas razones para cambiar tenía Veterinario antes del refactoring?**
  
  Tenía 4 razones principales para cambiar:
  1 Si cambiaban las reglas de negocio para reservar citas.
  2 Si cambiaba la lógica de diagnósticos o los estados de las citas.
  3 Si cambiaban los cálculos o la estructura de la facturación.
  4 Si cambiaba el formato o la forma de generar los reportes.

- **¿Qué ganamos al separar modelo y servicios?**
  
  Ganamos mayor cohesión, legibilidad y mantenibilidad del código. Al separar el modelo (que solo almacena datos) de los servicios (que contienen la lógica de negocio), logramos que las modificaciones en una funcionalidad no rompan el resto del sistema, además de facilitar considerablemente la realización de pruebas unitarias.

- **¿Qué clase debería cambiar si mañana cambia el formato del reporte?**
  
  Debería cambiar únicamente la clase ReporteService, ya que es la encargada exclusiva de centralizar la lógica de generación de reportes en la arquitectura.

  ### Preguntas de discusión Integrante 2
  1 *¿Por qué los condicionales repetidos hacen más caro el cambio?*
   Porque al añadir un nuevo tipo de tratamiento, toca buscar y modificar todos los bloques if-else o switch distribuidos por el proyecto (Tratamiento.java, TratamientoService.java, etc.). Esto aumenta el tiempo de desarrollo y el riesgo de generar errores accidentales en la lógica ya existente.
 2 *¿Qué pasaría si agregamos Odontologia como tratamiento?*
   Basta con crear un archivo nuevo OdontologiaTratamiento.java que implemente ITratamiento con su propio costo e indicaciones. No se tiene que tocar ni editar ninguna de las clases existentes.
 3 *¿Cuándo una interfaz ayuda a extender el sistema?*
   Cuando define un contrato común (calcularCostoFinal() y obtenerIndicaciones()). Permite que los servicios deleguen el comportamiento en el objeto sin preocuparse de cuál es su clase concreta, cumpliendo el principio Open/Closed (abierto a extensión, cerrado a modificación)