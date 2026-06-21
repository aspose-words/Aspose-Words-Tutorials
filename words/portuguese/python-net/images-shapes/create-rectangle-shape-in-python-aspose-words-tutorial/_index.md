---
category: general
date: 2026-06-21
description: Crie uma forma retangular em Python usando Aspose.Words. Aprenda como
  adicionar sombra à forma, definir a cor de preenchimento da forma e salvar o documento
  como PDF em minutos.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: pt
og_description: Crie uma forma retangular em Python com Aspose.Words. Este guia mostra
  como adicionar sombra à forma, definir a cor de preenchimento da forma e salvar
  o documento como PDF.
og_title: Criar forma retangular em Python – tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Criar forma retangular em Python – tutorial Aspose.Words
url: /pt/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular em Python – tutorial Aspose.Words

Já se perguntou **como criar uma forma retangular** em um documento Word enquanto você programa em Python? Você não é o único. Muitos desenvolvedores se deparam com um obstáculo quando precisam de um elemento visual rápido — como uma caixa colorida com uma sombra sutil — e então exportam tudo como PDF.  

Neste guia vamos percorrer um exemplo completo e executável que **cria forma retangular**, **define a cor de preenchimento da forma**, **adiciona sombra à forma** e, finalmente, **salva o documento como PDF**. Sem referências vagas, apenas código concreto que você pode copiar‑colar e executar hoje.

## O que você precisará

Antes de mergulharmos, certifique‑se de que tem o seguinte na sua máquina:

- Python 3.8 ou mais recente (a sintaxe que usamos funciona em qualquer versão recente).
- Uma licença ativa do Aspose.Words for Python ou um teste gratuito (a biblioteca é pura‑Python, sem necessidade de interop COM).
- Um editor de texto ou IDE com o qual se sinta confortável — VS Code funciona muito bem, mas qualquer um serve.

É só isso. Sem frameworks pesados, sem dependências adicionais ao nível do SO. Vamos começar.

## Etapa 1: Instalar Aspose.Words for Python

Primeiro as coisas básicas. Se ainda não o fez, obtenha o pacote do PyPI:

```bash
pip install aspose-words
```

Por que esta etapa importa: o Aspose.Words fornece as classes `Document` e `DocumentBuilder` nas quais nos basearemos. Sem a biblioteca, nenhuma das chamadas posteriores — como `insert_shape` — existirá, então o script falharia antes mesmo de desenhar uma linha.

> **Dica profissional:** Mantenha seu ambiente virtual organizado. Execute `python -m venv .venv && source .venv/bin/activate` antes de instalar, para que a biblioteca fique isolada dos pacotes do sistema.

## Etapa 2: Criar um Novo Document e um DocumentBuilder

Agora realmente **criamos forma retangular** – mas primeiro precisamos de uma tela em branco.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

O objeto `Document` representa todo o arquivo, enquanto `DocumentBuilder` é um ajudante prático que sabe onde o cursor está e pode inserir elementos naquele ponto. Pense no builder como uma caneta que escreve na página.

## Etapa 3: Inserir a Forma Retangular

É aqui que a ação principal acontece. Vamos **criar forma retangular** com largura e altura fixas, depois posicioná‑la na página.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Por que um retângulo? É a forma mais simples que ainda nos permite demonstrar cores de preenchimento e sombras. Se precisar de um círculo ou de uma estrela depois, basta trocar `ShapeType.RECTANGLE` por outro valor do enum.

## Etapa 4: Definir a Cor de Preenchimento da Forma

Uma caixa branca simples não é muito empolgante, então vamos **definir a cor de preenchimento da forma** para algo suave — azul claro funciona bem para relatórios.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Você pode usar qualquer um dos membros predefinidos de `aw.Color` (`red`, `green`, `dark_gray`, etc.) ou passar uma tupla RGB (`aw.Color.from_argb(255, 30, 144, 255)`). A cor de preenchimento é o que o usuário vê antes de qualquer sombra ou borda ser aplicada.

## Etapa 5: Adicionar Sombra à Forma

Agora para o acabamento visual: **adicionar sombra à forma**. Sombras dão profundidade e fazem o retângulo sobressair na página.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Como adicionar sombra**? O código acima faz exatamente isso, mas vamos detalhar por que cada propriedade importa:

- `visible` – alterna o efeito ligado/desligado.
- `color` – define o tom; um cinza escuro imita a iluminação natural.
- `blur` – valores maiores produzem bordas mais suaves.
- `offset_x` / `offset_y` – deslocam a sombra em relação à forma; ajuste esses valores para simular diferentes ângulos de luz.
- `transparency` – 0 é sólido, 1 é invisível; 0.2 gera uma impressão sutil.
- `type` – `OUTER` projeta a sombra fora da forma, enquanto `INNER` a inseriria dentro.

