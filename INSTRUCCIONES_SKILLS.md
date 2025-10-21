# 🎯 Instrucciones para Usar las Skills de AgnoAGI

## ✅ Archivos Creados

Se han creado exitosamente **5 Skills profesionales** en `.claude/skills/`:

1. **Python_AI_Fundamentals** (12 KB)
   - Fundamentos Python para IA
   - NumPy, Pandas, PyTorch, async patterns
   - Type hints, testing, best practices

2. **Ollama_LocalModels** (17 KB)
   - Modelos locales con Ollama
   - Streaming, embeddings, RAG
   - Vision models, FastAPI integration

3. **AgnoAGI_Agents** (19 KB)
   - Framework Agno completo
   - Multi-agent systems, teams
   - Reasoning agents, custom tools
   - Memory, knowledge bases

4. **PaidModels_Integration** (21 KB)
   - Claude, OpenAI, Gemini, Groq
   - Function calling, vision
   - Cost tracking, optimization

5. **Production_Deployment** (22 KB)
   - Docker, Kubernetes, FastAPI
   - Monitoring, CI/CD
   - Security, scalability

**Total**: 91 KB de documentación experta

---

## 📋 Pasos para Integrar las Skills

### Paso 1: Verificar Skills Creadas

```bash
# Ver todas las skills
ls -lh .claude/skills/*/SKILL.md

# Deberías ver:
# Python_AI_Fundamentals/SKILL.md
# Ollama_LocalModels/SKILL.md
# AgnoAGI_Agents/SKILL.md
# PaidModels_Integration/SKILL.md
# Production_Deployment/SKILL.md
```

### Paso 2: Usar Skills en Claude Code (Ya están listas)

Las skills YA ESTÁN ACTIVAS en este directorio. Simplemente:

```bash
# Abrir Claude Code en este directorio
claude-code .

# O si ya estás en Claude Code, las skills se cargan automáticamente
```

### Paso 3: Invocar Skills

#### Opción A: Uso Automático (Recomendado)

Claude Code carga skills automáticamente según el contexto:

```
Tú: "Crea un agente Agno que busque en la web"
Claude: [Carga automáticamente AgnoAGI_Agents + PaidModels_Integration]
```

#### Opción B: Uso Explícito

Invoca skills manualmente:

```bash
# En Claude Code, usa slash command
/skill AgnoAGI_Agents

# Luego pregunta
Tú: "Muéstrame cómo crear un reasoning agent"
```

### Paso 4: Configurar para Uso Global (Opcional)

Para usar estas skills en TODOS tus proyectos:

#### En macOS/Linux:
```bash
# Crear directorio global de skills
mkdir -p ~/.claude/skills

# Copiar skills
cp -r .claude/skills/* ~/.claude/skills/

# O crear symlink (recomendado)
ln -s $(pwd)/.claude/skills ~/.claude/skills/agno-skills
```

#### En Windows:
```powershell
# Crear directorio global
New-Item -Path "$env:USERPROFILE\.claude\skills" -ItemType Directory -Force

# Copiar skills
Copy-Item -Path ".claude\skills\*" -Destination "$env:USERPROFILE\.claude\skills" -Recurse
```

### Paso 5: Configurar Claude Desktop (Si lo usas)

Si usas Claude Desktop app, agrega al config:

**Ubicación del archivo de configuración:**
- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`
- Linux: `~/.config/Claude/claude_desktop_config.json`

**Contenido:**
```json
{
  "skills": {
    "paths": [
      "/ruta/completa/a/.claude/skills"
    ]
  }
}
```

---

## 🚀 Ejemplos de Uso Inmediato

### Ejemplo 1: Crear Agente Simple con Claude
```
Tú: "Crea un agente Agno con Claude API que responda preguntas"

Claude carga: AgnoAGI_Agents + PaidModels_Integration
Genera: Código completo con Agent, Claude model, y ejemplos
```

### Ejemplo 2: Agente Local con Ollama
```
Tú: "Agente Agno con Ollama llama3.2 para análisis de texto"

