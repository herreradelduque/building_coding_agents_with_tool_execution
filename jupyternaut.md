# Jupyternaut / Jupyter AI — Guía paso a paso

## Resumen
Esta guía explica cómo instalar y configurar **Jupyternaut (persona Jupyter AI)**, establecer proveedores de modelos (Anthropic/Claude, OpenRouter, Hugging Face) y usar el magic `%%ai` con ejemplos y solución de problemas.

---

## Requisitos previos
- Python 3.10+ recomendado
- `pip` disponible
- JupyterLab 4.x o superior recomendado
- Familiaridad básica con terminal y variables de entorno

---

## 1. Instalación: JupyterLab y Jupyternaut
https://pypi.org/project/jupyter-ai-jupyternaut/



### 1.4 Iniciar JupyterLab
```bash
jupyter lab
```

Abre la UI de JupyterLab y busca el panel Jupyter AI / Chat (Jupyternaut).

---

## 2. Cómo Jupyter AI selecciona proveedores
Jupyter AI soporta múltiples proveedores mediante configuración (variables de entorno o ajustes por proveedor). Para endpoints compatibles con OpenAI, puede configurarse OpenRouter como interfaz unificada.

---

## 3. Configurar Claude (Anthropic)

### 3.1 Obtener la API key
Inicia sesión en Anthropic/Claude y crea una API key en tu cuenta.

### 3.2 Establecer la variable de entorno (macOS / Linux)
```bash
export ANTHROPIC_API_KEY="tu_api_key_anthropic"
```

En PowerShell (Windows):
```powershell
setx ANTHROPIC_API_KEY "tu_api_key_anthropic"
```

### 3.3 Ejemplo desde un notebook
```python
%%ai anthropic claude-3-5-sonnet-latest
Write a Python function that normalizes a pandas DataFrame column to zero mean and unit variance.
```

### 3.4 Verificar uso y cuotas
Comprueba el dashboard de Anthropic para límites y uso; Jupyternaut mostrará errores si la clave no es válida o se excede cuota.

---

## 4. OpenRouter (opción online gratuita recomendada)
api_key = "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"
### 4.1 Por qué OpenRouter
OpenRouter ofrece una API unificada que proxy modelos (Llama, Mistral, Qwen, etc.) y disponibilidad en capa gratuita para algunos modelos.

### 4.2 Crear cuenta y obtener API key
Visita: https://openrouter.ai y genera una API key desde Dashboard → API Keys.

### 4.3 Establecer la variable de entorno
```bash
export OPENROUTER_API_KEY="tu_api_key_openrouter"
```

### 4.4 Ejemplo en notebook
```python
%%ai openrouter meta-llama/llama-3.1-8b-instruct
Explain the difference between overfitting and underfitting in plain language.
```

### 4.5 Notas y límites
La disponibilidad y cuotas varían: revisa el dashboard de OpenRouter.

---

## 6. Modelos locales (completamente offline)

### 6.1 Ollama (runtime local recomendado)
Instala Ollama desde https://ollama.com/download y sigue las instrucciones de la plataforma.

Ejemplo: descargar un modelo
```bash
ollama pull llama3
```

Usar en notebook:
```python
%%ai ollama llama3
Write a Python loop that prints the first 10 Fibonacci numbers.
```

### 6.2 llama.cpp u otros runtimes locales
Puedes usar `llama.cpp` o runtimes locales de Hugging Face; asegúrate de que el modelo quepa en tu RAM/VRAM.

Configura Jupyter AI para apuntar al endpoint local de inferencia según la documentación del runtime.

---

## 8. Consejos de configuración y gestión de entorno

### 8.1 Guardar claves de forma segura
Usa un archivo `.env` (con `python-dotenv`) o tu perfil de shell (`~/.zshrc`, `~/.bashrc`) para persistir claves.
No guardes claves en control de versiones.

### 8.2 Ejemplo de `.env`
```env
ANTHROPIC_API_KEY=tu_api_key_anthropic
OPENROUTER_API_KEY=tu_api_key_openrouter
HF_API_TOKEN=tu_token_huggingface
```

### 8.3 Reiniciar JupyterLab
Si JupyterLab estaba en ejecución al cambiar variables de entorno, reinícialo para que recoja los cambios.


# Establecer variables (ejemplo)
export ANTHROPIC_API_KEY="..."
export OPENROUTER_API_KEY="..."
export HF_API_TOKEN="..."
```

---

## 12. Enlaces útiles
- Documentación Jupyter AI (integraciones OpenRouter / OpenAI)
- Documentación y signup de OpenRouter: https://openrouter.ai
- Repositorio y PyPI de Jupyternaut

---

## Notas finales
Guarda las claves en un lugar seguro y reinicia JupyterLab tras cualquier cambio de entorno.
