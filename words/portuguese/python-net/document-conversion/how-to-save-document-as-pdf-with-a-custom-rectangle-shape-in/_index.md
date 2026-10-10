---
category: general
date: 2026-10-07
description: Aprenda como salvar o documento como PDF enquanto adiciona uma forma
  retangular e sombra personalizada usando Aspose.Words para Python. Código passo
  a passo incluído.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: pt
lastmod: 2026-10-07
og_description: Salve o documento como PDF com uma forma retangular personalizada
  usando Aspose.Words para Python. Siga o exemplo completo para desenhar, estilizar
  e exportar o Word para PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Salvar documento como PDF com forma de retângulo – guia completo de Python
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Como salvar documento como PDF com uma forma retangular personalizada em Python
url: /pt/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como salvar documento como PDF com uma forma de retângulo personalizada em Python

Se você precisa **save document as PDF** enquanto adiciona gráficos personalizados, este guia mostra como fazer. Vamos percorrer a criação de um arquivo Word em branco, **drawing a rectangle shape**, definir seu tamanho, aplicar uma sombra visível e, finalmente, **export Word to PDF** usando a biblioteca Aspose.Words for Python.

Você terminará com um PDF que contém um retângulo perfeitamente posicionado, pronto para relatórios, faturas ou qualquer cenário de automação de documentos. Nenhuma ferramenta externa é necessária — apenas Python e o pacote Aspose.Words.

## O que você precisará

| Requisito | Por que é importante |
|-------------|----------------|
| Python 3.8+ | A API Aspose.Words for Python tem como alvo interpretadores modernos. |
| `aspose-words` package (`pip install aspose-words`) | Fornece o namespace `aw` usado nos exemplos de código. |
| Familiaridade básica com Python e programação orientada a objetos | O tutorial manipula objetos como `Document` e `Shape`. |
| Permissão de escrita para uma pasta onde o PDF será salvo | A etapa `save document as pdf` grava um arquivo no disco. |

> **Dica profissional:** Use um ambiente virtual (`python -m venv venv`) para manter as dependências isoladas.

## Como salvar documento como PDF com uma forma de retângulo

A seguir está um exemplo completo e executável. Cada passo é explicado para que você entenda **por que** realizamos a ação, não apenas **o que** o código faz.

### Etapa 1: Inicializar um novo documento em branco

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Criar um novo objeto `Document` fornece uma coleção de páginas limpa. Você também poderia carregar um *.docx* existente se quisesse **export Word to PDF** mais tarde, mas começar em branco mantém o exemplo focado.

### Etapa 2: Adicionar forma de retângulo ao documento

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

A etapa `add rectangle shape` usa `ShapeType.RECTANGLE`. Ao anexar a forma a um parágrafo, o Aspose.Words sabe onde renderizá‑la no PDF final.

### Etapa 3: Definir dimensões do retângulo

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Definir explicitamente as **rectangle dimensions** garante que a forma tenha aparência consistente em todas as plataformas. Você também pode usar os auxiliares `convert_to_inches` se preferir unidades imperiais.

### Etapa 4: (Opcional) Aplicar uma sombra personalizada visível

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Uma sombra faz o retângulo se destacar no PDF. O sinalizador `shadow.visible` é necessário; sem ele, as outras propriedades não têm efeito.

### Etapa 5: Salvar documento como PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Chamar `document.save` com a extensão **.pdf** automaticamente **save document as pdf** usando o renderizador PDF interno do Aspose.Words. Nenhuma etapa de conversão adicional é necessária, por isso esse método é a forma recomendada de **export Word to PDF**.

> **Por que isso funciona:** Aspose.Words grava o layout do documento, incluindo o retângulo e sua sombra, diretamente no fluxo PDF. O processo é sem perdas e mantém a qualidade vetorial.

## Código-fonte completo (script único)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Executar este script produz `shadow_rectangle.pdf` que se parece com isto:

![Diagrama do PDF gerado mostrando a forma de retângulo após save document as pdf](placeholder-image.png)

*O PDF contém uma única página com um retângulo com sombra preta centralizado no documento.*

## Perguntas comuns e casos de borda

| Pergunta | Resposta |
|----------|----------|
| **Posso posicionar o retângulo em um local específico?** | Sim. Defina `rectangle.left` e `rectangle.top` (em pontos) antes de salvar. |
| **E se eu precisar de várias formas?** | Crie objetos `Shape` adicionais, configure cada um e anexe‑os ao mesmo ou a diferentes parágrafos. |
| **A sombra afeta o tamanho do PDF?** | Apenas marginalmente; a sombra é armazenada como metadados vetoriais, não como imagem raster. |
| **Posso usar isso para converter arquivos *.docx* existentes?** | Absolutamente. Substitua `aw.Document()` por `aw.Document("input.docx")` e o restante das etapas permanece inalterado. |
| **Existe uma maneira de mudar a cor de preenchimento do retângulo?** | Defina `rectangle.fill_color = aw.drawing.Color.light_blue` (ou qualquer `Color` que preferir). |

## Próximos passos

Agora que você sabe como **save document as PDF** com um retângulo personalizado, você pode explorar:

* **Export Word to PDF** com cabeçalhos, rodapés e números de página.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) usando a mesma classe `Shape`.  
* **Batch process** uma pasta de arquivos Word, aplicando a mesma sobreposição de retângulo a cada um.  

Essas extensões seguem o mesmo padrão: criar uma forma, configurar suas propriedades e **save document as pdf**.

---

**Resumo:** Este tutorial mostrou como **save document as PDF** enquanto **add rectangle shape**, **set rectangle dimensions**, e aplicar uma sombra personalizada usando Aspose.Words for Python. O script completo está pronto para copiar, executar e adaptar aos seus próprios pipelines de automação de documentos. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma de retângulo, adicionar sombra e salvar PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Adicionar retângulo ao PDF com Aspose.Words – Guia passo a passo](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Salvar documento como PDF com Aspose.Words – Guia completo em C#](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}