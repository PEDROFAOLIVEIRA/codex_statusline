# Codex Statusline

[🇧🇷 Português](README.md) · [🇺🇸 English](README.en.md) · [🇪🇸 Español](README.es.md) · [🇯🇵 日本語](README.ja.md) · [🇨🇳 中文](README.zh.md)

Uma configuração compacta para a linha de status nativa do **Codex CLI**. Ela reúne modelo, projeto, branch Git, uso de contexto, limite de uso e modo de aprovação em uma linha.

![Prévia da statusline nativa do Codex](assets/statusline-preview.svg)

> A imagem é uma prévia ilustrativa. O Codex mostra indicadores nativos como texto; este projeto não desenha barras gráficas de progresso.

## Exemplo

```text
GPT-6-Luna medium · 08 - statusline · main · Context 8% used · 258K window · weekly 98% left · Ask for approval
```

Os valores variam conforme a sessão, a conta e a versão do Codex. Indicadores sem dados disponíveis podem ser omitidos.

## Instalação

1. Abra `%USERPROFILE%\.codex\config.toml` no Windows ou `~/.codex/config.toml` no macOS/Linux.
2. Copie o bloco de [`codex-statusline.toml`](codex-statusline.toml).
3. Se já existir uma seção `[tui]`, mescle apenas as duas opções abaixo e preserve as demais configurações.
4. Reinicie o Codex. No Codex CLI, também é possível abrir `/statusline` para selecionar e reordenar os indicadores.

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

| Indicador | Informação |
| --- | --- |
| `model-with-reasoning` | Modelo e nível de raciocínio atual. |
| `project-name` | Nome do projeto detectado pelo Codex. |
| `git-branch` | Branch atual, quando a pasta está em um repositório Git. |
| `context-used` | Percentual do contexto da conversa já utilizado. |
| `context-window-size` | Tamanho total da janela de contexto, quando disponível. |
| `weekly-limit` | Uso semanal restante, quando disponível para a conta. |
| `approval-mode` | Modo atual de aprovação de comandos. |

O Codex também oferece `five-hour-limit`; adicione esse item a `status_line` para mostrar o limite de 5 horas.

## O que a configuração não faz

A statusline nativa do Codex aceita indicadores predefinidos e os renderiza no rodapé. Ela não executa um script de renderização personalizado. Portanto, este projeto mostra percentuais em texto, sem barras gráficas, cores definidas por faixas de uso ou horários de reset. `status_line_use_colors` ativa as cores nativas do tema, mas não configura limiares de cor.

O Codex também não fornece nesta linha nativa indicadores de cache de prompt ou de tokens que seriam regravados no cache.

## Compatibilidade

Validado com Codex CLI `0.165.0-alpha.1.2` em Windows. Os indicadores podem variar entre versões; use `/statusline` para conferir as opções da sua instalação.

## Licença

MIT. Consulte [`LICENSE`](LICENSE).
