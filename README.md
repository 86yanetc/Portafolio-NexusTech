# 💎 Nexus-Tech: Intelligent Data Analyst

**Agente Multi-Agente de Inteligencia de Negocios y Machine Learning.**

<div align="right">
  <em>"Donde la cronología de los datos se convierte en la brújula estratégica: Entender el pasado, dominar el presente y anticipar el futuro."</em>
</div>

**Desarrollado por: Msc. Yanet Cesaire Velazquez**

## 📂 Documentación Técnica

Para conocer los detalles de arquitectura, desafíos técnicos superados y comparativas de rendimiento:

👉 [**Descargar Informe Técnico Completo (PDF)**](./documentos/Informe_Tecnico_Final.pdf)

*Nota: Este repositorio es un portafolio de arquitectura y diseño de sistemas de IA. El código fuente es de propiedad privada de la autora.*

## 🧠 Visión del Proyecto

Nexus-Tech no es solo una herramienta de visualización; es un **Ecosistema Multi-Agente de Inteligencia de Negocios y Machine Learning** diseñado para actuar como un Consultor de Estrategia Senior. Su arquitectura permite trascender el análisis estático para ofrecer una visión 360° de la salud empresarial, operando en tres dimensiones temporales críticas:

**📜 El Pasado para Entender:** Minería de datos profunda y analítica descriptiva para identificar patrones históricos y causas raíz.

**🛒 El Presente para Vender:** Monitoreo de KPIs en tiempo real y optimización operativa para maximizar la conversión y la eficiencia actual.

**🔮 El Futuro para Prevenir:** Modelos predictivos de Machine Learning que anticipan tendencias, detectan anomalías y mitigan riesgos antes de que impacten al negocio.

## 💡 Decisiones de Ingeniería y Preguntas Clave

En el diseño de Nexus-Tech, se priorizó la creación de un sistema que no solo informara, sino que ejecutara. Estas son las respuestas a los pilares fundamentales de su arquitectura:

### ¿Por qué un enfoque Agéntico (LangGraph) en lugar de un Dashboard tradicional?

La inteligencia de negocios convencional (Power BI/Tableau) es pasiva. Se optó por una arquitectura agéntica por tres razones críticas:

**Democratización del Dato:** Permite que un directivo sin conocimientos técnicos realice análisis complejos mediante lenguaje natural, eliminando la barrera del SQL o Python.

**Capacidad Ejecutiva:** A diferencia de un dashboard estático, el agente puede escribir y ejecutar código en tiempo real, adaptando el análisis a preguntas que no estaban previstas en el diseño original.

**Visión Predictiva Unificada:** El agente orquesta el flujo entre el análisis histórico y los modelos de Machine Learning (XGBoost/Forecasting), uniendo el pasado y el futuro en una sola respuesta coherente.

### ¿Por qué mantener el procesamiento 100% Local con Llama-3.1?

Tratándose de Big Data corporativa (ventas, márgenes, datos de clientes), la privacidad es innegociable:

**Seguridad de Activos:** Los datos financieros y estratégicos de la empresa nunca abandonan la infraestructura local, cumpliendo con los estándares más estrictos de cumplimiento y auditoría.

**Latencia de Ejecución:** Al estar el LLM y el motor de ejecución (Python REPL) en el mismo entorno local, se minimizan los tiempos de transferencia de datos masivos.

### ¿Cuál fue el desafío técnico más complejo?

El reto principal fue el desarrollo del Self-Healing Loop (Bucle de Autocorrección). Lograr que una IA genere código Python, lo ejecute, capture sus propios errores de sintaxis o de lógica de datos (como inconsistencias en nombres de columnas), y sea capaz de corregirse a sí misma en tiempo real sin intervención humana, fue el hito de ingeniería que permitió pasar de un experimento a una herramienta de producción confiable.

## 🏗️ Arquitectura del Sistema: Nexus-Tech Intelligent Data Analyst 

```mermaid
graph TD
    subgraph UI ["💻 CAPA DE USUARIO (Frontend)"]
        A[Streamlit Dashboard]
    end

    subgraph API ["⚡ CAPA DE COMUNICACIÓN"]
        B[FastAPI REST Service]
    end

    subgraph AGENT ["🧠 ORQUESTACIÓN AGÉNTICA (LangGraph)"]
        C{Router Node}
        D[Analytics Programmer]
        E[Prediction Programmer]
        F[[Python REPL / Sandbox]]
        G{Self-Healing Loop}
        H[Finisher Node / Redactor]
    end

    subgraph DATA ["💾 CAPA DE DATOS E INTELIGENCIA"]
        I[(SQLite: ventas_full)]
        J[Model Zoo: .joblib files]
        K[Output Folder: .png charts]
    end

    %% Flujo de la información
    A -- "Pregunta (Natural Language)" --> B
    B -- "Invocación de Grafo" --> C
    
    C -- "Clasificación: Analytics" --> D
    C -- "Clasificación: Prediction" --> E
    
    D -- "Generación de Código" --> F
    E -- "Generación de Código" --> F
    
    F -- "Consulta / Inferencia" --> I
    F -- "Carga de Modelos" --> J
    F -- "Error de ejecución" --> G
    G -- "Feedback para corrección" --> D & E
    
    F -- "Evidencia Técnica / CSV / Log" --> H
    I -- "Datos Reales" --> F
    
    H -- "Informe Ejecutivo (Markdown)" --> B
    F -- "Generación de Imágenes" --> K
    K -- "Visualización Dinámica" --> A
    B -- "Respuesta Final" --> A

    style C fill:#f96,stroke:#333,stroke-width:2px
    style G fill:#f66,stroke:#333,stroke-width:2px
    style I fill:#69f,stroke:#333,stroke-width:2px
    style J fill:#6f9,stroke:#333,stroke-width:2px
```

