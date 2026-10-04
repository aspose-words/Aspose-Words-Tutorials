---
category: general
date: 2026-10-04
description: Como criar um documento em Python e adicionar sombra a uma forma usando
  Aspose.Words. Aprenda a definir a cor da sombra, inserir uma forma retangular e
  personalizar a sombra externa.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: pt
lastmod: 2026-10-04
og_description: Como criar um documento em Python e adicionar sombra a uma forma.
  Este guia mostra como definir a cor da sombra, inserir uma forma retangular e aplicar
  uma sombra externa usando Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Como criar um documento com uma forma retangular e sombra em Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Como criar documento com forma de retângulo e sombra em Python
url: /pt/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento com forma retangular e sombra em Python

Se você precisa **como criar documento** que contém um retângulo estilizado, este guia oferece uma solução completa. Você verá como **adicionar sombra à forma**, definir a cor da sombra e controlar seu deslocamento e desfoque — tudo com Aspose.Words for Python. Ao final do tutorial você pode gerar um arquivo `.docx` que parece polido e pronto para distribuição.

Os passos abaixo cobrem tudo, desde a instalação da biblioteca até a personalização da aparência da sombra. Nenhuma documentação externa é necessária; o código está pronto para copiar, executar e adaptar aos seus próprios projetos. Você também aprenderá como **inserir forma retangular**, escolher um **estilo de sombra externa**, e lidar com armadilhas comuns, como sombras invisíveis ou configurações de wrap incorretas.

## Pré-requisitos

* Python 3.8 ou superior instalado.
* Uma licença ativa do Aspose.Words for Python (ou uma chave de avaliação gratuita).
* Familiaridade básica com scripts em Python.
* Acesso a um local no sistema de arquivos onde o documento gerado será salvo.

Você pode instalar o SDK com pip:

```bash
pip install aspose-words
```

## Etapa 1: Importar a biblioteca e criar um novo documento em branco

Criar um novo documento é a primeira ação em qualquer cenário de automação do Word. O construtor `aw.Document()` fornece um arquivo vazio que você pode preencher com texto, imagens ou formas.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

O objeto `DocumentBuilder` simplifica a inserção de conteúdo. Ele acompanha a posição atual do cursor, permitindo que você adicione elementos sequencialmente sem gerenciar manualmente as seções.

## Etapa 2: Inserir uma forma retangular do tamanho desejado

Uma forma retangular funciona como um contêiner para elementos visuais. Você pode definir sua largura e altura em pontos (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Neste ponto a forma não tem estilo visual, aparecendo apenas como um contorno simples. Os próximos passos lhe darão profundidade e cor.

## Etapa 3: Definir a forma para fluir inline com o texto ao redor

Quando uma forma está **inline**, ela se comporta como um caractere em um parágrafo. Isso garante que o retângulo permaneça onde você espera no layout do documento.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Se você preferir que a forma flutue sobre o texto, pode usar `WrapType.SQUARE` ou `WrapType.TOP_BOTTOM`, mas para a maioria dos relatórios uma forma inline mantém o layout previsível.

## Etapa 4: Tornar a sombra visível e escolher sua cor

Uma sombra que não é visível não traz benefício visual. A flag `visible` ativa o efeito, e a propriedade `color` determina seu tom. Usar preto fornece uma profundidade clássica e sutil.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Você pode substituir `aw.drawing.Color.black` por qualquer outra cor, como `aw.drawing.Color.gray` ou um valor RGB personalizado (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Etapa 5: Definir o deslocamento e o desfoque da sombra para dar profundidade

O deslocamento controla quão longe a sombra é deslocada da forma, enquanto o raio de desfoque suaviza as bordas. Valores pequenos criam uma sombra nítida; valores maiores produzem um aspecto mais suave.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Experimente esses números para adequá‑los às diretrizes de design. Para uma sombra projetada pesada, você pode aumentar tanto o deslocamento quanto o desfoque.

## Etapa 6: Escolher um estilo de sombra externa

Aspose.Words oferece vários estilos de sombra, como `INNER`, `OUTER` e `PERSPECTIVE`. O estilo **outer** coloca a sombra fora da borda da forma, o que é ideal para uma aparência limpa e profissional.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Se precisar de um efeito mais dramático, experimente `ShadowStyle.PERSPECTIVE` — ele adiciona uma inclinação tridimensional.

## Etapa 7: Salvar o documento com a sombra na forma

Salvar finaliza o arquivo e grava toda a formatação no disco. Escolha um diretório onde você tenha permissão de escrita e dê ao arquivo um nome descritivo.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Executar o script produz um arquivo Word que contém um retângulo com uma sombra visível e colorida. Abra o arquivo no Microsoft Word ou LibreOffice para verificar o resultado.

## Exemplo completo executável

Abaixo está o script completo que incorpora cada passo discutido. Copie o código para um arquivo chamado `create_shadowed_shape.py` e execute‑o com `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Saída esperada**

Ao abrir `ShapeWithShadow.docx`, você verá um único retângulo centralizado na página. O retângulo é acompanhado por uma sutil sombra preta deslocada para a parte inferior‑direita, levemente desfocada para criar profundidade. A sombra respeita o estilo outer, portanto não intersecta o interior do retângulo.

## Perguntas comuns e casos de borda

### Por que a sombra às vezes aparece invisível?

A sombra só é renderizada se `shadow.visible` estiver definido como `True` **e** o `wrap_type` da forma permitir que ela seja exibida. Uma forma inline funciona de forma confiável; formas flutuantes podem exigir ajustes adicionais de layout.

### Como posso mudar a cor da sombra para combinar com a paleta da marca?

Substitua `aw.drawing.Color.black` por um valor RGB personalizado:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### E se eu precisar que a forma apareça atrás do texto?

Defina o tipo de wrap para `WrapType.BEHIND` e ajuste `z_order_position` se necessário. Lembre‑se de que alguns visualizadores podem renderizar formas atrás‑do‑texto de maneira diferente.

### Posso aplicar as mesmas configurações de sombra a várias formas?

Sim. Crie uma função auxiliar que configure a sombra e chame‑a para cada forma que você inserir. Isso promove a reutilização de código e garante consistência de estilo.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Conclusão

Agora você sabe **como criar documento** que contêm arquivos com uma forma retangular e sombra personalizada usando Aspose.Words for Python. O tutorial abordou a inserção de um retângulo, tornar a forma inline, habilitar a sombra, definir sua cor, deslocamento, desfoque e estilo, e finalmente salvar o arquivo.

A partir daqui você pode explorar tópicos relacionados, como **add shadow to shape** para outros tipos de forma, **set shadow color** dinamicamente com base em dados, ou **how to add shadow** a imagens e caixas de texto. Experimente diferentes dimensões, cores e estilos de sombra para combinar com as diretrizes da sua marca ou sistema de design.

Pronto para automatizar mais documentos Word? Experimente adicionar tabelas, cabeçalhos ou conteúdo dinâmico a seguir — cada passo se baseia nos mesmos princípios demonstrados aqui. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar forma retangular, adicionar sombra e salvar PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Criar documento Word em branco com forma retangular sombreada – Guia passo a passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Como gerenciar variáveis de documento com Aspose.Words em Python: Um guia completo](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}