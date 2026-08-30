---
category: general
date: 2026-06-30
description: Adicione sombra a uma forma usando Aspose.Words para Python. Aprenda
  como definir a distância da sombra, personalizar o desfoque e salvar rapidamente
  um PDF com sombra na forma.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: pt
og_description: Adicione sombra a uma forma em um documento Word com Aspose.Words
  para Python. Este tutorial mostra como definir a distância, o desfoque e a cor da
  sombra e, em seguida, salvar como PDF.
og_title: Adicionar Sombra a uma Forma em Python – Guia Completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Adicionar sombra a forma em Python com Aspose.Words – Guia completo
url: /pt/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar Sombra a Forma em Python com Aspose.Words – Guia Completo

Adicionar sombra a uma forma em um documento Word usando Aspose.Words para Python é mais fácil do que você imagina. Se você já se perguntou **como definir a distância da sombra** ou **como adicionar sombra a uma forma** para um visual refinado, este guia tem tudo o que você precisa.

Nos próximos minutos vamos percorrer tudo o que você precisa: desde criar um documento novo, inserir um retângulo, ajustar as propriedades da sombra, até salvar um PDF que demonstra o efeito. Ao final, você será capaz de aplicar uma sombra a qualquer forma — retângulo, elipse ou desenho personalizado — sem precisar vasculhar a documentação da API.

> **Pré‑requisitos** – Você deve ter Python 3.7+ instalado, uma licença do Aspose.Words para Python (ou uma avaliação gratuita) e familiaridade básica com scripts em Python. Nenhuma outra biblioteca externa é necessária.

---

## Adicionar Sombra a Forma – Visão Geral Passo a Passo

A seguir, um roteiro rápido do que vamos realizar:

1. **Criar um novo documento** e um `DocumentBuilder` para editá‑lo.  
2. **Inserir uma forma retangular** do tamanho que precisar.  
3. **Habilitar e personalizar a sombra** – é aqui que a palavra‑chave principal brilha.  
4. **Salvar o documento** como PDF mantendo a sombra da forma.

Cada passo está dividido em sua própria seção, para que você possa copiar‑colar os trechos de código diretamente no seu IDE.

---

## Passo 1: Inicializar o Documento e o Builder

Primeiro de tudo — sem um `Document` você não tem nada para trabalhar. O `DocumentBuilder` é o seu pincel.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Por que isso importa*: O objeto `Document` representa o arquivo inteiro, enquanto o `DocumentBuilder` simplifica a inserção de texto, tabelas e formas. Pense no builder como um cursor que você pode mover pela página.

---

## Passo 2: Inserir uma Forma Retangular

Agora vamos adicionar um retângulo — nossa tela para o efeito de sombra. Você pode substituir `RECTANGLE` por `ELLIPSE`, `STAR` ou qualquer outro `ShapeType` se precisar de uma geometria diferente.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Dica de especialista*: As dimensões estão em pontos (1 pt ≈ 1/72 polegada). Ajuste‑as para se adequar ao seu layout; a sombra será dimensionada automaticamente.

---

## Como Definir a Distância da Sombra

A **distância** da sombra determina o quão longe ela aparece da forma. Uma distância maior imita uma fonte de luz mais distante, enquanto um valor menor gera um leve relevo.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Observação**: A distância funciona em conjunto com `angle`. Alterar o ângulo gira a sombra ao redor da forma, enquanto `distance` a empurra para fora.

---

## Como Adicionar Sombra à Forma – Personalizando Desfoque, Cor e Ângulo

Adicionar uma sombra não é apenas ativá‑la; geralmente você quer ajustar desfoque, cor e direção para um efeito realista.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Por que essas configurações?*  
- **Raio de desfoque** suaviza a borda, evitando uma silhueta agressiva.  
- **Ângulo** simula a fonte de luz; 45° é um padrão comum que parece equilibrado.  
- **Cor** pode ser qualquer objeto `Color`; experimente `Color.gray` para um efeito mais suave.

---

## Passo 4: Salvar o Documento como PDF

Com a forma e sua sombra prontas, persistir o resultado é simples. O Aspose.Words cuida da conversão para PDF automaticamente, preservando a fidelidade visual.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Saída esperada*: Abra o `ShadowShape.pdf` gerado. Você verá uma única página com um retângulo de 200 × 100 pt, sua sombra projetada a 4 pt de distância em um ângulo de 45°, desfocada em 5 pt. A sombra deve aparecer como um halo cinza‑preto sutil envolvendo a forma.

---

## Perguntas Frequentes & Casos de Borda

### E se eu precisar de uma forma diferente?

Substitua `aw.drawing.ShapeType.RECTANGLE` por qualquer outro valor enum, por exemplo, `aw.drawing.ShapeType.ELLIPSE`. As mesmas propriedades de sombra se aplicam — sem código extra necessário.

### Posso aplicar sombra a várias formas ao mesmo tempo?

Sim. Percorra as formas que você cria e configure cada `shadow_format` individualmente. Aqui está um trecho rápido:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Como mudar a opacidade da sombra?

Use a propriedade `shadow.transparency` (0 = opaco, 1 = totalmente transparente):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Exemplo Completo em Funcionamento

Abaixo está o script completo — copie, ajuste a pasta de saída e execute. Nenhuma parte está faltando.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Execute o script e, em seguida, abra o PDF resultante. Você deverá ver o retângulo com uma sombra nítida e deslocada — exatamente o que **add shadow to shape** promete.

---

## Conclusão

Acabamos de demonstrar como **add shadow to shape** em um documento Word usando Aspose.Words para Python, cobrindo os passos essenciais para **set shadow distance**, personalizar desfoque, ângulo e cor, e finalmente exportar um PDF que mantém o efeito. Essa técnica funciona para qualquer tipo de forma, e você pode ampliá‑la com loops, ajustes de opacidade ou até sombras em gradiente.

Pronto para o próximo desafio? Experimente combinar múltiplas sombras, sobrepor formas ou gerar um relatório onde cada gráfico receba sua própria sombra estilizada. Experimentar consolidará os conceitos e revelará novas possibilidades para automação de documentos.

Se este guia foi útil, sinta‑se à vontade para compartilhá‑lo, dar uma estrela ao repositório Aspose.Words ou deixar um comentário com suas próprias dicas de ajuste de sombra. Feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}