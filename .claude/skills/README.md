# AgnoAGI Skills para Claude Code

Este directorio contiene 5 Skills profesionales para desarrollo de agentes AI con AgnoAGI.

## Skills Creados

### 1. Python_AI_Fundamentals
Fundamentos de Python para desarrollo AI/ML incluyendo:
- Librerías esenciales (NumPy, Pandas, PyTorch, TensorFlow)
- Async programming patterns
- Type hints y Pydantic validation
- Error handling y logging
- Testing y best practices

### 2. Ollama_LocalModels
Integración completa con Ollama para modelos locales:
- Instalación y configuración
- Chat y streaming
- Embeddings y RAG
- Vision models
- FastAPI integration
- Modelfile customization

### 3. AgnoAGI_Agents
Framework completo de Agno para agentes AI:
- Creación de agentes básicos y avanzados
- Multi-agent systems y teams
- Reasoning agents
- Custom tools y toolkits
- Memory y knowledge bases
- Production deployment

### 4. PaidModels_Integration
Integración con APIs comerciales:
- Anthropic Claude (streaming, tools, vision, caching)
- OpenAI (GPT-4o, function calling, assistants)
- Google Gemini (multimodal)
- Groq (fast inference)
- Amazon Bedrock
- Azure OpenAI
- Cost tracking y optimization

### 5. Production_Deployment
Deploy a producción:
- FastAPI application structure
- Docker y Docker Compose
- Kubernetes (deployments, services, HPA)
- Monitoring (Prometheus, Sentry)
- CI/CD pipelines
- Best practices

## Pasos para Integrar las Skills

### Opción 1: Usar Skills Directamente (Recomendado)

Las skills ya están en `.claude/skills/` y Claude Code las cargará automáticamente.

**Para invocar una skill:**

```
/skill Python_AI_Fundamentals
```

O simplemente menciona el contexto:

```
"Necesito crear un agente con Agno"
```

Claude Code automáticamente usará la skill `AgnoAGI_Agents`.

### Opción 2: Configurar en Claude Desktop/CLI

Si usas Claude Desktop o CLI, agrega al archivo de configuración:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

**Windows:** `%APPDATA%/Claude/claude_desktop_config.json`

**Linux:** `~/.config/Claude/claude_desktop_config.json`

```json
{
  "skills": {
    "paths": [
      "/ruta/completa/a/.claude/skills"
    ]
  }
}
```

### Opción 3: Registro Global de Skills

Para hacer las skills disponibles en todos tus proyectos:

```bash
# Copiar skills a directorio global
mkdir -p ~/.claude/skills
cp -r .claude/skills/* ~/.claude/skills/

# O crear symlink
ln -s $(pwd)/.claude/skills ~/.claude/skills/agno-skills
```

## Cómo Usar las Skills

### Uso Implícito (Automático)

Claude Code detecta automáticamente cuándo necesita una skill:

```
Usuario: "Crea un agente de Agno que busque en la web"
Claude: [Carga automáticamente AgnoAGI_Agents skill]
```

### Uso Explícito

Invoca skills manualmente con slash commands:

```bash
# Cargar skill específica
/skill AgnoAGI_Agents

# Luego hacer preguntas
"Muéstrame cómo crear un reasoning agent"
```

### Combinación de Skills

```
"Crea un agente Agno con Ollama local, despliégalo con FastAPI y Docker"
```

Claude Code cargará automáticamente:
- AgnoAGI_Agents
- Ollama_LocalModels
- Production_Deployment

## Ejemplos de Uso

### Ejemplo 1: Crear Agente Simple
```
Usuario: "Crea un agente básico con Agno y Claude API"

Claude usará: AgnoAGI_Agents + PaidModels_Integration
```

### Ejemplo 2: Deploy a Producción
```
Usuario: "Necesito dockerizar mi aplicación de agentes AI"

Claude usará: Production_Deployment
```

