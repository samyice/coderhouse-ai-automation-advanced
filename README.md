# AI Automation

Proyecto integrador desarrollado para el curso **AI Automation Advanced**, orientado a la construcción progresiva de un agente en **n8n** para la gestión inicial de consultas comerciales de un estudio.

## Objetivo

El proyecto busca integrar capacidades de inteligencia artificial con un CRM, permitiendo interpretar mensajes desestructurados de potenciales clientes, extraer información relevante, identificar datos faltantes y decidir de forma autónoma cuándo ejecutar herramientas externas.

El workflow se diseña de manera modular para poder integrarse más adelante con un CRM propio, sin depender de que dicho sistema esté finalizado durante las primeras etapas del curso.

## Arquitectura inicial

En el **Checkpoint 1**, el flujo implementado incluye:

* **Chat Trigger** como punto de entrada de consultas.
* **AI Agent** configurado como agente con herramientas.
* **Groq Chat Model** utilizando `llama-3.3-70b-versatile`.
* **Google Sheets** como herramienta provisional para registrar consultas comerciales válidas.
* **Gmail** como mecanismo de observabilidad y reporte de ejecución.
* Límite de **7 iteraciones máximas** como guardrail del agente.
* Registro de pasos intermedios para auditoría del comportamiento del modelo.

## Lógica del agente

El agente actúa como asistente de precalificación comercial de un estudio.

Analiza información como:

* nombre;
* email;
* teléfono;
* ubicación;
* tipo de inmueble;
* tipo de proyecto;
* superficie;
* alcance;
* presupuesto;
* plazo estimado;
* estado del proyecto.

La herramienta de registro solo se ejecuta cuando se cumplen las condiciones mínimas definidas para considerar válida una consulta comercial.

Actualmente se requiere:

1. Una necesidad o proyecto identificable.
2. Una ubicación o zona del proyecto.
3. Al menos un medio de contacto: email o teléfono.

Si falta información obligatoria, el agente solicita únicamente los datos necesarios y no genera registros parciales.

## Evolución del proyecto

Este repositorio contiene un único proyecto que evolucionará durante los distintos módulos del curso.

La arquitectura prevista contempla incorporar progresivamente:

* **M1:** agente base, herramientas y observabilidad.
* **M2:** arquitectura multiagente.
* **M3:** memoria y contexto por sesión.
* **M4:** integraciones reales con CRM, calendario y servicios de Workspace.
* **M5:** RAG y consulta de base documental.
* **M6:** interacción por voz mediante STT/TTS.
* **Módulos posteriores:** ampliación de capacidades hasta el Proyecto Final Integrador.

La integración con Google Sheets es temporal. En una etapa posterior, la herramienta podrá reemplazarse por una API del CRM definitivo manteniendo la lógica principal del agente.

## Estructura del repositorio

coderhouse-ai-automation-advanced/
├── checkpoint1/
│   └── checkpoint1_Samanta_Castro.json
├── checkpoint2/
├── checkpoint3/
└── README.md
```

Cada checkpoint conservará una versión exportada del workflow para documentar la evolución del proyecto.

## Tecnologías

* n8n
* Groq
* Llama 3.3 70B Versatile
* Google Sheets API
* Gmail API
* OAuth 2.0

## Estado actual

**Checkpoint 1 completado.**

El agente puede:

* interpretar consultas iniciales de arquitectura;
* identificar información relevante;
* detectar datos faltantes;
* decidir autónomamente cuándo ejecutar una herramienta;
* registrar consultas válidas en Google Sheets;
* generar un reporte de ejecución por Gmail;
* exponer pasos intermedios para observabilidad y auditoría.
