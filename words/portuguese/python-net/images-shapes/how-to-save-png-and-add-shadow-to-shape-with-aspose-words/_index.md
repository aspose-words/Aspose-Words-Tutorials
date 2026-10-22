---
category: general
date: 2026-08-17
description: Como salvar PNG usando Aspose.Words para Python. Aprenda a adicionar
  sombra a uma forma, salvar o documento como PDF e exportar Word para PNG em um único
  guia.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: pt
lastmod: 2026-08-17
og_description: Como salvar PNG com Aspose.Words. Este tutorial mostra como adicionar
  uma sombra a uma forma, salvar o documento como PDF e exportar Word para PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Como salvar PNG e adicionar sombra a forma com Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Como salvar PNG e adicionar sombra a uma forma com Aspose.Words
url: /pt/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como salvar PNG e adicionar sombra a forma com Aspose.Words

Se você precisa de **como salvar PNG** a partir de um arquivo Word, este guia fornece uma solução completa e executável. Você também verá como **adicionar sombra a forma**, **salvar documento como PDF** e **exportar Word para PNG** sem sair do ambiente Aspose.Words.

O tutorial cobre tudo o que é necessário para transformar um documento Word em branco em um PDF e uma imagem PNG, aplicando um efeito de sombra simples a uma forma retangular. Nenhuma ferramenta externa é necessária, e o código funciona com Aspose.Words for Python via .NET 7 ou posterior.

## O que você irá realizar

* Criar um novo documento Word programaticamente.  
* Inserir uma forma retangular e configurar um efeito de sombra.  
* Salvar o mesmo documento como um arquivo PDF.  
* Exportar o documento como uma imagem PNG.  

Essas etapas respondem à consulta comum **como salvar PNG** enquanto também tratam **adicionar sombra a forma** e **salvar documento como PDF** em um único fluxo de trabalho.

## Pré-requisitos

* Python 3.9 ou superior.  
* Aspose.Words for Python via .NET instalado (`pip install aspose-words`).  
* Permissão de escrita no diretório de saída que você especificar.  

Se você ainda não instalou o Aspose.Words, execute:

```bash
pip install aspose-words
```

## Como salvar PNG com Aspose.Words

O primeiro passo importante é criar um documento e um `DocumentBuilder`. O builder fornece uma API fluente para inserir conteúdo como formas, tabelas ou texto.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` representa todo o arquivo Word na memória. `aw.DocumentBuilder` aponta para a localização atual de inserção, que inicialmente é o início da primeira (e única) seção.

## Adicionar sombra à forma antes da exportação

Uma forma pode ser qualquer objeto de desenho—retângulo, elipse ou polígono personalizado. Aqui criamos um retângulo de 100 × 100 points e aplicamos uma sombra suave.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Por que configurar a sombra antes de salvar? Aspose.Words renderiza a sombra durante as fases de exportação para PDF e PNG, de modo que o efeito visual é preservado em ambos os formatos de saída.

### Dica profissional
Se precisar de uma sombra mais nítida, reduza `blur`. Para um deslocamento mais pronunciado, aumente `distance`. A classe `Shadow` também expõe `angle` e `transparency` para controle fino.

## Salvar documento como PDF

Salvar um documento Word como PDF é uma linha de código assim que o conteúdo está pronto. A constante `SaveFormat.PDF` indica ao Aspose.Words que ele deve realizar a conversão.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

O PDF resultante contém o retângulo com a sombra exata que você definiu. Aspose.Words lida com gráficos vetoriais, portanto o tamanho do PDF permanece modesto.

## Exportar Word para PNG

Exportar para PNG cria uma imagem raster de cada página. Por padrão, Aspose.Words usa 96 DPI; você pode aumentar esse valor para saída de alta resolução fornecendo um objeto `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Quando você **exporta Word para PNG**, cada página é salva como um arquivo PNG separado. Como nosso documento de exemplo tem apenas uma página, aparece apenas um único arquivo PNG.

### Opcional: PNG de alta resolução

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Um DPI maior é útil quando o PNG será usado em impressão ou quando você precisa de uma miniatura nítida.

## Script completo – copie, cole e execute

Abaixo está o script completo e autocontido que implementa cada passo descrito acima. Salve-o como `generate_assets.py` e execute-o a partir da linha de comando.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Saída esperada

Executar o script cria três arquivos:

* `output/output.pdf` – um PDF com um retângulo que projeta uma sombra preta.  
* `output/output.png` – um PNG de 96 DPI renderizando a mesma página.  
* `output/high_res_output.png` – um PNG de 300 DPI para maior qualidade.

Abra qualquer um dos arquivos no visualizador de sua preferência para verificar se a sombra aparece exatamente como definida.

## Perguntas comuns e casos de borda

**E se o diretório de saída não existir?**  
O script chama `os.makedirs(output_dir, exist_ok=True)`, que cria a pasta automaticamente. Isso evita um `FileNotFoundError` durante as operações de salvamento.

**Posso adicionar várias formas com sombras diferentes?**  
Sim. Crie objetos `Shape` adicionais, configure cada propriedade `shadow` de forma independente e insira‑os com `builder.insert_node(shape)` antes de salvar.

**A sombra será preservada ao converter para outros formatos raster (por exemplo, JPEG)?**  
Aspose.Words renderiza a sombra para todos os formatos raster suportados por `SaveFormat`. Você pode substituir `aw.SaveFormat.PNG` por `aw.SaveFormat.JPEG` e a sombra ainda aparecerá.

**Como isso difere de “converter word para pdf”?**  
`convert word to pdf` é essencialmente a mesma operação realizada na etapa 4. A mesma chamada `doc.save` com `SaveFormat.PDF` lida com a conversão internamente, preservando layout, fontes e gráficos como sombras.

**Existe um limite para o tamanho da forma?**  
Formas são medidas em points (1 pt ≈ 1/72 polegada). Dimensões muito grandes podem aumentar o tamanho do arquivo resultante, mas o Aspose.Words não impõe um limite rígido. Ajuste os argumentos `width` e `height` ao construir `aw.Shape` conforme sua necessidade de layout.

## Conclusão

Agora você sabe **como salvar PNG** a partir de um documento Word enquanto aprende a **adicionar sombra a forma**, **salvar documento como PDF** e **exportar Word para PNG** usando Aspose.Words for Python. O script completo demonstra um padrão limpo e repetível que pode ser adaptado para documentos maiores, múltiplas páginas ou efeitos gráficos mais complexos.

Próximos passos podem incluir:

* Experimentar outros valores de `ShapeType` (elipse, nuvem, etc.).  
* Using `

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}