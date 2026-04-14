# assetManagementChallenge
Solución automatizada con n8n e IA para la trazabilidad de activos tecnológicos, detección de inconsistencias de inventario y optimización del ciclo de vida de hardware.


Para que tu repositorio no solo sea una entrega técnica, sino una propuesta que le hable directamente al equipo de Mercado Libre (usando sus propias herramientas empresariales), el README tiene que ser impecable.

Acá tenés el contenido completo del README.md. Está diseñado para resaltar que tu lógica es Enterprise-Ready:

🤖 AI-Driven Asset Management Auditor
Sistema de auditoría inteligente diseñado para resolver fallas estructurales en la integridad de datos de inventario IT, optimizando el ciclo de vida de los activos mediante automatización avanzada y modelos de lenguaje (LLM).

📊 Diagnóstico del Dataset (Pain Points)
Tras el análisis, se detectaron desvíos críticos que comprometen la operación:
Usuarios Fantasma: Discrepancias entre el estado In Use y la asignación real de responsables.
Ruido Operativo: Movimientos logísticos redundantes (mismo origen/destino) que ensucian la trazabilidad.
Ciclo de Vida Incompleto: Activos estancados desde 2022 y falta de estados de disposición final (Scrap/Decommission).

🛠️ Arquitectura y Stack Tecnológico
La solución fue diseñada bajo una premisa de eficiencia de recursos (Token Saver):

Orquestador: n8n.
Procesamiento: JavaScript (Lógica de filtrado y normalización).
IA Engine: Integración híbrida. Desarrollado localmente con Ollama, 100% compatible con Google Gemini (Enterprise version).
Base de Datos: Google Sheets API.

🚀 Cómo Iniciar (Setup)
### 📊 Estructura del Google Sheet (Database)
El workflow está diseñado para interactuar con una hoja de cálculo estructurada en dos pestañas principales. Para replicar la solución, se debe utilizar un archivo con las siguientes columnas:

acceso a mi planilla para poder replicar
### 📑 Acceso a la Base de Datos (Live Demo)
Puedes consultar la estructura de datos y el log histórico en tiempo real aquí:
[🔗 Google Sheets - Asset Management Database](https://docs.google.com/spreadsheets/d/1EHUDFelkk8vVxHaN69w9FFk2yUIA0DoNSbSUU5cuchM/edit?usp=sharing)




#### Pestaña 1: `Dataset_Original`
Es la fuente de entrada donde se vuelcan los datos crudos de los activos (Assets, Movement, StatusHistory).

#### Pestaña 2:  "Auditoria_Results
Es donde el workflow vuelca todo el registro de auditoria
 - `Asset ID`: asset
  - `Riesgo`: riesgo
  - `Hallazgos`: desvios encontrados en los assets
  - `Fecha Auditoría`: Fecha de registro auditoria

#### Pestaña 3: `Reporte_Historico` (Crucial para el KPI de Evolución)
Es donde el workflow escribe los resultados y desde donde lee para comparar tendencias.
- **Columnas:** - 
  - `Fecha`: Marca de tiempo de la auditoría.
  - `% de riesgo`: Porcentaje calculado (ej: 54.17).
  - `TotalDeAlertas`: Cantidad de activos con conflictos detectados.
  - `Total_Activos`: Universo total de la base.

  
Para replicar este workflow en un entorno de producción o testing:
Importar Workflow: Descargar el archivo workflow/Asset_Auditor.json e importarlo en tu instancia de n8n.

-Configurar Credenciales:
-Conectar el nodo de Google Sheets con el ID de tu planilla.
-Configurar el nodo de Gmail para el envío de alertas.
-Configuración de IA: - El workflow utiliza un nodo de AI Agent. Recomiendo remplazar Ollama y colocar una ia mas compleja como gemini o gpt
Para usarlo con el stack de la empresa, simplemente cambia el modelo en el nodo de "AI Agent" de Ollama a Google Gemini. La estructura de los prompts ya está optimizada para este cambio.
-Ejecutar: El trigger está configurado de forma manual para la demo, pero se recomienda un Cron semanal.

📈 KPIs e Impacto Operativo
Cycle Time: Reducción del tiempo de auditoría de 4 horas (manual) a < 30 segundos (auto).
Visibilidad 360: Análisis del 100% de la base en cada corrida.
Análisis de Tendencia (Exclusivo): El sistema no es estático; compara el riesgo actual con la auditoría anterior para generar un KPI de Evolución (Mejora/Deterioro).


📺 Demo y Documentación
Video Explicativo: (https://youtu.be/rZP5sFIiwI4)

Documento de Estrategia: [Informe de Auditoría Inteligente y Gestión de Activos.pdf](https://github.com/federicospottiDEV/assetManagementChallenge/blob/cdd4011c8122474cd07b0f1e2e3daac4ecc9aa4d/Informe%20de%20Auditor%C3%ADa%20Inteligente%20y%20Gesti%C3%B3n%20de%20Activos.pdf)






Desarrollado por Federico Spotti > 📧 federicosspotti@gmail.com
🛠️ Tech Stack: n8n, JavaScript, Ollama, Google Sheets API.
