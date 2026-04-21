# 🚀 ASTRA (Architecture for Strategic Task & Reasoning Automation)

**ASTRA** es un consultor de negocios semiautónomo diseñado para acelerar la fase de ideación y validación de proyectos. Transforma ideas iniciales en entregables de negocio estructurados (Plan, Pitch Deck y Análisis de Viabilidad) de forma automatizada.

## 🌟 Descripción General

Los chatbots de IA tradicionales a menudo proporcionan respuestas conversacionales no estructuradas. ASTRA supera esta limitación obligando al LLM (OpenAI GPT-4) a actuar como un motor lógico. Genera exclusivamente estructuras de datos en formato JSON, permitiendo una integración perfecta con herramientas de Google Workspace a través de Make.com.

* **Usuario Objetivo:** Emprendedores, consultores de innovación y estudiantes.
* **Propósito:** Validar hipótesis y estructurar ideas de negocio rápidamente sin intervención manual intermedia.

## 🏗️ Arquitectura del Sistema

El flujo de trabajo consta de los siguientes componentes clave:

1.  **Entrada:** Discord (Interfaz de usuario).
2.  **Orquestador:** Make.com (Gestión del flujo, parseo de datos JSON).
3.  **Cerebro:** OpenAI GPT-4 (Ejecutando el Protocolo ASTRA v8.0 + RAG Estático).
4.  **Salida:** Google Docs (Informe detallado), Google Slides (Pitch Deck), y Google Sheets (Logging y Gobernanza).

![Diagrama de Arquitectura de ASTRA](enlace-a-tu-imagen-de-arquitectura.png)

## 🧠 El Protocolo ASTRA v8.0 (Prompt Engineering)

El núcleo de este proyecto no es código de programación tradicional, sino el diseño meticuloso del prompt del sistema (Protocolo ASTRA v8.0).

Este protocolo fuerza al modelo a:
* Ignorar el lenguaje natural en la salida.
* Aplicar metodologías inyectadas estáticamente (Design Thinking, Business Model Canvas, NABC).
* Generar una salida estrictamente en formato JSON validado, lo que permite la extracción "quirúrgica" de datos para la generación de documentos.

Puedes consultar el prompt completo en el archivo `ASTRA_v8_Prompt.txt` incluido en este repositorio.

## 🛠️ Cómo Funciona (Workflow)

1.  El usuario envía un comando (`!idea`) con su concepto de negocio a través de Discord.
2.  Make.com captura el mensaje y lo envía a OpenAI.
3.  OpenAI procesa la idea usando la metodología RAG estática y devuelve un objeto JSON estructurado.
4.  Make.com parsea el JSON y ejecuta acciones en paralelo:
    * Crea un Google Doc con un plan de negocio detallado.
    * Inyecta los datos en una plantilla de Google Slides utilizando etiquetas dinámicas (ej. `{{titulo}}`).
    * Registra la ejecución en Google Sheets para auditoría.
5.  El usuario recibe una notificación en Discord con los enlaces a los documentos generados.

## 📂 Estructura del Repositorio

* `README.md`: Documentación del proyecto.
* `ASTRA_v8_Prompt.txt`: El prompt del sistema utilizado en OpenAI.
* `Make_Blueprint.json` (Si lo incluyes): Plantilla importable para replicar el escenario en Make.com.
* `assets/`: Imágenes y diagramas de la arquitectura.

## 💡 Lecciones Aprendidas

El desarrollo de ASTRA demostró que para aplicaciones empresariales, un prompt estándar es insuficiente. Fue necesario diseñar un "Sistema Operativo" para el LLM (el protocolo ASTRA), evolucionando desde un rol conversacional hasta un motor lógico estricto. Además, la necesidad de manejar objetos JSON anidados y ejecuciones paralelas justificó la elección de Make.com sobre alternativas más lineales.

---
**Autor:** Fernando Martínez Buitrago