### Ejemplo 3: RAG Local
```
Usuario: "Implementa RAG con Ollama y embeddings"

Claude usará: Ollama_LocalModels + Python_AI_Fundamentals
```

### Ejemplo 4: Multi-Agent System
```
Usuario: "Crea un equipo de agentes: uno busca en web, otro analiza finanzas"

Claude usará: AgnoAGI_Agents + PaidModels_Integration
```

## Verificar Skills Cargadas

En Claude Code, puedes verificar las skills disponibles:

```bash
# Ver skills disponibles
/skills list

# Ver contenido de una skill
/skills show AgnoAGI_Agents
```

## Estructura de una Skill

Cada skill sigue este formato:

```markdown
---
name: Skill Name
description: Brief description
version: 1.0.0
---

# Skill Content

Documentación, ejemplos, código...
```

## Personalizar Skills

Puedes editar las skills según tus necesidades:

```bash
# Editar una skill
code .claude/skills/AgnoAGI_Agents/SKILL.md

# Agregar recursos adicionales
mkdir .claude/skills/AgnoAGI_Agents/resources
# Agregar archivos de ejemplo, configs, etc.
```

## Tips para Máximo Rendimiento

1. **Sé específico**: Menciona qué quieres hacer claramente
2. **Combina skills**: Pide tareas que requieran múltiples skills
3. **Actualiza skills**: Mantén las skills actualizadas con nuevas versiones de librerías
4. **Comparte contexto**: Menciona tu stack actual para mejores sugerencias
5. **Itera**: Pide mejoras incrementales en tu código

## Casos de Uso Comunes

### Backend API con IA
```
"Crea una API FastAPI con agentes Agno, usando Claude API,
con Docker y Kubernetes para producción"
```
Skills usadas: Todas

### Prototipo Rápido Local
```
"Agente simple con Ollama para responder preguntas sobre mis documentos"
```
Skills usadas: Ollama_LocalModels, AgnoAGI_Agents, Python_AI_Fundamentals

### Sistema Multi-Agente Empresarial
```
"Sistema de 3 agentes: research, análisis y escritor. Deploy en AWS con monitoreo"
```
Skills usadas: AgnoAGI_Agents, PaidModels_Integration, Production_Deployment

## Resolución de Problemas

### Skill no se carga
```bash
# Verificar que SKILL.md existe
ls .claude/skills/*/SKILL.md

# Verificar permisos
chmod -R 644 .claude/skills/*/SKILL.md
```

### Skill desactualizada
```bash
# Actualizar skill con nueva información
code .claude/skills/AgnoAGI_Agents/SKILL.md
# Guardar cambios
```

### Conflictos entre skills
```bash
# Desactivar skill temporalmente
mv .claude/skills/SkillName .claude/skills/SkillName.disabled
```

## Recursos Adicionales

- **Agno Docs**: https://docs.agno.com/
- **Ollama**: https://ollama.com/
- **Claude API**: https://docs.anthropic.com/
- **FastAPI**: https://fastapi.tiangolo.com/
- **Claude Code Docs**: https://docs.claude.com/claude-code

## Actualización de Skills

Para mantener las skills actualizadas:

```bash
# Pull últimos cambios
git pull origin claude/research-context7-skills-011CUKdeTHYftXFyBNaUMGnr

# O actualizar manualmente
# Edita cada SKILL.md con nueva información
```

## Contribuir

Para agregar más skills:

1. Crear directorio: `.claude/skills/Nueva_Skill/`
2. Crear archivo: `SKILL.md` con formato correcto
3. Agregar documentación y ejemplos
4. Commit y push

## Soporte

Si tienes problemas:
1. Revisa este README
2. Verifica estructura de archivos
3. Consulta documentación oficial de Claude Code
4. Abre un issue en el repositorio

---

**Creado**: 2025-10-21
**Versión**: 1.0.0
**Autor**: Claude Code
