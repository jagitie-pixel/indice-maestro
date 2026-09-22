# Índice maestro de libros

Habilidad para Codex que convierte dos o más índices de libros o documentos en un temario común, conservando todas las procedencias originales.

## Uso

Invoca `$indice-maestro` y adjunta o pega los índices. La salida es una tabla con número maestro, apartado maestro y una columna por libro, seguida de un control de cobertura.

- Títulos maestros en español y numeración jerárquica independiente.
- Números y títulos originales completos en las columnas de procedencia.
- Agrupación temática sin eliminar entradas repetidas ni específicas.
- Pendientes de ubicación dentro de la tabla.
- Auditoría de cada entrada original; no se declara completo un resultado con omisiones o fuentes ilegibles.

## Instalación como habilidad local

Copia la carpeta `skills/indice-maestro` dentro de la carpeta personal de habilidades de Codex (`~/.codex/skills`, o la carpeta `skills` de tu ubicación personalizada de Codex). Abre una conversación nueva para que se detecte.

También se incluye el manifiesto `.codex-plugin/plugin.json` para distribuirla como plugin.

## Archivos

- `skills/indice-maestro/SKILL.md`: instrucciones de la habilidad.
- `skills/indice-maestro/references/formato.md`: exportaciones y comprobaciones.
- `skills/indice-maestro/agents/openai.yaml`: presentación e invocación.

## Alcance

Trabaja con los índices aportados. No resume el contenido no recibido de los libros ni completa huecos con conocimiento externo. La cobertura del 100 % se refiere a las entradas del índice aportado y verificable, no al contenido completo del libro. Las agrupaciones temáticas requieren revisión humana cuando exista duda.

El paquete no incluye libros, índices privados, credenciales ni datos de la aplicación. La validación de estructura de la habilidad no constituye una garantía de exactitud de cada resultado generado.
