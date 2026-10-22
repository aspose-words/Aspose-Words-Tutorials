---
category: general
date: 2026-08-17
description: Salve o documento como imagem e exporte todas as páginas em PNG usando
  Aspose.Words para Python. Aprenda a converter DOCX para PNG com um único comando.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as image
- convert docx to png
- export docx to png
- export all pages png
- export word pages image
language: pt
lastmod: 2026-08-17
og_description: Salve o documento como imagem e exporte todas as páginas em PNG com
  Aspose.Words para Python. Este guia mostra como converter DOCX para PNG de forma
  eficiente.
og_image_alt: Diagram showing a multi‑page Word document converted into a single PNG
  grid preview
og_title: Salvar documento como imagem e converter DOCX para PNG em Python
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  headline: 'Save document as image: convert DOCX to PNG in Python'
  type: TechArticle
- description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  name: 'Save document as image: convert DOCX to PNG in Python'
  steps:
  - name: '**Save format** – PNG is lossless and widely supported.'
    text: '**Save format** – PNG is lossless and widely supported.'
  - name: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
    text: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
  - name: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
    text: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
  type: HowTo
tags:
- Aspose.Words
- Python
- DOCX
title: 'Salvar documento como imagem: converter DOCX para PNG em Python'
url: /pt/python/document-conversion/save-document-as-image-convert-docx-to-png-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar documento como imagem: converter DOCX para PNG em Python

Se você precisa **salvar documento como imagem** e gerar uma visualização única para um arquivo Word de várias páginas, este guia mostra como fazer isso com Aspose.Words para Python. Você também aprenderá a **converter DOCX para PNG** em uma única operação simples.

Exportar cada página de um documento Word para PNG pode ser trabalhoso quando você escreve um loop manualmente. Aspose.Words oferece opções integradas que permitem **exportar todas as páginas PNG** com uma única chamada, ao mesmo tempo em que dão controle sobre layout, resolução e intervalo de páginas. Ao final deste tutorial você terá um script pronto‑para‑executar que produz um PNG em estilo grade contendo todas as páginas do documento de origem.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.8 ou mais recente instalado.
* O pacote `aspose-words` (`pip install aspose-words`).
* Um arquivo Word (`.docx`) que contenha pelo menos duas páginas.
* Permissão de escrita no diretório onde você deseja armazenar o PNG resultante.

Nenhuma ferramenta externa adicional é necessária; Aspose.Words lida com a conversão totalmente na memória.

## Etapa 1: Carregar o documento Word

A primeira etapa é criar um objeto `aw.Document` que representa o arquivo DOCX de origem. Esse objeto fornece acesso a todas as páginas, seções e recursos dentro do documento.

```python
import aspose.words as aw

# Load the multi‑page Word document
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)
```

*Por que isso importa*: Carregar o documento uma única vez fornece um modelo de objeto completo que o Aspose.Words pode renderizar posteriormente para qualquer formato de imagem suportado. A classe `aw.Document` também valida o arquivo, oferecendo feedback imediato caso o DOCX esteja corrompido.

## Etapa 2: Criar opções de salvamento PNG e configurá‑las

Aspose.Words usa `ImageSaveOptions` para controlar como um documento é rasterizado. Nesta etapa definimos três propriedades importantes:

1. **Formato de salvamento** – PNG é sem perdas e amplamente suportado.
2. **Conjunto de páginas** – define o intervalo de páginas a exportar; usar `0, document.page_count` captura todas as páginas.
3. **Layout** – `GRID` organiza todas as páginas exportadas em uma única imagem, ideal para cenários de pré‑visualização.

```python
# Configure PNG export options
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export all pages (page index starts at 0)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid layout (rows × columns are auto‑calculated)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: increase resolution for sharper output (default is 96 DPI)
png_options.resolution = 150  # DPI
```

*Por que isso importa*: Definir `page_set` para o intervalo completo permite **exportar docx para png** sem iterar manualmente sobre as páginas. O layout `GRID` produz uma única imagem que contém todas as páginas lado a lado, atendendo ao requisito de **exportar páginas do Word como imagem** de forma compacta. Ajustar `resolution` ajuda quando o documento de origem contém detalhes finos.

