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

