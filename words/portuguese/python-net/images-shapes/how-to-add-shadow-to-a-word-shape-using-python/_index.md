---
category: general
date: 2026-08-14
description: Como adicionar sombra a uma forma do Word usando Python – aprenda a aplicar
  efeito de sombra, criar efeito de sombra e salvar o documento Word de forma eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow
- apply shadow effect
- create shadow effect
- save word document
- add shadow to shape
language: pt
lastmod: 2026-08-14
og_description: Como adicionar sombra a uma forma do Word usando Python. Siga este
  tutorial completo para aplicar efeito de sombra, criar efeito de sombra e salvar
  o documento do Word com um visual profissional.
og_image_alt: Screenshot illustrating how to add shadow to a Word shape using Python
og_title: Como adicionar sombra a uma forma do Word usando Python – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  headline: How to add shadow to a Word shape using Python
  type: TechArticle
- description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  name: How to add shadow to a Word shape using Python
  steps:
  - name: Load the Word document
    text: '```python import aspose.words as aw'
  - name: Retrieve the target shape
    text: '```python # Get the first shape in the document tree. shape = doc.get_child(aw.NodeType.SHAPE,
      0, True) ```'
  - name: Create a shadow object for the shape
    text: '```python # Instantiate a Shadow object and assign it to the shape. shape.shadow
      = aw.Shadow() ```'
  - name: Configure the shadow’s appearance
    text: '```python # Adjust the softness of the shadow edges. shape.shadow.blur
      = 5 # Higher values = softer edges'
  - name: Save the document to apply the changes
    text: '```python # Save the modified document. Overwrite or specify a new file
      name. doc.save("YOUR_DIRECTORY/output.docx") ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
- Document styling
title: Como adicionar sombra a uma forma do Word usando Python
url: /pt/python/images-shapes/how-to-add-shadow-to-a-word-shape-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar sombra a uma forma do Word usando Python

Se você precisa **adicionar sombra** a uma forma dentro de um documento Word, este guia mostra os passos exatos. Você aprenderá como aplicar efeito de sombra, criar efeito de sombra e salvar o documento Word sem sair do seu IDE.

Adicionar uma sombra visual faz diagramas, chamadas e ícones se destacarem, melhorando a legibilidade para os usuários finais. O tutorial assume que você tem conhecimentos básicos de Python e uma versão recente da biblioteca Aspose.Words for Python instalada.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.8 ou mais recente instalado.  
* Pacote `aspose-words` (`pip install aspose-words`) – a biblioteca que manipula arquivos DOCX.  
* Um documento Word (`input.docx`) que contenha ao menos uma forma (por exemplo, um AutoShape ou imagem).

Esses requisitos garantem que o código seja executado sem alterações no Windows, macOS ou Linux.

## Como adicionar sombra a uma forma em um documento Word

As seções a seguir dividem a tarefa em passos claros e numerados. Cada passo explica **por que** a operação é importante, não apenas **o que** digitar.

### Passo 1: Carregar o documento Word

```python
import aspose.words as aw

# Load the existing DOCX file. Replace YOUR_DIRECTORY with the actual path.
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Por que isso importa:* Carregar o documento cria uma representação em memória que você pode manipular. Sem esse objeto, não é possível acessar formas ou aplicar estilos.

### Passo 2: Recuperar a forma alvo

```python
# Get the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

*Por que isso importa:* `get_child` percorre a hierarquia de nós do documento e devolve o tipo de nó solicitado. O terceiro argumento (`True`) indica ao Aspose.Words que a busca deve ser recursiva, garantindo que você encontre uma forma mesmo que ela esteja dentro de um parágrafo ou de uma tabela.

> **Dica profissional:** Se o seu documento contiver várias formas, itere com `doc.get_child_nodes(aw.NodeType.SHAPE, True)` e selecione a que precisar por índice ou verificando `shape.title` ou `shape.alt_text`.

### Passo 3: Criar um objeto de sombra para a forma

```python
# Instantiate a Shadow object and assign it to the shape.
shape.shadow = aw.Shadow()
```

*Por que isso importa:* Uma instância de `Shadow` contém todos os parâmetros visuais (blur, distance, color etc.). Atribuí‑la à forma indica ao Word que deve renderizar uma sombra quando o documento for aberto.

### Passo 4: Configurar a aparência da sombra

```python
# Adjust the softness of the shadow edges.
shape.shadow.blur = 5          # Higher values = softer edges

# Set how far the shadow is offset from the shape.
shape.shadow.distance = 3     # Measured in points

# Optional: change the shadow color to a light gray.
shape.shadow.color = aw.Color.gray

# Optional: set the shadow's transparency (0 = opaque, 255 = fully transparent).
shape.shadow.transparency = 50
```