Claude carga: AgnoAGI_Agents + Ollama_LocalModels
Genera: Setup de Ollama, configuración de agente, código listo
```

### Ejemplo 3: Sistema Multi-Agente
```
Tú: "Sistema de 3 agentes: web researcher, finance analyst, writer"

Claude carga: AgnoAGI_Agents + PaidModels_Integration
Genera: Team de agentes con especialización, coordinación
```

### Ejemplo 4: RAG con Embeddings
```
Tú: "Implementa RAG con Ollama embeddings para búsqueda en docs"

Claude carga: Ollama_LocalModels + AgnoAGI_Agents
Genera: Knowledge base, embeddings, search, RAG completo
```

### Ejemplo 5: Deploy a Producción
```
Tú: "Dockeriza mi app de agentes con FastAPI, Nginx, PostgreSQL"

Claude carga: Production_Deployment + Python_AI_Fundamentals
Genera: Dockerfile, docker-compose, FastAPI app, configs
```

---

## 🎓 Casos de Uso Avanzados

### 1. Backend Empresarial Completo
```
Tú: "API FastAPI con agentes Agno, Claude API, Docker, Kubernetes,
     monitoreo Prometheus, CI/CD GitHub Actions"

Skills usadas: TODAS (Python, Agno, Paid Models, Production)
Resultado: Sistema completo production-ready
```

### 2. Prototipo Rápido Gratuito
```
Tú: "Agente local con Ollama para chatbot básico, sin APIs de pago"

Skills usadas: Ollama_LocalModels, AgnoAGI_Agents
Resultado: Chatbot funcionando 100% local
```

### 3. Análisis de Datos con IA
```
Tú: "Agente que analiza CSV con Pandas, genera insights con GPT-4o"

Skills usadas: Python_AI_Fundamentals, PaidModels_Integration
Resultado: Pipeline de análisis automatizado
```

### 4. Research Assistant
```
Tú: "Agente que busca web, lee PDFs, genera reportes markdown"

Skills usadas: AgnoAGI_Agents (tools: web, file)
Resultado: Research assistant completo
```

---

## 🔍 Verificar que Todo Funciona

### Test 1: Verificar Archivos
```bash
cd .claude/skills
ls -la

# Deberías ver:
# Python_AI_Fundamentals/
# Ollama_LocalModels/
# AgnoAGI_Agents/
# PaidModels_Integration/
# Production_Deployment/
# README.md
```

### Test 2: Ver Contenido de una Skill
```bash
head -n 20 .claude/skills/AgnoAGI_Agents/SKILL.md

# Deberías ver:
# ---
# name: AgnoAGI Agents
# description: Expert guidance...
# ---
```

### Test 3: Probar en Claude Code
```
# En Claude Code:
Tú: "Muéstrame un ejemplo de agente Agno básico"

# Claude debería generar código usando la skill AgnoAGI_Agents
```

---

## 📚 Cheat Sheet de Comandos

### Ver Skills Disponibles
```bash
# Listar skills
ls .claude/skills/

# Ver tamaños
du -sh .claude/skills/*

# Ver metadata de una skill
head -n 10 .claude/skills/AgnoAGI_Agents/SKILL.md
```

### Búsqueda en Skills
```bash
# Buscar término en todas las skills
grep -r "FastAPI" .claude/skills/

# Buscar en skill específica
grep "reasoning" .claude/skills/AgnoAGI_Agents/SKILL.md

# Ver ejemplos de código
grep -A 10 "```python" .claude/skills/AgnoAGI_Agents/SKILL.md
```

### Actualizar Skills
```bash
# Editar skill
code .claude/skills/AgnoAGI_Agents/SKILL.md

# Agregar recursos
mkdir .claude/skills/AgnoAGI_Agents/resources
# Agregar PDFs, ejemplos, configs...
```

---

## 🛠️ Troubleshooting

### Problema: Skills no se cargan
**Solución:**
```bash
# Verificar permisos
chmod -R 644 .claude/skills/*/SKILL.md

# Verificar estructura
find .claude/skills -name "SKILL.md"
```

### Problema: Skill desactualizada
**Solución:**
```bash
# Editar skill manualmente
code .claude/skills/SkillName/SKILL.md

