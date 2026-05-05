---
category: general
date: 2026-05-04
description: Aprenda como criar uma forma retangular, como adicionar forma com sombras,
  alterar a cor da sombra, definir a distância da sombra e salvar o documento como
  PDF usando Aspose.Words para Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: pt
og_description: Crie uma forma retangular com Aspose.Words para Python, aprenda como
  adicionar forma, alterar a cor da sombra, definir a distância da sombra e salvar
  o documento como PDF.
og_title: Criar forma retangular – Adicionar sombra, mudar a cor e salvar como PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Criar forma de retângulo em Python – Guia completo para adicionar sombras e
  salvar como PDF
url: /pt/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular – Tutorial completo para desenvolvedores Python

Já precisou **criar forma retangular** em um documento Word e se perguntou como dar a ela uma sombra refinada? Talvez você esteja construindo um gerador de relatórios e o acabamento visual seja importante — especialmente quando o resultado final é um PDF. A boa notícia? Com Aspose.Words para Python você pode não apenas **como adicionar forma**, mas também ajustar cada propriedade da sombra, da cor à distância, e então **salvar documento como pdf** em um fluxo contínuo.

Neste guia, percorreremos todo o processo passo a passo. Você verá o código exato que pode copiar‑colar, entenderá *por que* cada linha importa e receberá algumas dicas para lidar com casos extremos (como sombras transparentes ou DPI não‑padrão). Ao final, você será capaz de **criar forma retangular**, personalizar sua sombra e exportar um PDF nítido sem esforço.

## Pré-requisitos

- Python 3.8+ instalado na sua máquina.  
- Aspose.Words para Python via `pip install aspose-words`.  
- Familiaridade básica com Python orientado a objetos (nada avançado).  

Se você já tem um ambiente virtual configurado, basta executar o comando de instalação e está pronto para usar.

## Etapa 1: Inicializar o Document e o Builder

Antes de poder **como adicionar forma**, você precisa de um documento em branco para trabalhar. A classe `Document` representa o arquivo inteiro, e `DocumentBuilder` é sua ferramenta de pintura.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Por que isso importa:* `Document` contém todas as seções, páginas e recursos. `DocumentBuilder` fornece uma API fluente para inserir conteúdo exatamente onde você precisa — pense nele como um cursor em um processador de texto.

## Etapa 2: Inserir a Forma Retangular

Agora realmente **como adicionar forma**. O método `insert_shape` precisa do tipo de forma e suas dimensões (em pontos). Aqui escolhemos um retângulo de 200 × 100 pt e aplicamos um preenchimento azul‑claro.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Dica profissional:* Se precisar que a forma alinhe com o texto existente, use `builder.move_to` antes de inserir, ou ajuste as propriedades `left`/`top` após a criação.

## Etapa 3: Ativar a Sombra

Uma forma sem sombra parece plana. Para **definir distância da sombra** e tornar o efeito visível, obtenha o formato da sombra e habilite‑o.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Por que esta etapa:* O formato da sombra é um objeto separado; alternar `visible` é a primeira coisa que você deve fazer, caso contrário todas as outras propriedades da sombra são ignoradas.

## Etapa 4: Estilizar a Sombra – Cor, Desfoque, Distância, Direção

É aqui que a mágica acontece. Vamos **alterar a cor da sombra**, ajustar o raio de desfoque, definir quão longe a sombra fica do retângulo e girá‑la 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Explicação de cada propriedade:*

| Propriedade | O que faz | Valores típicos |
|-------------|-----------|-----------------|
| `style` | Determina se a sombra é *interna* ou *externa*. | `OUTER` (mais comum) |
| `blur_radius` | Controla a suavidade; maior = bordas mais desfocadas. | 0–20 px é usual |
| `distance` | Quão longe a sombra está deslocada da forma. | 0–10 pt para sutil, >10 para dramático |
| `direction` | Ângulo da fonte de luz, medido no sentido horário a partir do eixo x. | 0‑360° |
| `color` | Matiz da sombra. | Qualquer `aw.Color` (ex.: `gray`, `dark_red`) |

*Caso extremo:* Se você definir `distance` como `0`, a sombra ficará diretamente sob a forma, ocultando efetivamente o preenchimento da forma. Mantenha acima de `0` para um deslocamento visível.

## Etapa 5: Salvar o Documento como PDF

Finalmente, nós **salvar documento como pdf**. Aspose.Words rasteriza automaticamente a sombra, de modo que o PDF fica exatamente como a visualização no Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Por que PDF?* PDFs preservam o layout em diferentes plataformas, tornando‑os perfeitos para relatórios, faturas ou qualquer artefato imprimível.

---

![Criar forma retangular com sombra](https://example.com/images/rectangle-shadow.png){: .align-center alt="exemplo de criação de forma retangular com sombra"}

*A imagem acima mostra a saída final em PDF – um retângulo azul‑claro com uma sombra externa cinza suave, exatamente como configuramos.*

## Perguntas Frequentes & Variações

### E se eu precisar de uma sombra **transparente**?

Defina o canal alfa na cor da sombra:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Posso aplicar a mesma sombra a várias formas?

Sim. Extraia o `ShadowFormat` de uma forma e atribua‑o a outra:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Como mudar a sombra para um **tipo de forma diferente**?

Todos os tipos de forma compartilham as mesmas propriedades `ShadowFormat`, então você pode reutilizar o mesmo bloco de configuração — basta substituir `ShapeType.RECTANGLE` por `ShapeType.OVAL`, `ShapeType.TRIANGLE`, etc.

### E quanto a PDFs **de alta resolução** para impressão?

Especifique o `PdfSaveOptions` com um DPI mais alto:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Recapitulação

Cobrimos tudo o que você precisa para **criar forma retangular**, **como adicionar forma**, personalizar sua **cor da sombra**, **definir distância da sombra** e, finalmente, **salvar documento como pdf**. O script completo e executável fica assim:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Execute o script, abra o `ShadowedShape.pdf` resultante e você verá um retângulo nítido com uma sombra cinza sutil — exatamente o que se espera de um relatório formatado profissionalmente.

## O que fazer a seguir?

- **Explore outros tipos de forma** (`ShapeType.OVAL`, `ShapeType.LINE`) para enriquecer seus documentos.  
- **Combine múltiplas sombras** sobrepondo formas; você pode até criar um efeito de “brilho” usando uma sombra interna com uma cor vibrante.  
- **Automatize o processamento em lote**: percorra uma coleção de linhas de dados, gere uma forma por linha e mescle tudo em um único PDF.  
- **Integre com outras bibliotecas Aspose** (por exemplo, Aspose.Slides) se precisar exportar o mesmo visual para PowerPoint.

Sinta‑se à vontade para experimentar — altere o `blur_radius`, brinque com `direction` ou troque `gray` por um tom específico da sua marca. A API é flexível o suficiente para que alguns ajustes mudem drasticamente o impacto visual.

Tem dúvidas ou um cenário complicado? Deixe um comentário abaixo ou participe dos fóruns da comunidade Aspose. Boa codificação e aproveite esses retângulos belamente sombreados!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}