---
category: general
date: 2026-10-16
description: Crie um documento Word em branco, insira uma forma no Word, adicione
  sombra externa e salve como PDF usando Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: pt
lastmod: 2026-10-16
og_description: Crie um documento Word em branco com uma forma de sombra externa usando
  Aspose.Words para Python. Este guia mostra como inserir a forma, aplicar a sombra
  e salvar o arquivo como PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Crie um documento Word em branco com sombra de forma – Guia Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Criar documento Word em branco com forma sombreada em Python
url: /pt/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco com forma sombreada em Python

Se você precisa **criar um documento Word em branco** e adicionar um gráfico personalizado, este guia cobre tudo. Vamos percorrer como **inserir forma no Word**, aplicar uma **sombra externa à forma**, e finalmente **salvar como PDF usando Python**.

Você aprenderá a configurar o Aspose.Words para Python, construir um retângulo, estilizar sua sombra e gerar um PDF que preserva o efeito visual. Não é necessário ter experiência prévia com a API Aspose, mas é preciso ter conhecimentos básicos de Python e uma instalação funcional do Python 3.10 ou superior.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.10 ou mais recente instalado.
* Uma licença ativa do Aspose.Words para Python (uma avaliação gratuita funciona para testes).
* Acesso ao `pip` para instalar o pacote `aspose-words`.
* Permissão de escrita no diretório onde o PDF será salvo.

Você pode instalar a biblioteca com um único comando:

```bash
pip install aspose-words
```

## Criar documento Word em branco – configuração do ambiente

O primeiro passo é criar um arquivo Word vazio que servirá como tela para a forma.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` representa um arquivo Word completamente em branco. Ao usar `DocumentBuilder` você obtém acesso a métodos como `insert_shape`, que usaremos no próximo passo.

## Inserir forma no Word e definir dimensões

Agora adicionamos um retângulo que receberá uma sombra externa. O tamanho é expresso em pontos (1 pt ≈ 1/72 polegada).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

A chamada `insert_shape` retorna um objeto `Shape` que pode ser customizado ainda mais. Neste ponto o documento já contém um retângulo visível quando aberto no Microsoft Word.

## Adicionar sombra externa – personalizando o efeito

Aspose.Words fornece a classe `ShadowEffect` para definir propriedades da sombra, como estilo, desfoque, distância e cor.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Definir `style` como `OUTER` garante que a sombra apareça fora da borda do retângulo, proporcionando um sutil aspecto 3‑D. Você pode experimentar com `blur` e `distance` para obter uma sombra mais apertada ou mais difusa.

## Salvar como PDF python – finalizando o documento

Depois de estilizar a forma, o documento pode ser salvo diretamente como PDF. O Aspose.Words cuida da conversão internamente, preservando o efeito de sombra.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Ao abrir `shape_with_shadow.pdf` em qualquer visualizador de PDF, você verá o retângulo com a sombra externa exatamente como apareceu no Word.

## Exemplo completo funcional

Abaixo está o script completo que combina todas as etapas. Copie‑o para um arquivo chamado `create_word_with_shadow.py` e execute‑o.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Saída esperada**

Executar o script imprime uma linha de confirmação, por exemplo:

```
PDF generated at: output/shape_with_shadow.pdf
```

Abrir o PDF resultante mostra uma única página contendo um retângulo de 200 pt × 100 pt com uma sombra externa preta suave.

## Variações comuns e casos de borda

* **Alterar a cor da sombra** – Substitua `aw.Color.black` por qualquer outro valor `aw.Color`, como `aw.Color.red` ou `aw.Color.from_argb(255, 0, 120, 215)`.
* **Usar uma forma diferente** – Troque `aw.drawing.ShapeType.RECTANGLE` por `OVAL`, `DIAMOND` ou qualquer outro valor enum suportado.
* **Salvar como DOCX em vez de PDF** – Chame `doc.save("output/shape.docx")` para manter o formato Word.
* **Múltiplas formas** – Crie formas adicionais chamando `builder.insert_shape` novamente; cada forma pode ter seu próprio `ShadowEffect`.

**Dica profissional:** Se precisar posicionar a forma em um local específico, defina `rectangle.left` e `rectangle.top` após a inserção. Isso oferece controle pixel‑perfect sobre o posicionamento.

## Conclusão

Agora você sabe como **criar documento Word em branco**, **inserir forma no Word**, **adicionar sombra externa à forma** e **salvar como PDF usando Python**. O exemplo de código completo demonstra o fluxo de trabalho de ponta a ponta, e as explicações esclarecem por que cada chamada de API é necessária.

A partir daqui, você pode explorar opções de estilo mais avançadas, adicionar texto dentro da forma ou combinar várias formas para construir diagramas complexos. Experimente diferentes parâmetros de sombra para combinar com a linguagem visual da sua marca e integre esta abordagem em pipelines maiores de geração de documentos.

Happy coding!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}