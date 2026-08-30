---
category: general
date: 2026-08-07
description: Desenhe um retângulo em PDF usando Aspose.Words para Python e aprenda
  como adicionar sombra à forma, configurar a sombra da forma e salvar o documento
  como PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: pt
lastmod: 2026-08-07
og_description: Desenhe retângulo em PDF com Aspose.Words para Python. Este tutorial
  mostra como adicionar sombra a uma forma, configurar a sombra da forma e salvar
  o documento como PDF para geração profissional de documentos.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Desenhar retângulo em PDF com Aspose.Words para Python – guia
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Desenhar retângulo em PDF com Aspose.Words para Python
url: /pt/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Desenhar retângulo em PDF com Aspose.Words para Python

Se você precisa **desenhar retângulo em PDF** enquanto trabalha em Python, este guia fornece uma solução completa, pronta‑para‑executar. Você verá exatamente como **adicionar sombra à forma**, configurar essa sombra e, finalmente, **salvar o documento como PDF** para distribuição ou arquivamento.

Criar um retângulo sombreado é uma necessidade comum para relatórios, faturas ou anotações visuais. Ao final deste tutorial, você terá um único script que produz um PDF contendo um retângulo com sombra realista, e entenderá como ajustar tamanho, cor e deslocamento para se adequar a qualquer design.

## Pré-requisitos

* Python 3.8+ instalado.
* O pacote Aspose.Words for Python via .NET (`aspose-words`) – instale com:

```bash
pip install aspose-words
```

* Permissão de gravação na pasta onde você pretende salvar o PDF.

Nenhuma biblioteca adicional é necessária; Aspose.Words lida com a criação de formas, configuração de sombra e exportação para PDF internamente.

## Etapa 1: Criar um novo documento em branco (desenhar retângulo em PDF – inicializar)

O primeiro passo é instanciar um objeto `Document`. Esse objeto representa todo o arquivo PDF e fornece um contêiner para seções, parágrafos e formas.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Por que isso importa:** Aspose.Words trata a geração de PDF como uma conversão a partir de um modelo de documento Word, portanto começamos com um `Document` embora o resultado final seja um PDF.

## Etapa 2: Inserir uma forma de retângulo no corpo do documento

Um retângulo é um `ShapeType` específico. Nós o adicionamos ao corpo da primeira seção, o que cria automaticamente uma nova página ao ser salvo como PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Explicação:** As propriedades `width` e `height` controlam o tamanho visual da forma no PDF. Adicionar texto facilita a verificação do retângulo durante os testes.

## Etapa 3: Adicionar sombra à forma – habilitar e personalizar

Agora ativamos o efeito de sombra e ajustamos finamente sua aparência. É aqui que a palavra‑chave **add shadow to shape** entra em ação.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Por que configurar a sombra da forma?** Ajustar `blur`, `distance` e `angle` permite simular iluminação realista, o que melhora a legibilidade e a hierarquia visual nos PDFs gerados.

## Etapa 4: Salvar documento como PDF – saída final

Com o retângulo e sua sombra definidos, o último passo é exportar o documento Word para PDF. Isso atende ao requisito de **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Ao abrir `shadow_rectangle.pdf`, você verá uma única página contendo um retângulo com borda cinza intitulado “Shadow demo” com uma sombra diagonal nítida.

### Saída esperada

* Um arquivo PDF chamado `shadow_rectangle.pdf`.
* Uma página com um retângulo de 200 pt × 100 pt.
* Uma sombra visível deslocada 5 pt em um ângulo de 45°, desfocada em 8 pt.

## Etapa 5: Explorar variações e casos limites (opcional)

Abaixo estão ajustes comuns que você pode precisar em projetos reais:

| Variação | Code snippet | Quando usar |
|-----------|--------------|-------------|
| **Tipo de forma diferente** (por exemplo, elipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Para gráficos arredondados ou emblemas |
| **Cor de sombra personalizada** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Quando uma sombra cinza ou específica da marca for necessária |
| **Múltiplas formas** | Repeat the shape‑creation block and adjust `left`/`top` properties | Para construir diagramas complexos |
| **Sem texto dentro da forma** | Omit `rectangle.text = "..."` | Quando a forma for puramente decorativa |
| **Saída com DPI mais alto** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Para PDFs prontos para impressão |

**Dica profissional:** Sempre defina `shadow.visible = True` antes de ajustar outras propriedades; caso contrário, as alterações são ignoradas silenciosamente.

## Script completo – copie, cole e execute

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Execute o script a partir do seu terminal ou IDE. Substitua `YOUR_DIRECTORY` por um caminho de pasta real, como `"/tmp"` ou `"C:\\Users\\Me\\Documents"`.

## Conclusão

Agora você sabe como **desenhar retângulo em PDF** usando Aspose.Words para Python, **adicionar sombra à forma**, **configurar a sombra da forma** e **salvar o documento como PDF**. O exemplo completo demonstra cada passo, desde a criação do documento até a exportação final, e as variações opcionais mostram como adaptar o código para cenários mais complexos.

Em seguida, você pode explorar:

* Adicionar outros tipos de forma (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Aplicar preenchimentos em gradiente ou bordas para melhorar o apelo visual.
* Usar `PdfSaveOptions` para incorporar fontes ou controlar a compressão de imagens.

Sinta-se à vontade para experimentar os parâmetros para adequá‑los à sua identidade visual ou diretrizes de design. Feliz script de PDF!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Otimizar marcadores PDF usando Aspose.Words para Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Otimizar carregamento de PDF em Python com Aspose Words – pular imagens](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Manipulação de PDF com Aspose Words Python](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}