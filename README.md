# Analisis-ventas-contoso-qlik
Optimización y Análisis de Datos para Contoso: De la Extracción a la Toma de Decisiones 
1. Resumen del Proyecto

El presente proyecto tuvo como objetivo principal reestructurar, optimizar y analizar la información comercial de la empresa Contoso. El desafío técnico radicó en procesar datos en crudo desde una base de datos SQL y transformarlos en un modelo analítico eficiente, robusto y escalable, capaz de responder a preguntas de negocio complejas de manera dinámica.

2. Arquitectura de Datos y Proceso ETL 

Fase 1: Extracción y Limpieza 

El desarrollo comenzó con la ingesta y depuración para asegurar la calidad de la información:

    Conexión: Extracción directa desde la base de datos SQL original.

    Gestión de Rutas: Se implementó la variabilización de rutas de acceso para automatizar futuras cargas e independizar 
    el código del entorno local.

    Depuración: Se realizó una limpieza profunda corrigiendo claves sintéticas y eliminando referencias circulares 
    para evitar la degradación del rendimiento en Qlik.

Fase 2: Modelado de Datos 

(Arriba/Izquierda: Estado Inicial | Abajo/Derecha: Estado Optimizado)

Se realizó una reestructuración completa de la arquitectura:

    Transición a Modelo Estrella: Se migró de una estructura altamente normalizada (copo de nieve) que complejizaba 
    y ralentizaba las consultas , hacia un Modelo Estrella altamente eficiente.

    Consolidación: Los datos se centralizaron en una Fact_Table_Consolidada, rodeada de las dimensiones maestras: 
    Clientes, Tiendas, Calendario y Productos. Adicionalmente, se concatenaron las tablas de ventas dispersas y se 
    unificó la facturación mediante cálculos directos por tipo de moneda.

    Transformación: Se aplicaron operaciones y variables para generar nuevas dimensiones de análisis.

    Optimización de Recursos y Mantenimiento: Los datos procesados se almacenaron en formato .QVD para garantizar 
    la velocidad de la aplicación, y se aplicaron sentencias Drop table tras las transformaciones temporales para 
    liberar memoria RAM. Todo el script se migró a archivos .QVS externos, robusteciendo la carga y permitiendo la 
    reutilización del código.

3. Capa Analítica y Frontend 

Para la interfaz de usuario, se construyó una experiencia dinámica enfocada en la usabilidad:

    Desarrollo Analítico: Se implementaron medidas maestras estandarizadas y Set Analysis para realizar cálculos 
    complejos independientes de las selecciones (ej. comparativas interanuales), garantizando una lógica de cálculo 
    unificada.

    UX/UI: La navegación incluye cambios de moneda, modo oscuro/claro y limpieza de filtros. Se aplicaron colores 
    condicionales y títulos dinámicos basados en el contexto de los datos filtrados , además de jerarquías para un 
    drill-down intuitivo.

4. Dashboards y Visualizaciones 

El tablero principal cuenta con filtros por cliente y periodos , KPIs de margen comparativos y ventas totales , junto con gráficos temporales YTD y MAT. Integra gráficos combinados y de dona para analizar cantidades y márgenes por jerarquía de productos.

La vista de productos detalla los artículos más vendidos mediante gráficos de barras y cruza el margen neto vs. monto de ventas en un gráfico de dispersión ponderado por cantidades.

La vista de clientes incorpora un gráfico de bloques basado en ventas , segmentación RFM por estadío del cliente y distribución geográfica interactiva.

5. Insights y Conclusiones del Negocio 

El análisis del modelo consolidado permitió identificar los siguientes hallazgos clave:

    Comportamiento del Cliente Principal: "Berlin" es el cliente de mayor volumen (destacando en Auriculares 
    Bluetooth) y posee los mayores índices de Margen Neto, aunque presenta baja recencia de compra durante el año.

    Rentabilidad vs. Volumen: Los teléfonos móviles lideran en volumen de ventas, pero la subcategoría de "Teléfonos 
    inteligentes y PDA" es el motor del Margen Neto. En la categoría Equipos, los accesorios son los productos más 
    vendidos y los que mayor margen reportan.

    Detección de Riesgos: El segmento B2B (tipo "Company") concentra el mayor monto de compras en USD. Se detectaron 
    dos compañías clave en los mercados de Asia y Europa que actualmente se encuentran en estado de riesgo y requieren 
    atención comercial inmediata.

    Auditoría de Datos: El proceso analítico evidenció un error de origen en los datos de margen bruto correspondientes 
    al año 2021 para el producto 0202011, hallazgo que fue derivado al equipo correspondiente para su depuración.
