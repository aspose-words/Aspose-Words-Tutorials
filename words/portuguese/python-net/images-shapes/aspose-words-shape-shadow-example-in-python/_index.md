---
category: general
date: 2026-11-18
description: O exemplo de sombra de forma do Aspose.Words mostra como adicionar uma
  sombra a uma forma do Word usando Python. Siga este guia passo a passo para modificar
  e salvar o documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: pt
lastmod: 2026-11-18
og_description: O exemplo de sombra de forma do Aspose.Words demonstra como adicionar
  uma sombra a uma forma do Word com Python. Aprenda o código completo, por que cada
  etapa é importante e como adaptá‑lo.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Exemplo de sombra de forma Aspose.Words – Guia Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Exemplo de sombra de forma do Aspose.Words em Python
url: /pt/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exemplo de sombra em forma do Aspose.Words em Python

O exemplo de sombra em forma do Aspose.Words demonstra como adicionar um efeito de sombra a uma forma em um documento Word usando Python. Neste tutorial você obterá um script completo e executável que carrega um documento, configura a sombra e salva o resultado.

Aplicar sombra a uma forma é uma maneira comum de melhorar a hierarquia visual em relatórios, brochuras ou faturas. O código abaixo funciona com Aspose.Words for Python via .NET e não requer bibliotecas de terceiros adicionais.

## O que você aprenderá

* Como carregar um arquivo `.docx` com **Aspose.Words for Python**.  
* Como localizar a primeira forma (incluindo formas dentro de tabelas ou grupos).  
* Como configurar o desfoque, o deslocamento horizontal e o deslocamento vertical da sombra.  
* Como salvar o documento modificado preservando todo o restante do conteúdo.  

**Pré‑requisitos**

* Python 3.8 ou superior.  
* Aspose.Words for Python via .NET instalado (`pip install aspose-words`).  
* Um documento Word (`input.docx`) que contenha ao menos uma forma (por exemplo, uma imagem, AutoShape ou caixa de texto).  

Se precisar instalar a biblioteca, execute:

```bash
pip install aspose-words
```

## Exemplo de sombra em forma do Aspose.Words – visão geral

O script a seguir é a solução completa. Ele segue as quatro etapas lógicas de um fluxo de trabalho típico de **manipulação de documentos Aspose**: carregar, localizar, modificar e salvar.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Resultado esperado

Abra `output.docx` no Microsoft Word. A primeira forma que você adicionou deve agora exibir uma sombra suave deslocada em 2 pt horizontalmente e verticalmente, com raio de desfoque de 5 pt. Todo o restante do conteúdo permanece inalterado.

## Etapa 1: Carregar o documento Word

Carregar um documento é a primeira operação em qualquer fluxo de trabalho **Aspose.Words for Python**. A classe `Document` analisa o arquivo e constrói um modelo de objetos em memória. Como a biblioteca funciona na plataforma .NET, ela pode lidar com arquivos grandes de forma eficiente.

*Por que isso importa:* Carregar o documento uma única vez e manter uma referência (`doc`) evita I/O repetido, o que melhora o desempenho quando você precisa aplicar várias modificações.

## Etapa 2: Acessar a forma

Formas podem ser filhos diretos do corpo do documento, ou podem estar aninhadas dentro de tabelas, grupos ou canvases de desenho. Usar `get_child(NodeType.SHAPE, 0, True)` pesquisa recursivamente e retorna a primeira forma correspondente.

*Por que isso importa:* O parâmetro `True` garante que você não perca formas que estejam ocultas dentro de outros nós. Se você o omitisse, apenas formas de nível superior seriam consideradas, e muitos documentos reais retornariam `None`.

### Alternativa: Encontrar uma forma por nome

Se o seu documento contiver várias formas, talvez prefira localizar uma específica:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Este trecho demonstra uma variação de **python shape shadow** que filtra pela propriedade `name` da forma.

## Etapa 3: Configurar a sombra da forma

A propriedade `shadow` de um objeto `Shape` oferece controle detalhado sobre o efeito visual. Os três atributos mais comumente ajustados são:

| Propriedade | Faixa típica | Impacto visual |
|-------------|--------------|----------------|
| `blur`      | 0 – 15       | Valores maiores criam uma borda mais suave. |
| `offset_x`  | –10 – 10     | Valores positivos deslocam a sombra para a direita. |
| `offset_y`  | –10 – 10     | Valores positivos deslocam a sombra para baixo. |

Você também pode modificar `color`, `transparency`, `visible` e `style`. O exemplo define um desfoque modesto e um pequeno deslocamento para manter a sombra sutil.

**Dica profissional:** Quando uma forma já possui sombra, as propriedades acima sobrescrevem as configurações existentes. Se precisar preservar o estilo original, leia os valores atuais antes de alterá‑los.

## Etapa 4: Salvar o documento modificado

Chamar `doc.save()` grava a representação em memória de volta para um arquivo `.docx`. O Aspose.Words atualiza automaticamente todas as relações internas, de modo que o arquivo de saída permanece totalmente compatível com o Microsoft Word.

*Por que isso importa:* Salvar apenas uma vez ao final do processo reduz o risco de corrupção de arquivos e melhora a velocidade geral, especialmente ao processar muitos documentos em um lote.

## Variações comuns e casos de borda

### Trabalhando com várias formas

Se precisar aplicar a mesma sombra a todas as formas, itere sobre a coleção de nós:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Aplicando sombra a um tipo específico de forma

Você pode filtrar por `ShapeType` (por exemplo, `aw.ShapeType.IMAGE`). Isso é útil quando você deseja afetar apenas imagens, não AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Manipulando documentos sem formas

O script já gera um `ValueError` claro se nenhuma forma for encontrada. Em código de produção, você pode registrar o problema e continuar processando outros arquivos.

### Notas de compatibilidade

* O código funciona com **Aspose.Words for Python via .NET** versão 23.10 ou posterior.  
* O efeito de sombra é suportado no Word 2007+ (`.docx`). Formatos mais antigos (`.doc`) perderão o efeito após a conversão.

## Conclusão

Este **exemplo de sombra em forma do aspose.words** orienta você através do carregamento de um arquivo Word, localização de uma forma, configuração de sua sombra e salvamento do resultado com **Aspose.Words for Python**. Agora você tem um padrão reutilizável para qualquer cenário de **manipulação de documentos Aspose** que envolva aprimoramentos visuais.

Em seguida, você pode explorar:

* Adicionar preenchimentos gradientes ou estilos de linha a formas (`modify shape shadow` e outras propriedades visuais).  
* Combinar a configuração de sombra com formatação de texto para criar modelos totalmente estilizados.  
* Automatizar o processo para um lote de documentos usando `os.listdir` e o padrão mostrado acima.

Sinta‑se à vontade para experimentar diferentes níveis de desfoque, deslocamentos e cores para adequar às diretrizes da sua marca. Feliz codificação!


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [How to set shadow on a shape in Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [How to save PNG and add shadow to shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}