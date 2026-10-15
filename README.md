# -ClinicaVeterinaria
### Preguntas de discusión - Refactoring (SRP)

- **¿Cuántas razones para cambiar tenía Veterinario antes del refactoring?**
  Tenía 4 razones principales para cambiar:
  1. Si cambiaban las reglas de negocio para reservar citas.
  2. Si cambiaba la lógica de diagnósticos o los estados de las citas.
  3. Si cambiaban los cálculos o la estructura de la facturación.
  4. Si cambiaba el formato o la forma de generar los reportes.

- **¿Qué ganamos al separar modelo y servicios?**
  Ganamos mayor cohesión, legibilidad y mantenibilidad del código. Al separar el modelo (que solo almacena datos) de los servicios (que contienen la lógica de negocio), logramos que las modificaciones en una funcionalidad no rompan el resto del sistema, además de facilitar considerablemente la realización de pruebas unitarias.

- **¿Qué clase debería cambiar si mañana cambia el formato del reporte?**
  Debería cambiar únicamente la clase ReporteService, ya que es la encargada exclusiva de centralizar la lógica de generación de reportes en la arquitectura.