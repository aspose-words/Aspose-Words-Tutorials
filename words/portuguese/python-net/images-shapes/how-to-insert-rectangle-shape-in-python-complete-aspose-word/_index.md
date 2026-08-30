---
category: general
date: 2026-06-27
description: Aprenda como inserir uma forma retangular em Python usando Aspose.Words,
  alterar a cor da sombra, adicionar sombra externa e aplicar efeito de sombra à forma
  — tudo em um único tutorial.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: pt
og_description: Domine como inserir forma retangular em Python, alterar a cor da sombra,
  adicionar uma sombra externa e aplicar um efeito de sombra à forma com Aspose.Words.
og_title: Como Inserir Forma Retangular no Python – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Como Inserir Forma de Retângulo em Python – Guia Completo do Aspose.Words
url: /pt/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Inserir Forma Retangular em Python – Guia Completo do Aspose.Words

Já se perguntou **how to insert rectangle shape** em um documento Word usando Python? Você não está sozinho — muitos desenvolvedores encontram esse obstáculo ao automatizar relatórios ou criar modelos. A boa notícia é que o Aspose.Words torna tudo muito simples, e neste tutorial vamos percorrer todo o processo, desde desenhar o retângulo até aplicar uma sombra externa elegante.

Também vamos abordar **how to change shadow color**, **how to add outer shadow** e a etapa final de **apply shadow effect to shape**. Ao final, você terá um retângulo totalmente estilizado que pode inserir em qualquer arquivo .docx programaticamente.

## Pré‑requisitos

- Python 3.8+ instalado na sua máquina  
- Aspose.Words for Python via `pip install aspose-words`  
- Familiaridade básica com scripts Python (não é necessário conhecimento profundo da API do Word)  

Se você já tem tudo isso, ótimo — vamos começar. Caso contrário, instale a biblioteca primeiro; o restante do guia assume que a importação funciona sem problemas.

## Como Inserir Forma Retangular com Aspose.Words for Python

O primeiro passo é exatamente o que a palavra‑chave principal promete: **how to insert rectangle shape**. Criaremos um novo documento, instanciamos um `DocumentBuilder` e inserimos um retângulo na página.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Por que isso importa:** A chamada `insert_shape` é o núcleo de *how to insert rectangle shape*. Ela devolve um objeto `Shape` que você pode manipular depois — tamanho, posição, preenchimento, bordas, o que precisar. Observe que também definimos um `fill_color`; sem ele a sombra pode se misturar a uma página branca, dificultando a visualização.

### Dica profissional
Se precisar posicionar o retângulo em um local específico, use `builder.move_to` antes de inserir, ou ajuste `rectangle.left` e `rectangle.top` após a criação.

## Alterando a Cor da Sombra de uma Forma

Agora que o retângulo está no documento, vamos responder **how to change shadow color**. O Aspose.Words expõe um objeto `ShadowEffect` onde você pode definir a propriedade `color` para qualquer valor RGB.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Por que você pode querer isso:** Uma sombra preta muito escura pode ficar agressiva, especialmente em documentos de cores claras. Ajustar a cor permite combinar com a identidade visual da empresa ou simplesmente obter um efeito visual mais suave.

### Caso de borda
Se esquecer de definir `shadow.opacity`, o padrão será totalmente opaco, o que pode fazer a sombra parecer uma forma sólida. Sempre combine a mudança de cor com um nível de opacidade adequado.

## Adicionando um Efeito de Sombra Externa

A próxima pergunta que muitos fazem é **how to add outer shadow**. A flag `ShadowStyle.OUTER` indica ao Aspose.Words que a sombra deve ser renderizada fora do contorno da forma, e não dentro dele.

O trecho de código acima já usa `ShadowStyle.OUTER`, mas vamos isolar essa configuração para maior clareza:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Se você trocar para `ShadowStyle.INNER`, a sombra aparecerá *dentro* do retângulo, o que é útil para efeitos de embossing. Para a maioria dos cenários de design de documentos, o estilo externo oferece um aspecto natural de sombra projetada.

## Aplicando o Efeito de Sombra à Sua Forma

Já usamos **apply shadow effect to shape** ao atribuir `rectangle.shadow = shadow`. Vamos reunir tudo e salvar o documento, confirmando que o efeito persiste.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Ao abrir `RectangleWithShadow.docx` no Microsoft Word, você deverá ver um retângulo azul‑claro com uma sutil sombra cinza externa projetada em um ângulo de 45°. A sombra será levemente desfocada e deslocada, exatamente como configuramos.

### Armadilhas comuns
- **Diretório ausente:** `doc.save` lançará um erro se a pasta não existir. Crie-a antes ou use `os.makedirs`.
- **Incompatibilidade de versão:** A API de sombra requer Aspose.Words 22.9+; versões mais antigas ignoram silenciosamente as configurações de sombra.

## Exemplo Completo Funcional

Abaixo está o script completo, pronto para execução, que combina todas as etapas. Copie‑e‑cole em um arquivo chamado `rectangle_shadow.py` e execute com `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Saída esperada:** Um documento Word (`RectangleWithShadow.docx`) contendo um único retângulo com uma sombra externa cinza. Abra‑o no Word para verificar o efeito visual.

## Perguntas Frequentes

| Pergunta | Resposta |
|----------|----------|
| *Posso usar um tipo de forma diferente?* | Claro — substitua `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.TRIANGLE` etc., e a mesma lógica de sombra se aplica. |
| *E se eu precisar de uma borda mais espessa?* | Defina `rectangle.line_width = 2.0` (points) antes de aplicar a sombra. |
| *É possível animar a sombra?* | Não diretamente com Aspose.Words; seria necessário exportar para HTML/CSS para animação. |
| *Isso funciona no macOS?* | Sim — o Aspose.Words é independente de plataforma, contanto que o Python esteja em execução. |

## Conclusão

Percorremos **how to insert rectangle shape**, demonstramos **how to change shadow color**, explicamos **how to add outer shadow** e, finalmente, mostramos como **apply shadow effect to shape** usando Aspose.Words for Python. O script completo está pronto para ser inserido em qualquer pipeline de automação, proporcionando um retângulo com aparência profissional e sombra refinada em segundos.

Pronto para o próximo passo? Experimente trocar a cor de preenchimento, brincar com diferentes ângulos de `direction`, ou adicionar múltiplas formas na mesma página. Você também pode explorar a rica API de formatação de texto do Aspose.Words para combinar sombras com texto estilizado — perfeito para relatórios que chamam a atenção.

Se este tutorial foi útil, dê um joinha, compartilhe com a equipe ou deixe um comentário com suas próprias variações. Boa codificação!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## O Que Você Deve Aprender a Seguir?

Os tutoriais abaixo abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}