# O pull cambios si hay updates
git pull origin claude/research-context7-skills-011CUKdeTHYftXFyBNaUMGnr
```

### Problema: Conflicto entre skills
**Solución:**
```bash
# Desactivar skill temporalmente
mv .claude/skills/SkillName .claude/skills/SkillName.disabled

# Reactivar
mv .claude/skills/SkillName.disabled .claude/skills/SkillName
```

---

## 🎯 Siguiente Pasos Recomendados

### 1. Prueba Básica (5 min)
```
# En Claude Code:
Tú: "Crea un agente Agno simple que responda preguntas"
```

### 2. Proyecto Local (15 min)
```
Tú: "Agente con Ollama llama3.2, streaming responses, guardar en archivos"
```

### 3. API REST (30 min)
```
Tú: "FastAPI con endpoint /chat, agente Agno con Claude, Docker"
```

### 4. Sistema Completo (1-2 horas)
```
Tú: "Sistema multi-agente, PostgreSQL, Redis, Docker Compose, monitoring"
```

---

## 📖 Recursos y Documentación

### Documentación Oficial
- **Agno**: https://docs.agno.com/
- **Ollama**: https://ollama.com/
- **Claude API**: https://docs.anthropic.com/
- **OpenAI API**: https://platform.openai.com/docs
- **FastAPI**: https://fastapi.tiangolo.com/

### Ejemplos en las Skills
Cada skill incluye:
- ✅ Ejemplos de código completos
- ✅ Patrones de producción
- ✅ Best practices
- ✅ Troubleshooting
- ✅ Links a docs oficiales

### Repositorio
```bash
# Ver commits
git log --oneline

# Ver cambios
git show HEAD

# Branch actual
git branch
```

---

## ✨ Tips Pro

### 1. Combina Skills
```
Tú: "Usa Ollama local para desarrollo, Claude API para producción,
     deploy con Docker"
```
Claude cargará: Ollama + PaidModels + Production

### 2. Sé Específico
```
❌ "Crea un agente"
✅ "Crea un agente Agno con Claude 3.7 Sonnet, que busque en web
    con DuckDuckGo, guarde en PostgreSQL, y tenga FastAPI endpoint"
```

### 3. Itera
```
Tú: "Crea agente básico"
Tú: "Ahora agrégale memoria"
Tú: "Ahora deplóyalo con Docker"
```
Skills se cargan progresivamente

### 4. Aprende de los Ejemplos
```bash
# Las skills tienen 100+ ejemplos de código
# Léelos para entender patrones
cat .claude/skills/AgnoAGI_Agents/SKILL.md | grep -A 20 "```python"
```

---

## 🎁 Bonus: Plantillas Rápidas

### Plantilla 1: Chatbot Local
```
Tú: "Chatbot con Ollama llama3.2, interfaz FastAPI, streaming"
```

### Plantilla 2: Research Agent
```
Tú: "Agente que busca web, analiza resultados, genera markdown report"
```

### Plantilla 3: Data Analyst
```
Tú: "Agente que lee CSV, analiza con Pandas, genera insights con GPT-4o"
```

### Plantilla 4: Multi-Agent System
```
Tú: "Team de agentes: researcher, analyst, writer. Claude API, PostgreSQL"
```

### Plantilla 5: Production API
```
Tú: "FastAPI + Agno + Claude + Docker + K8s + Prometheus"
```

---

## 📞 Soporte

Si tienes problemas:

1. ✅ Lee este documento
2. ✅ Revisa `.claude/skills/README.md`
3. ✅ Consulta la skill específica
4. ✅ Busca en docs oficiales
5. ✅ Pregunta a Claude Code directamente

---

## 🎉 ¡Listo para Empezar!

Las skills están **100% funcionales** y listas para usar.

**Empieza ahora:**
```
# Abre Claude Code
claude-code .

# O si ya estás en Claude Code:
Tú: "Muéstrame un ejemplo de agente Agno"
```

---

**Creado**: 2025-10-21
**Versión**: 1.0.0
**Branch**: `claude/research-context7-skills-011CUKdeTHYftXFyBNaUMGnr`
**Skills**: 5 archivos, 91 KB de documentación experta
