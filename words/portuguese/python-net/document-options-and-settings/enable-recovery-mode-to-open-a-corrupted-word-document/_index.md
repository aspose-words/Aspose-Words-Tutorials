---
category: general
date: 2026-09-30
description: Ative o modo de recuperação para abrir um documento Word corrompido usando
  o Aspose.Words. Aprenda como recuperar arquivos docx corrompidos de forma segura
  e confiável.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: pt
lastmod: 2026-09-30
og_description: Ative o modo de recuperação para abrir um documento Word corrompido
  com Aspose.Words. Este guia mostra passo a passo como recuperar arquivos docx corrompidos
  e manter seu fluxo de trabalho estável.
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: Ativar o modo de recuperação para abrir documentos Word corrompidos
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: Ativar o modo de recuperação para abrir um documento Word corrompido
url: /pt/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar modo de recuperação para abrir um documento Word corrompido

Se você precisar **habilitar o modo de recuperação** ao abrir um documento Word corrompido, este tutorial mostra exatamente como fazer isso com Aspose.Words para Python. Seja o arquivo danificado durante a transferência ou editado por um programa incompatível, habilitar o modo de recuperação permite que a biblioteca tente reparar o documento em vez de lançar uma exceção.

Neste guia você aprenderá como **abrir documentos Word corrompidos**, **recuperar conteúdo de docx corrompido** e entenderá as opções que controlam o processo de **carregar documento com recuperação**. As etapas funcionam com Aspose.Words 23.10 (a versão mais recente no momento da escrita) e exigem apenas um ambiente Python padrão.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.9 ou mais recente instalado.  
* Aspose.Words para Python via .NET (`aspose-words`) instalado (`pip install aspose-words`).  
* Um arquivo DOCX que se sabe estar corrompido (para teste você pode renomear um `.docx` válido para `.zip` e quebrar o XML manualmente).

> **Dica profissional:** Mantenha um backup do arquivo original. O modo de recuperação modifica o documento em memória, mas nunca grava de volta na origem a menos que você o salve explicitamente.

## Etapa 1: Importar a biblioteca e criar opções de carregamento

A primeira coisa que você deve fazer é importar `aspose.words` e instanciar um objeto `LoadOptions`. Esse objeto contém todas as configurações que afetam como o arquivo é lido.

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*Por que isso importa:* `LoadOptions` é a porta de entrada para o ajuste fino do analisador. Sem ele, Aspose.Words usa o modo estrito padrão, que aborta ao encontrar qualquer erro estrutural.

## Etapa 2: Habilitar modo de recuperação

Defina a propriedade `recovery_mode` como `RecoveryMode.RECOVER`. Isso indica ao carregador que tente reparar automaticamente partes quebradas, como nós XML ausentes, relacionamentos danificados ou fluxos truncados.

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

Habilitar o modo de recuperação **não** garante um documento perfeito, mas aumenta drasticamente a chance de que você ainda consiga extrair texto, imagens ou tabelas.

## Etapa 3: Carregar o DOCX potencialmente corrompido com as opções configuradas

Agora use o construtor `Document` que aceita tanto o caminho do arquivo quanto a instância de `LoadOptions`.

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*Por que isso importa:* O bloco `try/except` demonstra **como abrir docx corrompido** com segurança. Sem o modo de recuperação, a mesma chamada levantaria uma exceção imediatamente, interrompendo seu programa.

## Etapa 4: Verificar o conteúdo recuperado (opcional, mas recomendado)

Após o carregamento, você deve verificar se o documento contém conteúdo significativo. Uma maneira rápida é extrair o texto simples e imprimir os primeiros caracteres.

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

Se a saída mostrar uma pré‑visualização razoável, você pode prosseguir com o processamento do documento (por exemplo, converter para PDF, extrair tabelas etc.). Se o texto estiver vazio, o arquivo pode estar além de reparo e você talvez precise solicitar uma nova cópia.

## Etapa 5: Salvar o documento reparado (se quiser uma cópia limpa)

Quando estiver satisfeito com o conteúdo recuperado, pode salvar um novo DOCX limpo. Esta etapa é opcional, mas costuma ser útil para fluxos de trabalho posteriores.

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Salvar cria um novo arquivo que não contém mais a corrupção que acionou o modo de recuperação.

## Casos limites e dicas adicionais

| Situação                                 | Abordagem recomendada |
|------------------------------------------|-----------------------|
| **O arquivo não é um DOCX** (ex.: `.doc`) | Use `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` antes de carregar. |
| **Recuperação parcial apenas**          | Após o carregamento, inspecione `document.get_text()` e `document.get_page_count()`. Se a contagem de páginas for 0, o documento pode ser irrecuperável. |
| **Documentos grandes**                  | Habilite `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE` para reduzir o uso de RAM durante a recuperação. |
| **Precisa registrar o que foi reparado** | Defina `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER` e então leia `document.get_last_save_options().recovery_log` (se disponível) para detalhes. |

> **Atenção:** O modo de recuperação pode descartar silenciosamente elementos não suportados (por exemplo, fontes ausentes). Se a fidelidade visual for crítica, compare o arquivo reparado com uma versão conhecida como boa.

## Exemplo completo em funcionamento

Juntando tudo, aqui está um script autocontido que você pode executar imediatamente:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

Executar o script imprime uma mensagem de sucesso, um pequeno trecho de texto e cria `repaired.docx` na mesma pasta.

## Conclusão

Agora você sabe como **habilitar o modo de recuperação** para **abrir documentos Word corrompidos**, **recuperar conteúdo de docx corrompido** e carregar o documento com segurança usando Aspose.Words para Python. As etapas principais — criar `LoadOptions`, ativar `RecoveryMode.RECOVER` e tratar exceções — formam um padrão confiável que pode ser reutilizado em qualquer pipeline de automação.

Em seguida, considere explorar tópicos relacionados, como **converter o documento recuperado para PDF**, **extrair tabelas com `DocumentVisitor`**, ou **processar em lote uma pasta de arquivos corrompidos**. Todos esses se baseiam na mesma fundação de modo de recuperação demonstrada aqui.

Feliz codificação, e que seus documentos permaneçam saudáveis!


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [how to recover docx – set recovery mode & open corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Recover corrupted DOCX with Aspose.Words LoadOptions – Complete C# Guide](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}