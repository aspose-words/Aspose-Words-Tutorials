---
category: general
date: 2026-06-24
description: Crie uma forma retangular em Python com Aspose.Words, aprenda como adicionar
  sombra à forma, definir o ângulo da sombra e salvar o documento como PDF em minutos.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: pt
og_description: Crie uma forma retangular em Python, adicione sombra à forma, defina
  o ângulo da sombra e salve o documento como PDF com Aspose.Words. Siga este guia
  passo a passo.
og_title: Criar Forma de Retângulo em Python – Tutorial Completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Criar Forma de Retângulo em Python – Guia Completo do Aspose.Words
url: /pt/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Forma Retangular em Python – Guia Completo do Aspose.Words

Já se perguntou como **create rectangle shape** em um documento Word usando Python? Talvez você precise de uma caixa de destaque em negrito, um indicativo visual para um diagrama, ou simplesmente um retângulo elegante para um relatório. Seja qual for o caso, você chegou ao lugar certo. Neste tutorial vamos percorrer todo o processo — desde inserir o retângulo, adicionar uma sombra sutil, ajustar o ângulo da sombra e, finalmente, **save document as PDF** para que você possa compartilhá‑lo com qualquer pessoa.

Usaremos **Aspose.Words for Python via .NET**, uma biblioteca poderosa que permite manipular arquivos Word sem precisar abrir o próprio Word. Ao final deste guia você será capaz de responder à pergunta *“how to add shape shadow”* com confiança, e terá um script pronto‑para‑executar que pode ser inserido em qualquer projeto.

---

## O que você precisará

Antes de mergulharmos, certifique‑se de que tem o seguinte:

- **Python 3.8+** instalado na sua máquina.  
- **Aspose.Words for Python via .NET** (pacote `aspose-words`). Instale‑lo com:

  ```bash
  pip install aspose-words
  ```

- Uma pasta gravável onde o PDF gerado será salvo.  
- (Opcional) Uma IDE ou editor de texto — VS Code funciona muito bem.

É só isso. Sem DLLs extras, sem instalação do Office, apenas um único pacote pip.

---

## Etapa 1: Configurar o Documento e o Builder

A primeira coisa que você precisa fazer é **create rectangle shape**‑friendly objects: um `Document` e um `DocumentBuilder`. Pense no builder como sua caneta; ele desenha tudo para você.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Por que isso importa:** O objeto `Document` representa o arquivo .docx completo, enquanto o `DocumentBuilder` fornece métodos como `insert_shape` que tornam o desenho de formas muito fácil.

---

## Etapa 2: Inserir a Forma Retangular

Agora que temos um builder, podemos finalmente **create rectangle shape**. O método `insert_shape` precisa de três argumentos: o tipo de forma, a largura e a altura. Usaremos 200 pt de largura e 100 pt de altura para uma proporção agradável.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Neste ponto você **create rectangle shape** com sucesso no seu documento. Se você abrir o DOCX gerado (faremos isso mais adiante), verá um retângulo simples onde o cursor estava.

---

## Etapa 3: Acessar o Objeto de Formatação da Sombra

Para **add shadow to shape**, primeiro precisamos obter a formatação de sombra da forma. Cada forma em Aspose.Words possui a propriedade `shadow_format` que expõe todas as configurações relacionadas à sombra.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Ter a referência `shadow` nos permite alternar visibilidade, desfoque, distância, ângulo, cor e transparência — tudo em poucas linhas de código.

---

## Etapa 4: Habilitar a Sombra e Configurar sua Aparência

É aqui que a mágica acontece. Vamos **add shadow to shape**, deixá‑la levemente desfocada, deslocá‑la um pouco, definir a direção (a parte **set shadow angle**), e dar a ela um tom preto semitransparente.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Dica profissional:** Se precisar de um efeito mais dramático, aumente `blur_radius` ou diminua `transparency`. Por outro lado, uma sombra nítida e totalmente opaca pode ser obtida com `blur_radius = 0` e `transparency = 0`.

---

## Etapa 5: Salvar o Documento como PDF

Nós **create rectangle shape**, nós **add shadow to shape**, e agora vamos **save document as PDF** para que o resultado fique idêntico em qualquer dispositivo. Aspose.Words faz isso em uma única linha.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Executar o script gerará `shadowed_rectangle.pdf` na pasta `output`. Abra‑o com qualquer visualizador de PDF e você verá um retângulo limpo com uma sombra suave de 45 graus — exatamente como configuramos.

---

## Exemplo Completo Funcionando

Abaixo está o script completo, pronto‑para‑executar, que combina todas as etapas acima. Copie‑e cole em um arquivo chamado `create_rectangle_with_shadow.py` e execute `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Saída esperada:** Um arquivo PDF mostrando um único retângulo com uma sombra diagonal suave. Sem páginas extras, sem artefatos ocultos — apenas a forma que criamos.

---

## Perguntas Frequentes & Casos de Borda

### E se eu precisar de uma forma diferente?

Aspose.Words suporta muitos valores de `ShapeType` (elipse, estrela, chamada, etc.). Basta substituir `aw.drawing.ShapeType.RECTANGLE` pelo enum desejado, como `aw.drawing.ShapeType.ELLIPSE`.

### Posso adicionar várias sombras?

A API expõe apenas um `ShadowFormat` por forma, mas você pode simular múltiplas sombras duplicando a forma, deslocando cada cópia e ajustando a transparência.

### Como mudar a cor da sombra para combinar com a minha marca?

Basta definir `shadow.color` para qualquer `aw.drawing.Color`. Para um azul da marca, use `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### E quanto a salvar como DOCX em vez de PDF?

Substitua `document.save(pdf_path)` por `document.save("output/shadowed_rectangle.docx")`. A renderização da sombra é preservada em ambos os formatos.

### A sombra funciona em visualizadores de PDF mais antigos?

Aspose.Words renderiza a sombra como um efeito vetorial, amplamente suportado. Contudo, visualizadores muito antigos podem achatar o efeito; testar nos dispositivos do seu público‑alvo é sempre uma boa prática.

---

## Dicas para Polir seu PDF

- **Adicionar borda:** `rectangle.line_format.width = 1.5` e definir uma cor para um contorno nítido.  
- **Centralizar o retângulo:** Use `builder.move_to_document_start()` antes de inserir, então `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combinar com texto:** Insira um `TextFragment` após o retângulo para rotulá‑lo, por exemplo, `"Seção Importante"`.

Esses pequenos ajustes podem transformar um retângulo simples em uma caixa de destaque polida que parece profissional em relatórios, propostas ou e‑books.

---

## Conclusão

Agora você tem uma receita sólida, de ponta a ponta, para **create rectangle shape** em Python, **add shadow to shape**, **set shadow angle**, e **save document as PDF** usando Aspose.Words. As etapas são diretas, o código é totalmente autocontido, e você viu por que cada linha importa — desde a inicialização do documento até o polimento do PDF final.

A seguir, você pode explorar **how to add shape shadow** a desenhos mais complexos, experimentar preenchimentos gradientes, ou gerar tabelas dentro das suas formas. A biblioteca também suporta vincular formas a marcadores, o que pode ser útil para PDFs interativos.

Tentou alguma variação? Compartilhe nos comentários, ou mande suas dúvidas restantes. Boa codificação, e aproveite para dar mais profundidade aos seus documentos!

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## O que Você Deve Aprender a Seguir?

Os tutoriais abaixo abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}