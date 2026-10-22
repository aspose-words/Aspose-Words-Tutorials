---
category: general
date: 2026-09-30
description: Aprenda a criar uma forma retangular, aplicar sombra à forma e salvar
  o Word com a forma usando Aspose.Words para Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: pt
lastmod: 2026-09-30
og_description: Crie rapidamente uma forma retangular em um documento do Word. Este
  tutorial mostra como adicionar a forma, aplicar sombra à forma, definir o desfoque
  da sombra e salvar o Word com a forma.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Criar forma de retângulo no Word com Python – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Como criar forma de retângulo em um documento Word usando Python
url: /pt/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar forma retangular em um documento Word usando Python

Se você precisa **criar forma retangular** em um arquivo Word, este guia mostra uma solução completa e executável. Você verá como adicionar a forma, aplicar um efeito de sombra, ajustar o desfoque e, finalmente, **salvar Word com forma** para que o resultado possa ser aberto no Microsoft Word ou em qualquer visualizador compatível.

O exemplo usa **Aspose.Words for Python via .NET**, uma biblioteca que permite manipular documentos Word sem precisar do Microsoft Office instalado. Não é necessário ter experiência prévia com a API — apenas conhecimentos básicos de Python.

## O que você vai alcançar

- Inserir um retângulo na primeira seção de um novo documento.  
- Configurar uma sombra suave definindo seu desfoque, deslocamento e cor.  
- Persistir o documento no disco e verificar o resultado visual.

## Pré-requisitos

- Python 3.8 ou superior.  
- Pacote `aspose-words` instalado (`pip install aspose-words`).  
- Permissão de escrita no diretório de saída.

## Criar forma retangular e configurar sua aparência

O primeiro passo é instanciar um documento em branco e adicionar uma forma retangular a ele. A forma servirá como tela para o efeito de sombra.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Por que isso importa:**  
Criar o retângulo fornece um objeto concreto (`shape`) que você pode estilizar posteriormente. Definir dimensões explícitas garante que a forma tenha a mesma aparência em todas as plataformas.

## Como adicionar forma a um documento Word

Embora o código acima já adicione o retângulo, você pode precisar adicionar formas adicionais (por exemplo, círculos, setas) mais tarde. O mesmo padrão se aplica: chame `append_child` no corpo do documento e passe o `ShapeType` desejado.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Dica:** Use a enumeração `ShapeType` para explorar todas as formas suportadas. Isso mantém seu código legível e evita números mágicos.

## Aplicar sombra à forma e definir desfoque da sombra

Uma sombra adiciona profundidade e interesse visual. A classe `ShadowEffect` permite controlar desfoque, deslocamento e cor. Abaixo aplicamos uma sombra preta suave ao retângulo.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Por que definir desfoque?**  
`blur` determina o quão difusa a sombra aparece. Um valor baixo (por exemplo, 1.0) gera uma borda nítida, enquanto um valor mais alto (por exemplo, 5.0) cria um fade suave, que costuma ser mais esteticamente agradável.

**Caso extremo:** Se você definir `blur` como 0, a sombra se torna uma silhueta sólida. Alguns visualizadores podem renderizá‑la com artefatos de aliasing, portanto escolha um valor maior que 0 para uma saída mais suave.

## Salvar Word com forma

Persistir o documento finaliza todas as alterações. O método `save` grava um arquivo `.docx` que qualquer processador Word moderno pode abrir.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Ao abrir `output.docx`, você verá um retângulo posicionado a uma polegada do canto superior‑esquerdo, com uma sombra preta suave deslocada dois pontos para a direita e para baixo. O desfoque da sombra faz a forma parecer levantada da página.

**Pro dica:** Se precisar gerar muitos documentos em um loop, reutilize a mesma instância `Document` e limpe seu corpo entre as iterações para reduzir o consumo de memória.

## Variações comuns e solução de problemas

| Situação | O que mudar | Motivo |
|-----------|----------------|--------|
| Cor de sombra diferente | `shadow.color = aw.Color.red` | Use cores da marca ou destaque formas importantes. |
| Deslocamento de sombra maior | Aumente `shadow.offset_x`/`offset_y` | Enfatize profundidade para maquetes de UI. |
| Sem sombra | Omitir a linha `shape.shadow = shadow` | Útil para relatórios minimalistas. |
| Exportar para PDF em vez de DOCX | `doc.save("output.pdf")` | PDF é ideal para distribuição somente leitura. |

Se a forma não aparecer, verifique se você está adicionando-a à seção correta (`get_first_section()`) e se o documento foi salvo após as modificações.

## Exemplo completo e executável

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Executar o script produz `output.docx` contendo o retângulo com uma sombra suave. Abra o arquivo no Microsoft Word para confirmar que o efeito visual corresponde à descrição.

## Conclusão

Agora você sabe como **criar forma retangular**, **como adicionar forma** a um documento Word, **aplicar sombra à forma**, **definir desfoque da sombra** e, finalmente, **salvar Word com forma** usando Aspose.Words for Python. O mesmo padrão pode ser estendido a outros tipos de forma, cores e efeitos, dando controle total sobre os gráficos do documento sem depender da automação do Office.

**Próximos passos**

- Experimente `Shape.fill` para adicionar gradientes ou fundos de imagem.  
- Use objetos `Paragraph` para colocar texto dentro do retângulo.  
- Combine múltiplas formas para construir diagramas complexos e, então, exporte para PDF para distribuição.  

Sinta‑se à vontade para adaptar o código às suas necessidades de relatórios ou modelagem e compartilhe seus resultados nos comentários!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}