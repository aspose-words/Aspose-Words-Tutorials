---
category: general
date: 2026-06-05
description: Exemplo de criação de documento Word em Python que mostra como adicionar
  sombra a uma forma, aplicando efeito de sombra no Word com Aspose.Words.
draft: false
keywords:
- create word document python
- how to add shadow
- add shadow to shape
- apply shadow effect word
- insert shape with shadow
language: pt
og_description: O tutorial de criação de documento Word em Python orienta você a adicionar
  uma sombra a uma forma, aplicando um efeito de sombra no Word usando Aspose.Words.
og_title: Criar documento Word em Python – Adicionar sombra à forma
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Create Word document Python example shows how to add shadow to a shape,
    applying shadow effect in Word with Aspose.Words.
  headline: Create Word Document Python – Add Shadow to Shape Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Use `builder.insert_image(...)` to place an image, then access
      `image_shape.shadow_format` just like we did with the rectangle.
    question: Can I add a shadow to a picture instead of a shape?
  - answer: Yes. Aspose.Words preserves shape effects during conversion, so the PDF
      will retain the shadow.
    question: Does the shadow survive when I convert the document to PDF?
  - answer: Call `builder.insert_shape` for each shape, then configure each shape’s
      `shadow_format` independently. No shared state.
    question: What if I need multiple shapes with different shadows?
  - answer: 'Minimal for typical documents. If you’re generating thousands of shapes,
      consider batch processing or limiting blur radius to keep rendering fast. ##
      Conclusion We’ve just demonstrated how to **create Word document python** code
      that inserts a rectangle and **adds shadow to shape** using Aspose.Word'
    question: Is there a performance impact when adding many shadows?
  type: FAQPage
tags:
- python
- aspose-words
- document automation
title: Criar documento Word em Python – Guia para adicionar sombra a forma
url: /pt/python/images-shapes/create-word-document-python-add-shadow-to-shape-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Word Document Python – Guia de Adição de Sombra a Forma

Já se perguntou como **create Word document python** código que não só insere uma forma, mas também lhe dá uma sombra elegante? Você não está sozinho. Em muitos relatórios, faturas ou folhetos de marketing, uma sombra sutil pode fazer um retângulo parecer que está se levantando da página, adicionando profundidade sem gráficos extras.

Neste tutorial, percorreremos um exemplo completo e executável que mostra exatamente **how to add shadow** a uma forma usando Aspose.Words for Python. Ao final, você terá um arquivo `.docx` com um retângulo que projeta uma sombra suave de 45 graus — perfeito para deixar seus documentos com aparência polida e profissional.

## O que este Guia Cobre

Começaremos configurando o ambiente, depois criaremos um novo documento Word, inseriremos um retângulo, configuraremos suas propriedades de sombra e, finalmente, salvaremos o arquivo. Ao longo do caminho, discutiremos por que cada configuração é importante, armadilhas comuns e algumas dicas extras que você pode experimentar. Nenhuma referência externa é necessária; tudo o que você precisa está aqui.

**Pré-requisitos**

- Python 3.8+ instalado  
- pacote `aspose-words` (`pip install aspose-words`)  
- Familiaridade básica com a sintaxe Python (se você já escreveu um “Hello, World!” antes, está pronto)

Pronto? Vamos mergulhar.

## Etapa 1: Inicializar o Documento – Conceitos Básicos de **Create Word Document Python**

A primeira coisa que você precisa é um objeto de documento em branco e um `DocumentBuilder` que permite adicionar conteúdo. Pense no builder como uma caneta que escreve no arquivo Word.

```python
import aspose.words as aw

# Create a new, empty Word document
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add elements
builder = aw.DocumentBuilder(doc)
```

*Por que isso importa:* `aw.Document()` é o ponto de entrada para qualquer operação do Aspose.Words. Sem ele, você não pode adicionar formas, texto ou qualquer outro elemento. O builder mantém uma referência ao documento, então você não precisa passar o documento manualmente.

## Etapa 2: Inserir um Retângulo – Usando a Lógica **Insert Shape With Shadow**

Agora vamos colocar um retângulo na página. As dimensões estão em pontos (1 pt ≈ 1/72 polegada), então 150 × 100 pts resultam em uma caixa bem proporcionada.

```python
# Insert a rectangle shape of 150x100 points
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
```

*Dica de especialista:* Se precisar de uma forma diferente, basta trocar `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`, `ShapeType.CLOUD`, etc. O mesmo código de configuração de sombra funciona para qualquer forma que você escolher.

## Etapa 3: Aplicar Efeito de Sombra – **How To Add Shadow** Precisamente

É aqui que a mágica acontece. O objeto `shadow_format` controla visibilidade, distância, desfoque, ângulo, cor e transparência. Ajuste cada propriedade para obter o visual desejado.