## Etapa 3: Salvar o documento como uma pré‑visualização PNG única

Com as opções preparadas, a gravação é feita em uma única linha. Aspose.Words grava o arquivo PNG no disco usando as configurações definidas acima.

```python
# Destination path for the combined PNG image
output_path = "YOUR_DIRECTORY/preview.png"

# Perform the export – this creates one PNG that contains all pages
document.save(output_path, png_options)
print(f"Document successfully saved as image: {output_path}")
```

**Saída esperada**

Ao executar o script, ele cria `preview.png`. Se o DOCX de origem tinha três páginas, o PNG mostrará essas três páginas dispostas em uma grade (por exemplo, 2 × 2 com a última célula vazia). Abrir o arquivo em qualquer visualizador de imagens confirma que cada página foi rasterizada corretamente.

### Dica profissional

Se você precisar apenas de um subconjunto de páginas, altere os argumentos de `PageSet`, por exemplo:

```python
# Export pages 2‑4 only (zero‑based index)
png_options.page_set = aw.saving.PageSet(1, 4)
```

Isso ainda respeita a lógica de **exportar todas as páginas png** para o intervalo selecionado, reduzindo o uso de memória em documentos muito grandes.

## Lidando com documentos grandes e restrições de memória

Ao trabalhar com documentos que têm dezenas ou centenas de páginas, o PNG gerado pode ficar grande. Considere estas estratégias:

* **Aumente `resolution` somente quando necessário** – DPI mais alto gera arquivos maiores.
* **Use `PageLayout.SINGLE_COLUMN`** – cria uma faixa vertical em vez de uma grade, facilitando a rolagem.
* **Transmita a saída** – Aspose.Words também suporta salvar em um stream `BytesIO` caso você precise enviar a imagem pela rede sem gravá‑la no disco.

```python
import io

stream = io.BytesIO()
document.save(stream, png_options)
# Now `stream.getvalue()` holds the PNG bytes
```

## Script completo para copiar‑colar rapidamente

Abaixo está o exemplo completo e executável que incorpora todas as etapas discutidas. Substitua `YOUR_DIRECTORY` pelo caminho real da pasta em sua máquina.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# 1. Load the source DOCX file
# ----------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)

# ----------------------------------------------------------------------
# 2. Configure PNG export options (save document as image)
# ----------------------------------------------------------------------
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export every page (export docx to png)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid (export word pages image)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: higher DPI for sharper output
png_options.resolution = 150

# ----------------------------------------------------------------------
# 3. Save the combined PNG file
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/preview.png"
document.save(output_path, png_options)

print(f"Document successfully saved as image: {output_path}")
```

Executar este script produz um PNG único que contém todas as páginas de `multi_page.docx`. A abordagem funciona com qualquer arquivo DOCX, independentemente da complexidade do conteúdo (tabelas, imagens, layouts complexos).

## Conclusão

Agora você sabe como **salvar documento como imagem**, **converter DOCX para PNG** e **exportar todas as páginas PNG** usando Aspose.Words para Python. Ao aproveitar `ImageSaveOptions` você evita loops manuais, obtém uma pré‑visualização em estilo grade e mantém controle sobre resolução e layout.  

A seguir, você pode explorar:

* Exportar para outros formatos raster (JPEG, BMP) – basta mudar `SaveFormat`.
* Adicionar marcas d'água ou anotações antes da exportação – manipule o objeto `Document`.
* Integrar este script a um serviço web para gerar pré‑visualizações sob demanda.

Experimente diferentes valores de `layout` e `resolution` para encontrar o equilíbrio que melhor se adapta aos requisitos de desempenho e qualidade da sua aplicação. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais abaixo abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Optimize RTF Image Handling in Python using Aspose.Words API: Save as WMF and Ensure Compatibility](/words/english/python-net/images-shapes/optimize-rtf-image-handling-aspose-words-python/)
- [Convert DOCX to Fixed-Form XAML in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/python-docx-to-xaml-aspose-tutorial/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}