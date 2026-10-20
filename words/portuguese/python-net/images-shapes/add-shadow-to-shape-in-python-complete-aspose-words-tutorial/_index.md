---
category: general
date: 2026-06-08
description: Adicione sombra à forma usando Aspose.Words para Python e defina a cor
  de preenchimento da forma em apenas alguns passos. Aprenda todo o fluxo de trabalho
  com código executável.
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: pt
og_description: Adicione sombra à forma com Aspose.Words para Python e defina a cor
  de preenchimento da forma instantaneamente. Siga este tutorial passo a passo para
  criar a saída em PDF.
og_title: Adicionar Sombra a Forma em Python – Guia Completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Adicionar Sombra a uma Forma em Python – Tutorial Completo do Aspose.Words
url: /pt/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar Sombra a Forma em Python – Tutorial Completo Aspose.Words

Já se perguntou como **adicionar sombra a uma forma** ao gerar um documento com Aspose.Words para Python? Você não está sozinho. Seja criando um modelo de relatório, um folheto de marketing ou um diagrama técnico, uma sombra sutil pode fazer um retângulo se destacar e parecer mais profissional.  

Neste guia também mostraremos **como definir a cor de preenchimento da forma**, para que você obtenha um retângulo totalmente estilizado pronto para exportação em PDF. A solução é simples, o código está pronto‑para‑executar, e o raciocínio por trás de cada linha é explicado em inglês simples.

## O que este tutorial cobre

- Inicializar um documento Aspose.Words e o builder.  
- Inserir uma forma retangular e **definir sua cor de preenchimento**.  
- Definir e aplicar um **efeito de sombra** a essa forma.  
- Salvar o resultado como PDF.  
- Exemplo completo e executável, além de dicas para armadilhas comuns.

Ao final do artigo, você será capaz de inserir um retângulo estilizado em qualquer arquivo Word ou PDF com apenas algumas linhas de Python. Sem ferramentas externas, sem adivinhações.

> **Pré‑requisitos** – Você precisa do Python 3.7+ e do pacote `aspose-words` (`pip install aspose-words`). Qualquer IDE ou editor de texto de sua escolha serve; Visual Studio Code funciona muito bem.

---

## Adicionar Sombra à Forma – Passo a Passo

A seguir dividimos o processo em blocos lógicos. Cada passo inclui o código exato que você precisa, uma breve explicação do *porquê* ele é importante e uma dica rápida para evitar problemas mais tarde.

### Passo 1: Criar o Documento e o Builder

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**Por que isso importa:** `Document` é o contêiner de tudo—páginas, estilos, imagens e formas. O `DocumentBuilder` é a API de alto nível que nos permite posicionar objetos sem nos preocuparmos com árvores de nós de baixo nível.

### Passo 2: Inserir uma Forma Retangular e Definir sua Cor de Preenchimento

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**Por que isso importa:** A forma funciona como uma tela para nossa sombra. Ao **definir a cor de preenchimento da forma** garantimos que o retângulo não seja apenas uma caixa transparente; ele se torna um elemento visível que a sombra pode acentuar. Você pode substituir `Color.BLUE` por qualquer valor RGB ou até mesmo um gradiente se precisar de mais estilo.

> **Dica profissional:** Se você planeja reutilizar a mesma cor em várias formas, armazene-a em uma variável (`my_fill = Color.from_argb(0, 120, 200, 255)`) e reutilize essa referência.

### Passo 3: Definir o Efeito de Sombra

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**Por que isso importa:** Uma sombra não é apenas um truque visual; ela transmite profundidade e hierarquia. O `blur_radius` controla a suavidade, `distance` determina o deslocamento, e `direction` permite simular uma fonte de luz. Ajuste esses valores para combinar com a linguagem de design.

### Passo 4: Aplicar a Sombra à Forma

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**Por que isso importa:** Até que esta linha seja executada, a forma permanece plana. Atribuir o `shadow_effect` indica ao Aspose.Words para renderizar o retângulo com a sombra definida quando o documento for salvo.

### Passo 5: Salvar o Documento como PDF

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**Por que isso importa:** Salvar como PDF fixa o estilo visual, fazendo a sombra aparecer exatamente como você a projetou. Você também pode salvar como `.docx` se precisar de edição posterior—Aspose.Words lida com ambos os formatos sem problemas.

---

## Definir a Cor de Preenchimento da Forma – Personalizando a Aparência

Se precisar de um tom diferente, substitua a atribuição `Color.BLUE` por qualquer um dos exemplos a seguir:

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **Por que você pode querer isso:** Um preenchimento semitransparente combinado com uma sombra pode criar um efeito “vidro” popular em mock‑ups de UI modernos.

---

## Exemplo Completo em Funcionamento

Aqui está o script completo em um único bloco. Copie‑e‑cole em um arquivo chamado `shadow_shape.py` e execute‑o—supondo que você tenha instalado `aspose-words`.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**Saída esperada:** Abra `ShadowShape.pdf` e você verá um retângulo azul com uma sombra preta suave e diagonal deslocada para a parte inferior‑direita. A sombra deve parecer ligeiramente desfocada, dando à forma uma aparência elevada.

---

## Armadilhas Comuns & Dicas Profissionais

| Problema | Por que acontece | Solução |
|------|----------------|-----|
| **Sombra não visível** | O preenchimento da forma está totalmente transparente ou o visualizador de PDF desabilita sombras. | Garanta que `fill_color` seja opaco (`alpha = 255`) ou ajuste a opacidade da `color` da sombra. |
| **Erro de caminho de arquivo** | `YOUR_DIRECTORY` não existe ou você não tem permissão de escrita. | Use `os.makedirs("YOUR_DIRECTORY", exist_ok=True)` antes de `doc.save`. |
| **Importação incorreta** | Tentando importar `ShadowEffect` do sub‑módulo errado. | Importe exatamente como mostrado: `from aspose.words.drawing import ShadowEffect, ShadowType, Color`. |
| **Cor inesperada** | Usando `Color.from_argb` com ordem errada (alpha, red, green, blue). | Lembre-se da ordem: **alpha**, **red**, **green**, **blue**. |

---

## Próximos Passos – Expanda seu Kit de Ferramentas de Formas

Agora que você sabe como **adicionar sombra a uma forma** e **definir a cor de preenchimento da forma**, pode explorar:

- **Preenchimentos em gradiente** (`LinearGradientBrush`) para fundos mais ricos.  
- **Múltiplas sombras** (interna + externa) encadeando objetos `ShadowEffect`.  
- **Outros tipos de forma** (`Ellipse`, `Polygon`) para criar ícones ou elementos de fluxograma.  
- **Incorporar o PDF** em uma resposta web ou anexo de e‑mail usando Flask ou Django.

Cada um desses tópicos se baseia nos mesmos conceitos centrais abordados aqui, então você se sentirá em casa.

---

## Conclusão

Percorremos todo o processo de **adicionar sombra a uma forma** no Aspose.Words para Python enquanto também **definimos a cor de preenchimento da forma**. Desde a criação do documento até a exportação em PDF, o código é autocontido e pronto para uso em produção.

Sinta-se à vontade para ajustar o raio de desfoque, a distância ou a cor para combinar com as diretrizes da sua marca. Se encontrar um caso extremo ou tiver uma solicitação de recurso, deixe um comentário abaixo—bom código!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Configurar Licença Aspose.Words em Python](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial de Sombra em Formas Aspose.Words – Adicionar Sombra a Forma Word em C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}