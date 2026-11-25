---
category: general
date: 2026-11-25
description: Adicionar sombra a uma forma em um documento Word com Python. Aprenda
  como inserir uma forma retangular no Word e aplicar uma sombra transparente usando
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: pt
lastmod: 2026-11-25
og_description: Adicione sombra a uma forma em um documento Word usando Python. Este
  tutorial mostra como inserir uma forma retangular no Word e definir uma sombra com
  30 % de transparência usando Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Adicionar sombra a uma forma em um documento Word com Python – guia passo
  a passo
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Como adicionar sombra a uma forma em um documento Word usando Python
url: /pt/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar sombra a uma forma em um documento Word usando Python

Se você precisar **adicionar sombra a uma forma** em um documento Word, este guia mostra uma solução completa e executável. Você verá como criar um arquivo Word, inserir uma forma retangular e aplicar uma sombra transparente de 30 % — tudo com a biblioteca Aspose.Words for Python.

Trabalhar com documentos Word programaticamente evita formatação manual e permite gerar relatórios, contratos ou folhetos de marketing em escala. Ao final deste tutorial, você será capaz de responder “**how to create Word document python**” com um exemplo de código pronto‑para‑executar.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.8 ou mais recente instalado.
* Uma licença ativa do Aspose.Words for Python (a avaliação gratuita funciona para avaliação).
* Pacote `aspose-words` instalado via `pip install aspose-words`.
* Uma pasta onde o arquivo de saída pode ser gravado (substitua `YOUR_DIRECTORY` no código).

Nenhuma dependência adicional é necessária.

## Etapa 1: Criar um novo documento Word

O primeiro passo é instanciar um objeto `Document`. Esse objeto representa todo o arquivo .docx na memória.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` funciona como um cursor virtual. Quando você chama seus métodos, a biblioteca insere os elementos correspondentes na posição atual do cursor.

## Etapa 2: Inserir forma retangular no Word

Em seguida, você **insere uma forma retangular** usando o método `insert_shape` do builder. O método requer o tipo de forma e seu tamanho em pontos (1 ponto = 1/72 polegada).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Você pode alterar as dimensões para corresponder ao seu design. O retângulo torna‑se parte da camada de desenho do documento, o que significa que você pode modificar posteriormente seu preenchimento, contorno ou sombra.

## Etapa 3: Acessar o formato de sombra da forma

Todo objeto de desenho expõe a propriedade `shadow_format` que controla a aparência da sombra. Recupere‑a para que você possa ajustar transparência, deslocamento, desfoque e cor.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Neste ponto, a forma tem a sombra padrão (nenhuma sombra). O objeto `ShadowFormat` contém todos os parâmetros necessários para criar um efeito realista.

## Etapa 4: Tornar a sombra 30 % transparente

A transparência é expressa como um valor entre `0` (totalmente opaco) e `1` (totalmente transparente). Definir como `0.3` produz uma sombra 30 % transparente, o que costuma ser suficiente para adicionar profundidade sem sobrecarregar o texto.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Essas propriedades adicionais não são obrigatórias, mas ilustram como você pode ajustar finamente o efeito. O sinalizador `visible` é essencial; se você esquecê‑lo, a sombra não aparecerá mesmo que as demais configurações estejam definidas.

## Etapa 5: Salvar o documento para visualizar o resultado

Finalmente, grave o documento no disco. Abrir o arquivo `.docx` resultante no Microsoft Word ou em qualquer visualizador compatível mostra o retângulo com a sombra transparente aplicada.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Ao abrir `output.docx`, você verá um retângulo simples com uma sombra cinza sutil deslocada para a parte inferior‑direita. A transparência de 30 % da sombra faz a forma parecer elevada da página.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Exemplo de adição de sombra a forma em um documento Word criado com Python"}

## Script completo e executável

Juntando todas as peças, você obtém um script autônomo que pode copiar, colar e executar imediatamente.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Saída esperada:** Ao abrir o `output.docx` gerado, será exibida uma única página com um retângulo que projeta uma sombra leve e semi‑transparente. Nenhuma formatação adicional é necessária.

## Variações comuns e casos de borda

| Situação | Como adaptar o código |
|-----------|-----------------------|
| **Tipo de forma diferente** (por exemplo, elipse) | Altere `aw.drawing.ShapeType.RECTANGLE` para `aw.drawing.ShapeType.ELLIPSE`. |
| **Cor de sombra personalizada** | Defina `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` para uma sombra avermelhada. |
| **Múltiplas formas** | Chame `builder.insert_shape` repetidamente; cada chamada retorna um objeto `Shape` separado que você pode estilizar independentemente. |
| **Salvar como PDF** | Substitua `doc.save(output_path)` por `doc.save(output_path.replace('.docx', '.pdf'))` e use a extensão `.pdf`. |
| **Executar sem licença** | A avaliação gratuita adiciona uma marca d'água à primeira página. Adquira uma licença para removê‑la em uso de produção. |

Essas variações demonstram que o mesmo padrão — criar um documento, inserir uma forma, ajustar `shadow_format`, salvar — cobre a maioria dos cenários de automação.

## Dicas e boas práticas

* **Reutilizar o builder**: Mantenha uma única instância de `DocumentBuilder` para todo o documento para evitar a criação desnecessária de objetos.
* **Liberar recursos**: Em serviços de longa duração, chame `doc.dispose()` após salvar para liberar memória nativa.
* **Validar a saída**: Use `doc.validate(aw.ValidationType.FULL_VALIDATION)` antes de salvar se precisar garantir a conformidade com o padrão Open XML.
* **Compatibilidade de versão**: O código funciona com Aspose.Words for Python ≥ 22.9. Certifique‑se de que seu pacote está atualizado com `pip install --upgrade aspose-words`.

## Conclusão

Agora você sabe como **adicionar sombra a uma forma** em um documento Word usando Python. Seguindo as cinco etapas — criar um documento, **inserir forma retangular**, configurar a sombra e salvar — você pode automatizar a geração de documentos bem formatados para relatórios, faturas ou materiais de marketing.  

A partir daqui, você pode explorar outras opções de formatação, como preenchimentos em degradê, ajuste de texto ou conversão do documento para PDF. Cada um desses tópicos se baseia nos mesmos conceitos de `DocumentBuilder` e formatação de formas apresentados neste tutorial.

Boa codificação e aproveite a profundidade visual que uma sombra simples pode trazer aos seus documentos Word automatizados!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar forma retangular em um documento Word usando Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Adicionar sombra a forma em Python – Tutorial completo Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Criar documento Word em branco e adicionar sombra a forma – Guia completo Python](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}