La arquitectura de Nexus-Tech se basa en un modelo Local-First de capas desacopladas, diseñado para maximizar la eficiencia en arquitecturas de CPU mediante inferencia cuantizada y orquestación asíncrona.

La infraestructura de Nexus-Tech ha sido diseñada bajo un paradigma de Inteligencia Agéntica de Ciclo Cerrado, donde el razonamiento del modelo y la ejecución de código ocurren en un entorno seguro y supervisado.

### 1. Capa de Interacción Directiva (Streamlit UI)

Interfaz No-Code de alto rendimiento que actúa como puente entre el lenguaje natural y el Big Data.

**Abstracción Técnica:** Permite a perfiles C-Level (CEO, CFO, CMO) ejecutar consultas complejas sin conocimientos de SQL o Python.

**Renderizado Dinámico** Sistema de visualización automática que interpreta archivos en la carpeta /output para presentar dashboards generados al vuelo por la IA.

### 2. Capa de Orquestación y Comunicación (FastAPI)

El motor de ejecución que garantiza una latencia mínima y una gestión de recursos eficiente.

**Persistence Layer:** Mantiene una instancia caliente del modelo Llama-3.1-8B, eliminando tiempos de carga en cada consulta.

**Gestión Síncrona:** Arquitectura diseñada para proteger el procesador durante las fases intensivas de generación de código y entrenamiento de modelos.

### 3. Cerebro Agéntico (LangGraph Architecture) 

El núcleo del proyecto utiliza LangGraph para crear un flujo de trabajo cíclico y especializado:

**Intelligent Router:** Clasificador semántico que decide el flujo de trabajo: Analítica Descriptiva (Pasado) o Ciencia Predictiva (Futuro).

**Specialized Nodes:** Nodos con expertos dedicados. El nodo de Analytics ejecuta leyes de Pareto y segmentación RFM; el nodo de Prediction orquestra algoritmos de Churn, Forecasting y Clustering.

**Self-Healing Loop (Autocorrección):** Implementación de una capa de resiliencia que detecta fallos en el código generado (errores de sintaxis o columnas faltantes), permitiendo al agente re-escribir y corregir su propia lógica hasta 3 veces antes de entregar resultados.


### 4. Entorno de Computación Segura (Python REPL)

Un entorno de ejecución aislado donde la IA interactúa con los activos de datos:

**Data Lake Local (SQLite):** Fuente de verdad con más de 100,000 registros indexados para consultas de alta velocidad.

**Joblib Model Repository:** Biblioteca de cerebros predictivos pre-entrenados (XGBoost, Random Forest, K-Means) listos para ser invocados por el agente.


### 5. Capa de Entrega de Valor (Business Narrative)

Transformación de outputs técnicos en Narrativa de Negocio. El sistema traduce matrices y arrays en informes ejecutivos enfocados en retorno de inversión (ROI), mitigación de riesgos y oportunidades de mercado.

## 🌲 Estructura del Directorio

![DIRECTORIO](./imagenes/directorio_nexus2.png)

## 🛠️ Especificaciones Técnicas y Pilares de Valor

### Stack Tecnológico de Vanguardia

El ecosistema ha sido construido utilizando herramientas de última generación para garantizar la privacidad, precisión y escalabilidad local.

**IA Generativa (LLM):** Meta Llama-3.1-8B-Instruct (Cuantización Q4_K_M), optimizado para inferencia en CPU mediante llama-cpp-python.

**Orquestación Agéntica:** LangGraph para el control de estados complejos, lógica cíclica de reintentos (Self-Healing) y enrutamiento dinámico de tareas.

**Machine Learning (Core):** Modelos predictivos basados en XGBoost, Random Forest y LightGBM.

**Optimización de Modelos:** Búsqueda Bayesiana con Optuna para ajuste de hiperparámetros y balanceo de clases mediante SMOTE.

**Ingeniería de Datos:** Pandas y NumPy para manipulación matricial, con SQLite como motor de persistencia de alta velocidad.

**Backend & Interfaz:** FastAPI (Arquitectura asíncrona) y Streamlit (UI ejecutiva).


![ANALISIS1](./imagenes/analisis_1a.png)

![ANALISIS2](./imagenes/analisis_2.png)