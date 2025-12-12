# River - Asistente Virtual Inteligente con LangGraph

## 🎯 Visión General

River es un asistente virtual inteligente que opera mediante comandos de voz, diseñado con una arquitectura moderna basada en agentes utilizando **LangGraph**. El sistema se activa con la frase "Oye River" y permite gestionar tareas diarias, calendario, comunicación y búsqueda de información mediante un enfoque de grafos de agentes.

## 🏗️ Arquitectura del Sistema

### Sistema Central de Agentes (LangGraph)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                             River Orchestrator                              │
│                          (LangGraph State Machine)                          │
└─────────────────┬───────────────────────────────┬───────────────────────────┘
                  │                               │
                  │                      ┌────────▼───────────────────────────┐
                  │                      │           Memory Manager           │
                  │                      │         (Perfil + Contexto)        │
                  │                      └────────────────────────────────────┘
                  │
┌─────────────────▼───────────────────────────────────────────────────────────┐
│                       Router de Agentes Especializados                      │
└─────┬────────────┬────────────────┬────────────┬────────────┬──────────┬────┘
      │            │                │            │            │          │     
┌─────▼──┐   ┌─────▼──────┐  ┌──────▼───┐   ┌────▼─────┐  ┌───▼────┐ ┌───▼────┐
│Calendar│   │Comunication│  │  Search  │   │  Tasks   │  │ Weather│ │ System │
│ Agent  │   │   Agent    │  │   Agent  │   │  Agent   │  │ Agent  │ │ Agent  │
└────────┘   └────────────┘  └──────────┘   └──────────┘  └────────┘ └────────┘
```

### Componentes Principales

#### 1. **Voice Activation System**
- **Wake Word Detection**: Detecta la frase de activacion "Oye River"
- **Command Recognition**: Modelo STT para transcripción
- **Voice Authentication**: Opcional (Futuro) - reconocimiento de voz del usuario

#### 2. **Orchestrator (LangGraph)**
- **State Management**: Gestión del estado de conversación
- **Agent Routing**: Enrutamiento inteligente a agentes especializados
- **Human-in-the-Loop**: Confirmación para acciones críticas
- **Context Management**: Mantenimiento del contexto de diálogo

#### 3. **Agentes Especializados**
- **Calendar Agent**: Gestión completa de calendario (Google Calendar)
- **Communication Agent**: WhatsApp/Llamadas/Email integrado
- **Search Agent**: Búsqueda web + RAG para información personal
- **Task Agent**: Gestión de tareas y recordatorios
- **Weather Agent**: Información meteorológica con ubicación
- **System Agent**: Control del dispositivo/automation

#### 4. **Memory System**
- **Profile Manager**: Gestion del perfil de usuario personalizado localmente

## 📁 Estructura de Archivos

```bash
Virtual_Assistant/
├── README.md
├── requirements.txt
├── setup.py
├── src/
│   ├── __init__.py
│   ├── main.py
│   ├── orchestrator/
│   │   ├── __init__.py
│   │   ├── state.py           # Definición del estado LangGraph
│   │   ├── graph.py           # Grafo principal LangGraph
│   │   └── nodes.py           # Nodos del grafo
│   ├── agents/
│   │   ├── __init__.py
│   │   ├── base_agent.py
│   │   ├── calendar_agent.py
│   │   ├── communication_agent.py
│   │   ├── search_agent.py
│   │   ├── task_agent.py
│   │   ├── weather_agent.py
│   │   └── system:agent.py
│   ├── voice/
│   │   ├── __init__.py
│   │   ├── wake_word.py
│   │   ├── stt_engine.py
│   │   ├── tts_engine.py
│   │   └── voice_auth.py     #Optional for future
│   ├── memory/
│   │   ├── __init__.py
│   │   ├── profile_manager.py
│   ├── tools/
│   │   ├── __init__.py
│   │   ├── calendar_tools.py
│   │   ├── comunication_tools.py
│   │   ├── system_tools.py
│   │   └── web_tools.py
│   └── utils/
│       ├── __init__.py
│       ├── config.py
│       ├── logger.py
│       └── validators.py
├── models/
└── tests/
    ├── __init__.py
    ├── test_agents.py
    ├── test_orchestrator.py
    └── test_voice.py
```

## 🚀 Orden de Desarrollo (Versión LangGraph)

### Fase 1: Sistema de Voz
1. **Wake word detection**
2. **STT Engine**
3. **TTS Engine** para respuestas

### Fase 2: Configuración Base y Orchestrator
1. **Setup del proyecto** con estructura moderna
2. **Implementar State de LangGraph** para gestión de estado
3. **Crear grafo principal** con routing básico
4. **Configurar memoria** con vector store

### Fase 2.5: Integracion
1. **Integración voz-orchestrator**

### Fase 3: Agentes
1. **Calendar Agent** con herramientas API
2. **Communication Agent** para WhatsApp/Email
3. **Search Agent** con RAG
4. **Tasks Agent** para gestión de tareas
5. **Weather Agent** con herramientas API
6. **System Agent** para gestión del sistema del movil

### Fase 4: Despliegue en dispositivo movil
2. **Optimización** para móvil

### Fase 5: Integración y Features Avanzados (Opcional/Futuro)
1. **Human-in-the-loop** con confirmaciones
2. **Context management** para conversaciones largas
3. **Multi-modalidad** (voz + texto + pantalla)
4. **Learning system** para personalización

### Fase 6: Deployment y Optimización
1. **Dockerización** completa
2. **Testing** exhaustivo
3. **Documentación** completa

## 🔧 Requisitos Técnicos

### Dependencias Principales
```txt

```

### Configuración de Entorno
```bash
# Variables críticas
OPENAI_API_KEY=your_key_here
```

## 🎮 Uso y Ejemplos

### Iniciar el Sistema
```bash

## Instalación
pip install -r requirements.txt

# Ejecución
python -m river.main
```

### Comandos de Ejemplo
```
"Oye River, ¿qué tengo hoy en el calendario?"
"Oye River, envía un mensaje a Maria diciendo que llegaré tarde"
"Oye River, ¿qué tiempo hace mañana?"
"Oye River, busca información sobre LangGraph"
"Oye River, crea una reunión mañana a las 3 PM"
```

## 🤖 Features Avanzados Implementados

### 1. **Sistema de Agentes Colaborativos**
- Routing inteligente basado en intención
- Fallback entre agentes
- Ejecución paralela cuando es posible

### 2. **Memoria Contextual**
- Perfil de usuario persistente

### 3. **Human-in-the-Loop**
- Confirmación para acciones críticas
- Corrección de comandos malinterpretados

### 4. **Integración Multi-plataforma**
- APIs de calendario (Google)
- Mensajería (WhatsApp, Email)
- Servicios web (Weather, News, Search)

## 📊 Estado del Proyecto

| Componente | Estado | Prioridad |
|------------|---------|-----------|
| Sistema de Voz | 🔄 En desarrollo | Alta |
| Orchestrator LangGraph | ⏳ Pendiente | Alta |
| Calendar Agent | ⏳ Pendiente | Media |
| Communication Agent | ⏳ Pendiente | Media |
| Search Agent | ⏳ Pendiente | Baja |
| Memory System | ⏳ Pendiente | Alta |

## 📄 Licencia

MIT License - ver LICENSE.md para detalles

---

**Nota**: Este proyecto está en desarrollo activo. La arquitectura puede evolucionar basada en nuevas características de LangGraph y feedback de uso.