*Por que isso importa:* `blur` controla a difusão da sombra, enquanto `distance` determina o deslocamento. Ajustar esses valores permite obter um leve relevo ou um efeito dramático de sombra projetada. Modificar `color` e `transparency` personaliza ainda mais o visual, o que é essencial quando o documento segue um guia de estilo corporativo.

### Passo 5: Salvar o documento para aplicar as alterações

```python
# Save the modified document. Overwrite or specify a new file name.
doc.save("YOUR_DIRECTORY/output.docx")
```

*Por que isso importa:* O método `save` grava as alterações em memória de volta para um arquivo DOCX físico. Após salvar, abrir `output.docx` no Microsoft Word exibirá a forma com a sombra configurada.

## Script completo que você pode executar hoje

Abaixo está o programa Python completo, pronto para execução. Substitua `YOUR_DIRECTORY` pela pasta que contém seus arquivos.

```python
import aspose.words as aw

# 1️⃣ Load the source document.
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# 2️⃣ Retrieve the first shape (you can loop for multiple shapes).
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# 3️⃣ Attach a new Shadow object.
shape.shadow = aw.Shadow()

# 4️⃣ Configure shadow properties.
shape.shadow.blur = 5
shape.shadow.distance = 3
shape.shadow.color = aw.Color.gray
shape.shadow.transparency = 50

# 5️⃣ Save the updated document.
doc.save("YOUR_DIRECTORY/output.docx")
```

### Resultado esperado

Ao abrir `output.docx` no Microsoft Word:

* A primeira forma exibirá uma sombra cinza suave deslocada em três pontos.  
* As bordas da sombra aparecerão desfocadas, dando à forma um leve levantamento tridimensional.  
* Nenhum outro conteúdo do documento será alterado.

Se você não vir a sombra, verifique se a forma não é uma imagem com transparência definida em 100 % ou se o modo de visualização do documento (Layout de Impressão) está ativo.

## Variações comuns e casos de borda

| Situação | Como adaptar o código |
|-----------|-----------------------|
| **Múltiplas formas** | Use `doc.get_child_nodes(aw.NodeType.SHAPE, True)` e itere sobre a coleção, aplicando a mesma configuração de sombra a cada forma. |
| **Somente certas formas precisam de sombra** | Verifique `shape.name` ou `shape.title` dentro do laço e aplique a sombra apenas quando o nome corresponder ao seu critério. |
| **Cores de sombra diferentes** | Defina `shape.shadow.color = aw.Color(255, 0, 0)` para uma sombra vermelha, ou use `aw.Color.from_argb(alpha, r, g, b)` para opacidade personalizada. |
| **Nenhuma forma existente** | Envolva a recuperação em um bloco `try/except`; se `shape` for `None`, crie uma nova `Shape` (por exemplo, um retângulo) e adicione‑a ao documento antes de aplicar a sombra. |
| **Salvar como PDF** | Após adicionar a sombra, chame `doc.save("output.pdf")` – a sombra será renderizada corretamente na exportação PDF. |

Essas variações garantem que o tutorial continue útil, seja você quem processe um único modelo ou um lote de documentos.

## Como adicionar sombra sem Aspose.Words (alternativa)

Se você prefere a biblioteca `python-docx`, não é possível definir diretamente uma sombra porque a biblioteca não expõe os elementos VML/OOXML subjacentes. Nesse caso, seria necessário manipular o XML manualmente:

```python
from docx import Document
from lxml import etree

doc = Document("input.docx")
shape = doc.inline_shapes[0]._inline
# Insert <v:shadow> element here (complex XML manipulation)
```

Como o Aspose.Words fornece uma API de alto nível `Shadow`, **adicionar sombra** é muito mais simples com essa biblioteca.

## Próximos passos

Agora que você sabe **como adicionar sombra** a uma forma, pode:

* **aplicar efeito de sombra** a tabelas ou caixas de texto usando a mesma classe `Shadow`.  
* **criar efeito de sombra** com diferentes combinações de blur e distance para fins de branding.  
* Explorar **adicionar sombra a forma** junto a outras opções de formatação, como espessura da linha, cor de preenchimento e rotação.  
* Automatizar o processamento em massa lendo uma pasta de arquivos DOCX, aplicando a sombra e salvando cada um com um nome contendo timestamp.

Essas extensões permitem construir um pipeline completo de estilização de documentos que atende aos padrões de design corporativo.

---

*Você aprendeu como adicionar sombra a uma forma do Word usando Python, como aplicar efeito de sombra, como criar efeito de sombra e como salvar o documento Word com a nova formatação.* Sinta‑se à vontade para experimentar os parâmetros e compartilhar seus resultados nos comentários!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}