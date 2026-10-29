# Codex Statusline

[🇧🇷 Português](README.md) · [🇺🇸 English](README.en.md) · [🇪🇸 Español](README.es.md) · [🇯🇵 日本語](README.ja.md) · [🇨🇳 中文](README.zh.md)

Una configuración compacta para la línea de estado nativa de **Codex CLI**. Reúne el modelo, el proyecto, la rama Git, el uso del contexto, los límites de uso y el modo de aprobación en una sola línea.

![Vista previa de la línea de estado nativa de Codex](assets/statusline-preview.svg)

> La imagen es una vista previa ilustrativa. Codex muestra sus indicadores nativos como texto; este proyecto no dibuja barras gráficas de progreso.

## Ejemplo

```text
GPT-6-Luna medium · 08 - statusline · main · Context 8% used · 258K window · weekly 98% left · Ask for approval
```

Los valores varían según la sesión, la cuenta y la versión de Codex. Los indicadores pueden omitirse cuando no hay datos disponibles.

## Instalación

1. Abre `%USERPROFILE%\.codex\config.toml` en Windows o `~/.codex/config.toml` en macOS/Linux.
2. Copia el bloque de [`codex-statusline.toml`](codex-statusline.toml).
3. Si ya existe una sección `[tui]`, combina solo las dos opciones siguientes y conserva el resto de la configuración.
4. Reinicia Codex. En Codex CLI, también puedes abrir `/statusline` para seleccionar y reordenar los indicadores.

```toml
[tui]
status_line = [
  "model-with-reasoning",
  "project-name",
  "git-branch",
  "context-used",
  "context-window-size",
  "weekly-limit",
  "approval-mode",
]
status_line_use_colors = true
```

## Indicadores

| Indicador | Información |
| --- | --- |
| `model-with-reasoning` | Modelo y nivel de razonamiento actuales. |
| `project-name` | Nombre del proyecto detectado por Codex. |
| `git-branch` | Rama actual, si la carpeta pertenece a un repositorio Git. |
| `context-used` | Porcentaje del contexto de conversación utilizado. |
| `context-window-size` | Tamaño total de la ventana de contexto, cuando está disponible. |
| `weekly-limit` | Uso semanal restante, cuando la cuenta ofrece estos datos. |
| `approval-mode` | Modo actual de aprobación de comandos. |

Codex también ofrece `five-hour-limit`; añádelo a `status_line` para mostrar el límite de 5 horas.

## Lo que esta configuración no hace

La línea nativa de Codex acepta indicadores predefinidos y los muestra en el pie de la interfaz. No ejecuta un script de renderizado personalizado. Por eso, este proyecto muestra porcentajes en texto, sin barras gráficas, colores por umbral ni tiempos de reinicio. `status_line_use_colors` habilita los colores nativos del tema, pero no define umbrales de color según el uso.

La línea nativa tampoco ofrece indicadores de actividad de la caché de prompts ni de tokens que se volverían a escribir en ella.

## Compatibilidad

Validado con Codex CLI `0.165.0-alpha.1.2` en Windows. Los indicadores disponibles pueden variar según la versión; usa `/statusline` para consultar tu instalación.

## Licencia

MIT. Consulta [`LICENSE`](LICENSE).
