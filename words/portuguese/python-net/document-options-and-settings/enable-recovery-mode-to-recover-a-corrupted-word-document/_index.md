---
category: general
date: 2026-10-04
description: Ative o modo de recuperação no Aspose.Words para recuperar com segurança
  um documento Word corrompido. Siga o guia passo a passo com código Python completo
  e explicações.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: pt
lastmod: 2026-10-04
og_description: Ative o modo de recuperação para restaurar um documento Word corrompido
  usando Aspose.Words. Este tutorial mostra o código Python exato, por que ele funciona
  e como lidar com casos extremos.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: Ative o modo de recuperação para restaurar um documento Word corrompido
  – guia completo
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: Ativar o modo de recuperação para recuperar um documento Word corrompido
url: /pt/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ativar o modo de recuperação para recuperar um documento Word corrompido

Se você precisar **ativar o modo de recuperação** ao carregar um arquivo Word, este guia mostra exatamente como fazer isso com Aspose.Words for Python. Ao ativar o modo de recuperação, você pode **recuperar um documento Word corrompido** que de outra forma lançaria uma exceção.

Nas seções a seguir, você aprenderá:

* Quais classes e propriedades controlam o comportamento de recuperação.  
* Como carregar um arquivo `.docx` potencialmente danificado sem travar sua aplicação.  
* Dicas para solucionar problemas comuns de carregamento e personalizar a estratégia de recuperação.

> **Pré‑requisito** – Você tem o Aspose.Words for Python instalado (`pip install aspose-words`) e um entendimento básico de I/O de arquivos em Python.

## O que o modo de recuperação faz e por que você deve ativá‑lo

Aspose.Words analisa a estrutura interna de um arquivo Word antes de expô‑lo como um objeto `Document`. Quando o arquivo está corrompido — partes ausentes, XML quebrado ou relacionamentos inválidos — o analisador pode:

| Modo | Comportamento |
|------|----------------|
| `STRICT` | Lança uma exceção ao primeiro sinal de corrupção. |
| `IGNORE_ERRORS` | Ignora partes ilegíveis, mas pode perder conteúdo silenciosamente. |
| `RECOVER` (a opção **ativar modo de recuperação**) | Tenta reconstruir o documento, preservando o máximo de conteúdo possível e expondo o modo escolhido via `load_options.recovery_mode`. |

`RECOVER` é a escolha recomendada quando você precisa **recuperar documentos Word corrompidos** para processamento posterior, como extração de texto ou conversão para PDF.

## Etapa 1: Criar LoadOptions e ativar o modo de recuperação

O primeiro passo é instanciar `LoadOptions` e definir a propriedade `recovery_mode` para `RecoveryMode.RECOVER`. Isso indica à biblioteca que ela deve seguir o caminho de recuperação durante a análise.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**Por que isso importa:**  
Se você pular esta etapa e o documento estiver danificado, o construtor `aw.Document(...)` lançará `InvalidOperationException`. Ativar o modo de recuperação evita a falha e fornece um objeto `Document` parcialmente reparado com o qual ainda é possível trabalhar.

## Etapa 2: Carregar o documento potencialmente corrompido usando as opções especificadas

Passe a instância `load_options` para o construtor `Document`. O carregador aplicará agora o algoritmo de recuperação automaticamente.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**Dica:** Substitua `YOUR_DIRECTORY` pelo caminho absoluto ou relativo que seu runtime pode acessar. Se o arquivo não existir, Aspose.Words lançará um `FileNotFoundError` antes mesmo de chegar à lógica de recuperação.

## Etapa 3: Verificar se o modo de recuperação foi aplicado

Você pode confirmar o modo ativo inspecionando `load_options.recovery_mode`. Isso é útil para registro ou tratamento condicional mais adiante no pipeline.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**Saída esperada**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

Se a saída mostrar `RECOVER`, você ativou com sucesso o **modo de recuperação** e o documento está pronto para processamento adicional (por exemplo, extração de texto, conversão para PDF ou salvamento de uma cópia reparada).

## Etapa 4 (opcional): Salvar uma cópia reparada para uso futuro

Após o carregamento, pode ser interessante persistir o documento recuperado para não precisar repetir a etapa de recuperação.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Salvar cria um novo `.docx` que o Aspose.Words considera válido, podendo ser aberto no Microsoft Word sem avisos.

## Perguntas comuns e tratamento de casos extremos

| Pergunta | Resposta |
|----------|----------|
| **E se o documento estiver completamente ilegível?** | Mesmo no modo `RECOVER`, alguns arquivos estão além do reparo. O objeto `Document` será criado, mas pode conter apenas uma página vazia. Verifique `doc.get_page_count()` para confirmar o conteúdo. |
| **Posso mudar para `IGNORE_ERRORS` após o carregamento?** | Não. O modo de recuperação deve ser definido **antes** da execução do construtor `Document`. Crie uma nova instância de `LoadOptions` se precisar de outra estratégia. |
| **O modo de recuperação afeta o desempenho?** | Sim, ele adiciona uma pequena sobrecarga porque a biblioteca tenta reconstruir partes quebradas. O impacto é insignificante para a maioria dos arquivos (< 2 MB). |
| **Esta abordagem é independente de linguagem?** | O mesmo conceito existe nas APIs .NET, Java e Node.js (`LoadOptions.RecoveryMode`). A sintaxe do código muda, mas a lógica é idêntica. |

## Dica profissional: Registrar informações detalhadas de recuperação

Aspose.Words fornece um `LoadOptions.recovery_callback` que recebe mensagens detalhadas sobre cada etapa de recuperação. Configurá‑lo pode ajudar a diagnosticar por que um documento específico falhou.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

Agora cada correção interna (por exemplo, “Removed duplicate relationship”) será impressa no console.

## Exemplo completo e executável

Juntando todas as peças, aqui está um script autônomo que você pode copiar‑colar e executar imediatamente:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

Executar o script imprime o modo de recuperação, a contagem de páginas e uma lista de palavras extraídas do documento reparado. Se você definir `save_repaired=True`, um novo arquivo limpo aparecerá ao lado do original.

## Conclusão

Agora você sabe como **ativar o modo de recuperação** no Aspose.Words for Python e **recuperar documentos Word corrompidos** de forma confiável. As etapas principais são:

1. Criar `LoadOptions` e definir `recovery_mode` para `RECOVER`.  
2. Carregar o `.docx` usando essas opções.  
3. Verificar o modo e, opcionalmente, salvar uma cópia reparada.

A partir daqui, você pode explorar tópicos adicionais como **extrair texto de um documento recuperado**, **convertê‑lo para PDF** ou **automatizar a recuperação em lote** para grandes bibliotecas de documentos.

---


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Recover Corrupted DOCX – Complete Guide to Enable Recovery Mode & Get Page](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}