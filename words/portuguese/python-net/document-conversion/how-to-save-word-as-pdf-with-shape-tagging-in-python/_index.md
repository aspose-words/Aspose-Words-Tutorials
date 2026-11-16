---
category: general
date: 2026-11-15
description: Salvar Word como PDF em Python usando Aspose.Words, aprenda como exportar
  formas e marcar formas flutuantes como inline para uma conversão precisa de docx
  para PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to pdf
- how to export shapes
- how to convert docx
- how to tag shapes
language: pt
lastmod: 2026-11-15
og_description: Salvar Word como PDF em Python usando Aspose.Words. Este guia mostra
  como exportar formas, marcar formas flutuantes como inline e converter docx para
  PDF de forma confiável.
og_image_alt: Screenshot of Python code that saves a Word document as PDF with shape
  tagging
og_title: Salvar Word como PDF com marcação de formas em Python – guia completo
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Save Word as PDF in Python using Aspose.Words, learn how to export
    shapes and tag floating shapes as inline for accurate docx to PDF conversion.
  headline: How to save Word as PDF with shape tagging in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
title: Como salvar Word como PDF com marcação de formas em Python
url: /pt/python/document-conversion/how-to-save-word-as-pdf-with-shape-tagging-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como salvar Word como PDF com marcação de formas em Python

Se você precisa **salvar Word como PDF** e manter cada desenho exatamente onde ele pertence, este guia mostra uma maneira confiável de fazer isso com Aspose.Words for Python. Você também aprenderá **como exportar formas** e **como marcar formas** para que objetos flutuantes se tornem elementos inline durante a conversão.

Neste tutorial abordamos:

* Converter um arquivo DOCX para PDF (`convert docx to pdf`)  
* Exportar formas flutuantes como tags inline (`how to export shapes`)  
* Marcar formas durante a operação de salvamento em PDF (`how to tag shapes`)  

Nenhuma ferramenta externa é necessária—apenas algumas linhas de código Python.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.8+ instalado  
* Uma licença ativa do Aspose.Words for Python (ou um teste gratuito)  
* O pacote `aspose-words` instalado (`pip install aspose-words`)  
* Um arquivo DOCX (`input.docx`) que contém formas flutuantes (imagens, caixas de texto, etc.)

## Etapa 1: Instalar e importar Aspose.Words

Primeiro, adicione a biblioteca ao seu ambiente e importe-a no seu script.

```python
# Install the package (run once):
# pip install aspose-words

import aspose.words as aw
```

*Por quê?* O módulo `aspose.words` fornece a classe `Document` e `PdfSaveOptions` que precisamos para controlar o tratamento de formas.

## Etapa 2: Carregar o documento Word

Use o construtor `Document` para ler o arquivo de origem.

```python
# Load the Word document you want to convert
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

Se o arquivo não existir, Aspose.Words gera um `FileNotFoundError`. Envolva a chamada em um bloco `try/except` para código de produção.

## Etapa 3: Configurar opções de salvamento PDF – exportar e marcar formas

A chave para uma conversão limpa é o objeto `PdfSaveOptions`. Definir `export_floating_shapes_as_inline_tag` como `True` indica ao mecanismo que trate desenhos flutuantes como elementos inline, o que elimina deslocamentos de layout no PDF resultante.

```python
# Create PDF save options and enable inline tagging for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes
```

*Por quê?* Quando `export_floating_shapes_as_inline_tag` está `False` (o padrão), as formas flutuantes mantêm seus metadados de posição originais, o que pode fazer com que apareçam fora do lugar no PDF. Habilitar a tag inline força o Aspose.Words a incorporar uma pequena tag XML que o renderizador de PDF interpreta como um objeto inline, preservando a fidelidade visual.

## Etapa 4: Salvar o documento como PDF

Agora escreva o arquivo PDF usando as opções configuradas.

```python
# Save the document as a PDF, applying the shape‑tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)

print(f"PDF saved to {output_path}")
```

Após a execução, `output.pdf` contém o layout original do Word com todas as formas flutuantes renderizadas corretamente como elementos inline.

## Etapa 5: Verificar a conversão (opcional)

Você pode verificar programaticamente que o PDF foi criado e contém ao menos uma página:

```python
import os
from aspose.pdf import Document as PdfDocument

