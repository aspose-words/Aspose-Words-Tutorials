---
category: general
date: 2026-09-27
description: Aprenda como definir sombra em uma forma com Aspose.Words para Python.
  Este guia aborda como adicionar sombra à forma, aplicar efeito de sombra e definir
  a cor da sombra.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: pt
lastmod: 2026-09-27
og_description: Como definir sombra em uma forma usando Aspose.Words para Python.
  Siga o guia passo a passo para adicionar sombra à forma, aplicar efeito de sombra
  e definir a cor da sombra.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Como definir sombra em uma forma no Aspose.Words para Python
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Como definir sombra em uma forma no Aspose.Words para Python
url: /pt/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como definir sombra em uma forma no Aspose.Words for Python

Se você precisa **definir sombra** para um objeto de desenho, este guia mostra o processo completo. Você verá como adicionar sombra a uma forma, configurar o desfoque, o deslocamento e a cor da sombra, e salvar o documento atualizado sem sair do código.

O tutorial parte do pressuposto de que você já tem um ambiente básico do Aspose.Words for Python. Ao final do artigo, você será capaz de aplicar um efeito de sombra com aparência profissional a qualquer forma em um arquivo DOCX.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.8+ instalado.  
* Aspose.Words for Python via .NET (`pip install aspose-words`) instalado.  
* Um documento Word (`input.docx`) que contenha ao menos uma forma (por exemplo, um retângulo ou imagem).  
  Se o documento estiver vazio, o código criará uma nova forma para demonstração.

Esses itens garantem que as etapas subsequentes sejam executadas sem erros de importação.

## Etapa 1: Carregar ou criar o documento Word

A primeira operação é obter um objeto `Document`. Você pode carregar um arquivo existente ou criar um novo.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Por que esta etapa importa*: O objeto `Document` é o ponto de entrada para todas as operações de processamento de Word. Sem ele você não pode acessar formas ou aplicar efeitos visuais.

## Etapa 2: Recuperar a forma alvo

Para manipular a aparência de uma forma, você precisa de uma referência ao nó da forma. O exemplo abaixo obtém a primeira forma encontrada na hierarquia do documento.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Por que esta etapa importa*: `add shadow to shape` requer um objeto de forma concreto. O código trata com segurança o caso em que o documento não contém formas, garantindo que o tutorial funcione para todos os leitores.

## Etapa 3: Configurar a aparência da sombra

Agora você pode **aplicar o efeito de sombra** ajustando a propriedade `shadow` da forma. As configurações a seguir fornecem uma sombra sutil e escura.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Por que cada propriedade importa*:

| Propriedade | Efeito |
|-------------|--------|
| `blur`      | Controla o quão difusa a sombra parece. |
| `offset_x` / `offset_y` | Determina a direção e a distância da sombra em relação à forma. |
| `color`     | Define o tom da sombra; você pode usar qualquer `aw.Color`. |
| `visible`   | Garante que a sombra seja renderizada no arquivo de saída. |

Você pode substituir `aw.Color.black` por `aw.Color.from_argb(255, 0, 0, 0)` para um valor RGBA personalizado, ou por qualquer outra cor predefinida.

## Etapa 4: Salvar o documento modificado

Depois de configurar a sombra, persista as alterações em um novo arquivo.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

Ao abrir `output.docx` no Microsoft Word, a forma selecionada exibirá uma sombra preta suave deslocada 2 pt para a direita e 2 pt para baixo.

## Exemplo completo em funcionamento

Juntando todas as etapas, temos um script autocontido que você pode copiar‑colar no seu IDE.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

Executar o script gera `output.docx` onde a primeira forma contém a sombra configurada.

## Problemas comuns e como evitá‑los

| Problema | Razão | Correção |
|----------|-------|----------|
| `shape` é `None` mesmo após carregar um documento | O documento não contém objetos de desenho. | Use o bloco de criação de forma de fallback mostrado na Etapa 2. |
| A sombra não aparece no Word | `shape.shadow.visible` ficou como `False` ou o documento foi salvo em um formato antigo (ex.: `.doc`). | Garanta `visible = True` e salve como `.docx`. |
| A cor parece diferente do esperado | O tema do documento sobrescreve cores explícitas. | Defina `shape.shadow.color` após desativar sobrescritas de tema, ou use `aw.Color.from_argb`. |

Tratar esses casos de borda torna a solução robusta para código em produção.

## Estendendo o efeito (próximos passos)

Agora que você sabe **como adicionar sombra**, pode explorar aprimoramentos relacionados:

* **apply shadow effect** com gradiente ou sombras múltiplas ajustando as sub‑propriedades de `shape.shadow`.  
* Use **set shadow color** dinamicamente com base na entrada do usuário ou nas cores do tema.  
* Combine **add shadow to shape** com outras ações de formatação, como rotação, estilo de linha ou efeitos 3‑D.  
* Automatize a adição de sombra para cada forma em um documento iterando sobre `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

Essas extensões permitem criar pipelines de geração de documentos sofisticados que produzem saídas polidas e visualmente consistentes.

## Conclusão

Agora você tem uma solução completa e executável para **definir sombra** em uma forma usando Aspose.Words for Python. O guia abordou carregamento de documento, recuperação ou criação de forma, configuração de desfoque, deslocamento e **set shadow color**, e, por fim, salvamento do arquivo. Aplique esse padrão a qualquer forma em seus projetos de automação e experimente ajustes visuais adicionais para atender aos requisitos de design.

--- 

*Sinta‑se à vontade para adaptar o código a outros tipos de forma, cores ou valores de deslocamento. Se encontrar algum problema, revisar a tabela “Problemas comuns” é um bom primeiro passo.*

## O que você deve aprender a seguir?


Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Add shadow to shape in C# – Complete Guide to Apply Shadow Effect](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}