```python
# Grab the shadow formatting object
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set how far the shadow sits from the shape (in points)
shadow.distance = 5.0

# Blur radius controls softness; higher = fuzzier edges
shadow.blur = 3.0

# Angle determines the light source direction (degrees clockwise from the x‑axis)
shadow.angle = 45

# Choose a color – black works for most professional documents
shadow.color = aw.drawing.Color.black

# Transparency is a float from 0 (opaque) to 1 (fully transparent)
shadow.transparency = 0.4   # 40 % transparent gives a subtle effect
```

**Por que cada configuração é importante**

| Property | Uso Típico | Impacto Visual |
|----------|------------|-----------------|
| `visible` | Ativa/desativa o efeito | Nenhuma sombra se `False` |
| `distance` | Controla o deslocamento da forma | Valores maiores afastam mais a sombra |
| `blur` | Suaviza as bordas | Blur maior = sombra mais difusa |
| `angle` | Simula a direção da luz | 0° = sombra à direita, 90° = abaixo |
| `color` | Combina com a identidade visual ou tema | Sombras brancas raramente fazem sentido |
| `transparency` | Ajusta a opacidade | 0.0 = sólido, 0.8 = quase imperceptível |

*Armadilha comum:* Esquecer de definir `shadow.visible = True` resulta em uma forma perfeitamente correta, mas sem sombra — fácil de passar despercebido quando você está focado na cor ou tamanho.

## Etapa 4: Salvar o Documento – Etapa Final de **Create Word Document Python**

Depois de configurar a forma, basta gravar o documento no disco. Você pode escolher qualquer formato suportado (`.docx`, `.pdf`, `.html`, etc.). Para este guia, usaremos o clássico `.docx`.

```python
# Save the document to the desired location
output_path = "shadowed_shape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Quando você abrir `shadowed_shape.docx` no Microsoft Word (ou qualquer visualizador compatível), verá um retângulo com uma sombra nítida de 45 graus — exatamente o que o código acima descreve.

### Resultado Esperado

- Um arquivo Word de uma única página.
- Um retângulo centralizado onde o builder foi posicionado.
- Uma sombra preta semitransparente deslocada 5 pts, desfocada em 3 pts, projetada em um ângulo de 45°.

Se você não vir a sombra, verifique novamente se `shadow.visible` está `True` e se está usando um visualizador que respeita os efeitos de forma (a maioria das versões modernas do Word faz isso).

## Bônus: Ajustando a Sombra para Diferentes Estilos

Você pode querer um visual mais suave para um relatório corporativo, ou uma sombra ousada e colorida para um folheto de marketing. Aqui estão algumas variações rápidas:

```python
# Soft gray shadow for subtle emphasis
shadow.color = aw.drawing.Color.gray
shadow.transparency = 0.6
shadow.blur = 5.0
shadow.distance = 3.0

# Red, dramatic shadow for a creative brochure
shadow.color = aw.drawing.Color.red
shadow.transparency = 0.2
shadow.blur = 2.0
shadow.angle = 120
```

Experimentar com esses valores é a melhor maneira de entender como **add shadow to shape** funciona na prática.

## Pré‑visualização Visual (Texto Alternativo Incluído)

![Retângulo sombreado em um documento Word – exemplo create word document python](/images/shadowed_rectangle.png)

*Texto alternativo:* *Retângulo sombreado em um documento Word – exemplo create word document python.*

## Perguntas Frequentes

**Q: Posso adicionar uma sombra a uma imagem em vez de uma forma?**  
A: Absolutamente. Use `builder.insert_image(...)` para inserir uma imagem, então acesse `image_shape.shadow_format` da mesma forma que fizemos com o retângulo.

**Q: A sombra permanece quando eu converto o documento para PDF?**  
A: Sim. Aspose.Words preserva os efeitos de forma durante a conversão, então o PDF manterá a sombra.

**Q: E se eu precisar de várias formas com sombras diferentes?**  
A: Chame `builder.insert_shape` para cada forma, então configure o `shadow_format` de cada forma independentemente. Sem estado compartilhado.

**Q: Existe impacto de desempenho ao adicionar muitas sombras?**  
A: Mínimo para documentos típicos. Se você estiver gerando milhares de formas, considere processamento em lote ou limitar o raio de desfoque para manter a renderização rápida.

## Conclusão

Acabamos de demonstrar como o código **create Word document python** insere um retângulo e **adds shadow to shape** usando Aspose.Words. Ao configurar `shadow_format`, você pode **apply shadow effect word** documentos com controle detalhado sobre distância, desfoque, ângulo, cor e transparência. O mesmo padrão funciona para qualquer forma, imagem ou até caixa de texto, oferecendo uma caixa de ferramentas versátil para documentos com aparência profissional.

Qual o próximo passo? Experimente combinar várias formas, sobrepor texto, ou exportar para PDF para ver a sombra sobreviver à conversão. Você também pode explorar outros efeitos visuais como brilho ou reflexão — basta substituir `shadow_format` por `glow_format` ou `reflection_format`.

Feliz codificação, e que seus documentos tenham sempre essa profundidade extra!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar Documento Word em Branco com Forma Retângulo Sombreada – Guia Passo a Passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Criar forma retângulo no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}