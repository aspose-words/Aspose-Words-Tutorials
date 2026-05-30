---
category: general
date: 2026-05-30
description: Como inserir um retângulo e adicionar sombra no Word usando Aspose –
  um guia passo a passo em Python para criar um documento Word com efeito de sombra
  em forma.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: pt
og_description: Como inserir um retângulo e adicionar sombra no Word usando Aspose
  – aprenda a criar um documento Word com efeito de sombra em forma em Python.
og_title: Como inserir um retângulo e adicionar sombra no Word usando Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Como inserir retângulo e adicionar sombra no Word usando Aspose
url: /pt/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir um retângulo e adicionar sombra no Word usando Aspose

Já se perguntou **como inserir um retângulo** em um arquivo Word sem abrir a interface do usuário? Você não está sozinho. Muitos desenvolvedores precisam gerar relatórios, faturas ou certificados em tempo real, e desenhar um retângulo simples com uma sombra agradável pode deixar a saída mais polida. Neste tutorial vamos percorrer os passos exatos para criar um documento Word, inserir uma forma retangular e aplicar uma sombra realista usando Aspose.Words para Python.

Cobriremos tudo, desde a configuração do pacote Aspose até o ajuste da distância, desfoque e opacidade da sombra. Ao final, você terá um trecho reutilizável que pode ser inserido em qualquer pipeline de automação. Sem mágica, apenas código claro e algumas dicas práticas.

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

- Python 3.8+ instalado (o código funciona em 3.9, 3.10 e versões mais recentes)
- Uma licença ativa do Aspose.Words para Python ou uma chave de avaliação gratuita
- Pacote `aspose-words` instalado via `pip install aspose-words`
- Uma pasta gravável onde o **create word document aspose** gerado será salvo

É só isso — sem DLLs extras, sem interop COM, apenas Python puro.

## Etapa 1: Inicializar o Documento (How to create word document aspose)

Primeiro de tudo: você precisa de um objeto `Document` novo. Pense nele como uma tela em branco. O código a seguir cria o documento e um `DocumentBuilder` que nos permitirá inserir formas.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Por que isso importa:* O `DocumentBuilder` oferece uma API de alto nível para adicionar parágrafos, tabelas e — sim — formas sem lidar com árvores de nós de baixo nível. Se você pular o builder e manipular nós diretamente, acabará com código verboso e mais difícil de manter.

## Etapa 2: Inserir o Retângulo (how to insert rectangle)

Agora realmente **how to insert rectangle**. O Aspose.Words trata um retângulo como um tipo de forma genérica. Você especifica a largura e a altura em pontos (1 ponto ≈ 1/72 polegada). Sinta‑se à vontade para ajustar os números conforme sua diagramação.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Dica profissional:** Se precisar posicionar o retângulo em um local específico da página, defina `shape.left` e `shape.top` após a inserção. Isso fornece controle pixel‑perfeito.

## Etapa 3: Acessar o Formato de Sombra da Forma (add shadow to shape)

O visual de uma forma reside em seu `ShadowFormat`. Ao recuperá‑lo, ganhamos acesso a todas as propriedades que definem a aparência da sombra.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Neste ponto a sombra está invisível — pense nela como uma camada oculta aguardando suas instruções.

## Etapa 4: Configurar a Sombra (how to add shape shadow, apply shadow effect word)

É aqui que a mágica acontece. Vamos ativar a sombra e ajustar sua aparência. Os valores abaixo produzem uma sombra suave e diagonal que funciona bem na maioria dos documentos, mas você pode experimentar.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### O que cada propriedade faz

| Propriedade | Efeito | Faixa Típica |
|-------------|--------|--------------|
| `visible` | Ativa/desativa a sombra | `True` / `False` |
| `distance` | Distância da sombra em relação à forma | 2 – 10 pts |
| `blur` | Suavidade das bordas da sombra | 4 – 12 pts |
| `color` | Tom da sombra; cinza escuro é um padrão seguro | Qualquer `aw.Color` |
| `opacity` | Transparência; 0 = invisível, 1 = sólida | 0.3 – 0.8 para aspecto sutil |
| `angle` | Direção da luz | 0 – 360° |

**Por que ajustar isso?** Uma sombra bem afinada pode fazer um retângulo plano parecer elevado da página, adicionando profundidade sem imagens. Se definir `opacity` muito alta, a sombra fica agressiva; muito baixa e ela desaparece.

## Etapa 5: Salvar o Documento (create word document aspose)

Por fim, grave o arquivo no disco. Você pode usar qualquer extensão suportada pelo Aspose.Words (`.docx`, `.pdf`, `.html`). Para este tutorial, vamos ficar com `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Abra o arquivo resultante no Microsoft Word e você verá um retângulo nítido com uma sombra sutil — exatamente o que se espera de um modelo profissional.

![como inserir forma de retângulo com sombra usando Aspose.Words](/images/rectangle-shadow.png){alt="como inserir forma de retângulo com sombra usando Aspose.Words"}

*A captura de tela (acima) mostra o retângulo com a sombra aplicada. Observe o leve desfoque e o ângulo de 45°, que confere um aspecto natural.*

## Variações Comuns e Casos de Borda

### Adicionando Múltiplas Formas

Se precisar de mais de um retângulo, basta repetir a chamada `insert_shape`. Lembre‑se de mover o cursor do builder (`builder.move_to(shape)`) ou ajustar `shape.left`/`shape.top` para evitar sobreposição.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Alterando o Tipo de Forma

Embora este guia foque em retângulos, o mesmo padrão funciona para óvalos, estrelas ou formas livres personalizadas. Substitua `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.CLOUD`, etc., e as configurações de sombra permanecem idênticas.

### Salvando em Outros Formatos

O Aspose.Words pode exportar para PDF, PNG ou até XPS com uma única linha:

```python
doc.save("output/ShapeWithShadow.pdf")
```

A renderização da sombra é preservada entre os formatos, portanto seu PDF terá a mesma aparência do arquivo Word.

### Lidando com Documentos Grandes

Ao gerar relatórios massivos, considere chamar `doc.update_page_layout()` após inserir todas as formas. Isso força uma passagem de layout e pode melhorar o desempenho quando você converter para PDF posteriormente.

## Exemplo Completo em Funcionamento (Todas as Etapas Combinadas)

Abaixo está o script completo que você pode copiar‑colar em um arquivo chamado `rectangle_shadow.py`. Execute-o com `python rectangle_shadow.py` e verifique a pasta `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Executar este script produz exatamente o mesmo documento que discutimos anteriormente. Sinta‑se à vontade para ajustar os números; o código foi mantido deliberadamente simples para que você possa experimentar sem receio.

## Perguntas Frequentes

**Q: Isso funciona no Linux?**


## O Que Você Deve Aprender a Seguir?

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}