if os.path.exists(output_path):
    pdf_doc = PdfDocument(output_path)
    print(f"PDF has {pdf_doc.pages.count} page(s).")
else:
    raise FileNotFoundError("PDF was not created.")
```

*Dica:* Use um visualizador de PDF para verificar se imagens, caixas de texto e chamadas aparecem exatamente onde estavam no arquivo DOCX.

## Variações comuns e casos extremos

| Situação | O que mudar |
|-----------|----------------|
| **Você precisa manter as formas flutuantes flutuando** | Defina `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **Converter muitos arquivos em lote** | Itere sobre uma lista de caminhos de arquivos e reutilize uma única instância de `PdfSaveOptions`. |
| **Você quer incorporar uma senha** | Use `pdf_opts.encrypt_options.password = "your‑password"` antes de chamar `save`. |
| **Documentos grandes causam pressão de memória** | Habilite `pdf_opts.memory_optimization = True` para reduzir o uso de RAM. |

## Dica profissional: lidar com fontes ausentes

Se o DOCX de origem usar fontes que não estão instaladas no servidor, a renderização do PDF pode recorrer a uma fonte padrão. Registre as fontes ausentes com `FontSettings`:

```python
font_settings = aw.FontSettings()
font_settings.set_fonts_folder("YOUR_DIRECTORY/fonts", recursive=True)
doc.font_settings = font_settings
```

Isso garante que o PDF tenha a mesma aparência do arquivo Word original.

## Exemplo completo executável

```python
import aspose.words as aw
import os

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Saves a Word document as PDF while tagging floating shapes as inline.
    """
    # Load the DOCX
    doc = aw.Document(input_path)

    # Optional: register custom fonts
    # font_settings = aw.FontSettings()
    # font_settings.set_fonts_folder("fonts", recursive=True)
    # doc.font_settings = font_settings

    # Configure PDF options to export shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes

    # Save as PDF
    doc.save(output_path, pdf_opts)
    print(f"PDF saved to {output_path}")

if __name__ == "__main__":
    INPUT = "YOUR_DIRECTORY/input.docx"
    OUTPUT = "YOUR_DIRECTORY/output.pdf"

    if not os.path.isfile(INPUT):
        raise FileNotFoundError(f"Input file not found: {INPUT}")

    convert_docx_to_pdf(INPUT, OUTPUT)

    # Verify creation
    if os.path.isfile(OUTPUT):
        from aspose.pdf import Document as PdfDocument
        pdf = PdfDocument(OUTPUT)
        print(f"Conversion successful – PDF has {pdf.pages.count} page(s).")
    else:
        raise RuntimeError("PDF conversion failed.")
```

Executar o script produz `output.pdf` com todas as formas flutuantes corretamente marcadas, proporcionando um resultado limpo de **save word as pdf**.

## Conclusão

Agora você sabe como **salvar Word como PDF** em Python enquanto controla o tratamento de formas. Configurando `PdfSaveOptions.export_floating_shapes_as_inline_tag`, você pode de forma confiável **converter docx para pdf**, **exportar formas** como tags inline e responder **como marcar formas** durante a conversão.  

A partir daqui você pode explorar:

* Adicionar marcas d'água (`pdf_opts.add_watermark`) – uma extensão natural da personalização de PDF.  
* Converter outros formatos (HTML, EPUB) usando o mesmo padrão `save`.  
* Automatizar conversões em lote para grandes repositórios de documentos.

Execute o script, experimente as configurações opcionais e integre-o ao seu pipeline de processamento de documentos hoje. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Salvar Word como PDF – Converter Formas para Inline com Aspose.Words](/words/english/python-net/document-conversion/save-word-as-pdf-convert-shapes-to-inline-with-aspose-words/)
- [Como salvar Word como PDF com Aspose.Words para Python](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-with-aspose-words-for-python/)
- [Como converter DOCX para PDF em Python usando Aspose.Words](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}