Se precisar de uma sombra dramática, aumente `blur` para 10‑15 e eleve `offset_x`/`offset_y` para 6‑8.

## Etapa 6: Salvar o Documento como PDF

Todo esse trabalho é inútil se não pudermos **salvar o documento como PDF** e compartilhá‑lo. O Aspose.Words faz isso em uma única linha:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Por que PDF? PDFs preservam o layout em todas as plataformas, tornando‑os ideais para relatórios, faturas ou qualquer material imprimível. O método `save` detecta automaticamente a extensão do arquivo e escolhe o formato correto — basta garantir que o caminho termine com `.pdf`.

### Resultado Esperado

Abra o `ShapeWithShadow.pdf` resultante e você deverá ver um retângulo azul‑claro centralizado próximo ao topo da primeira página, com uma sombra cinza‑escura suave deslocada levemente para a direita e para baixo. As bordas da forma são nítidas, a sombra é sutil, e o tamanho do arquivo costuma ficar abaixo de 100 KB.

## Bônus: Ajustando Sombras – Respostas a “como adicionar sombra”

Você pode estar se perguntando, *“Posso mudar a direção da sombra sem mover a forma?”* Absolutamente. A posição da sombra é independente das coordenadas da forma; basta ajustar `offset_x` e `offset_y`. Valores positivos movem a sombra para a direita/para baixo, valores negativos movem para a esquerda/para cima. Para uma fonte de luz no canto superior esquerdo, use `offset_x = -3` e `offset_y = -3`.

Outra pergunta frequente: *“E se eu precisar de várias sombras na mesma forma?”* O Aspose.Words suporta apenas uma sombra por forma. Se precisar de efeitos em camadas, crie uma forma duplicada, deslocando‑a levemente, e aplique sombras diferentes a cada uma. É um pequeno truque, mas funciona.

## Script Completo – Pronto para Executar

Abaixo está o script completo e autocontido. Copie‑o para um arquivo chamado `create_rectangle_with_shadow.py` e execute‑o com `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Observação:** Substitua `YOUR_DIRECTORY` por um caminho absoluto ou relativo que exista na sua máquina. Se a pasta não existir, o Python lançará um `FileNotFoundError`.

## Problemas Comuns & Como Evitá‑los

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| Sombra não aparece | `shadow.visible` deixado no padrão `False` | Certifique‑se de que `shadow.visible = True` |
| Forma invisível | Cor de preenchimento definida como `aw.Color.transparent` ou `None` | Use uma cor sólida como `aw.Color.light_blue` |
| PDF está vazio | Esqueceu de chamar `doc.save` ou salvou com extensão errada | Chame `doc.save("output.pdf")` e verifique o caminho |
| Erro de tempo de execução `ImportError` | Aspose.Words não está instalado ou o ambiente Python está errado | Execute `pip install aspose-words` dentro do venv ativo |

## Próximos Passos – Explore Mais Formas e Formatação

Agora que você dominou **criar forma retangular**, pode:

- Substituir `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE` ou `ShapeType.PENTAGON` para experimentar outras geometrías.
- Adicionar texto dentro da forma usando `builder.move_to(rectangle.absolute_position)` e então `builder.writeln("Hello World")`.
- Combinar múltiplas formas em um grupo com `group = aw.drawing.GroupShape(doc)` para diagramas complexos.
- Exportar para outros formatos como DOCX (`doc.save("output.docx")`) ou HTML (`doc.save("output.html")`) para ver como a sombra se traduz.

Cada uma dessas extensões se baseia nos mesmos conceitos centrais: **adicionar sombra à forma**, **definir a cor de preenchimento da forma** e **salvar o documento como PDF** (ou outro formato).

---

### Pré‑visualização da Imagem *(opcional)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*A captura de tela mostra o resultado final em PDF com um retângulo azul‑claro e uma sombra externa sutil.*

---

## Conclusão

Percorremos cada passo necessário para **criar forma retangular** em Python, aplicar um preenchimento personalizado, **adicionar sombra à forma** e, finalmente, **salvar o documento como PDF**. O código está totalmente executável, as explicações cobrem o *porquê* de cada propriedade, e abordamos casos de borda comuns e próximos passos.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word Java – Adicionar forma retangular com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial de sombra de forma Aspose.Words – Adicionar sombra a forma Word em C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}