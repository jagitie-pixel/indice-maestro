# Exportación y datos internos

Leer al generar archivos. La tabla principal siempre tiene «Nº maestro», «Apartado maestro» y una columna por libro. No usar por defecto la antigua matriz de una fila por relación.

## Markdown, CSV y Excel

Mantén la misma tabla completa en todos estos formatos. En Markdown escapa barras verticales y otros caracteres que romperían las celdas sin cambiar el texto visible. En CSV usa UTF-8 y un escritor que escape comillas, separadores y saltos de línea; varias procedencias siguen separadas por punto y coma dentro de la misma celda entrecomillada cuando haga falta. Trata los números jerárquicos como texto para evitar fechas o decimales en Excel. Conserva «—» donde no hay procedencia.

Para hojas de cálculo guarda títulos y procedencias como texto, nunca como fórmulas. En CSV protege texto que empiece por =, +, - o @ con un apóstrofo cuando sea necesario; conserva el original en la representación canónica y señala brevemente esa protección en el control. El guion largo «—» de ausencia no es una fórmula.

En Markdown y Excel coloca el control de cobertura después de la tabla. Si se pide CSV, entrega la tabla en CSV y el breve control aparte: no agregues filas con un esquema diferente al archivo CSV. Otros metadatos o páginas pueden conservarse en datos internos o exportación adicional solicitada sin sustituir número y título original ni añadir columnas al formato principal sin petición.

## JSON opcional

Formato propio, no contrato de importación de la app. Usa schema_version "2.0" para distinguirlo de la salida anterior. Conserva:

- fuentes: id, etiqueta de columna, título, autoría, edición, archivo y metadatos aportados. Desconocidos: null; no inventar.
- entradas: id por aparición, fuente_id, padre_id, orden, numeracion_original, titulo_original, pagina_impresa, localizador_evidencia.
- filas: id estable, numero_maestro (cadena), apartado_maestro, padre_id, pendiente (booleano), procedencias (por fuente_id: lista completa de entrada_id).
- exclusiones: entrada_id y autorización expresa del usuario.
- control: por fuente, total_inventariado, total_excluido, total_evaluable, representados_unicos, pendientes_unicos y porcentaje (null si total_evaluable es cero o desconocido).

La fila contenedora del bloque pendiente puede tener procedencias vacías; es un rótulo estructural, no un tema inventado. Los temas sustantivos requieren fuentes. No exportes rutas locales absolutas salvo solicitud expresa.

## Invariantes de comprobación

IDs únicos; referencias existentes; jerarquía sin ciclos; padres de entradas de la misma fuente. Cada entrada evaluable aparece en su columna, con número y título original, incluida cada repetición. Un mismo ID asociado a varias filas cuenta una sola vez. Los excluidos autorizados no se cuentan como representados. El conjunto de IDs representados coincide con el evaluable antes de declarar cobertura completa.

Pendientes es un subconjunto de representados: no se suma de nuevo al numerador. Los capítulos originales necesitan representación explícita, aunque ya aparezcan sus hijos. Verifica tanto la correspondencia de datos como las celdas de la entrega final; el inventario interno por sí solo no prueba cobertura visual. No reduzcas la auditoría a una muestra.
