---
category: general
date: 2026-02-26
description: Crie uma forma retangular no Word usando Aspose.Words e aprenda a adicionar
  a forma ao Word, aplicar sombra à forma e definir a transparência da forma em minutos.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: pt
og_description: Crie uma forma retangular no Word usando Aspose.Words. Aprenda a adicionar
  forma ao Word, aplicar sombra à forma e definir a transparência da forma rapidamente.
og_title: Criar Forma de Retângulo no Word – Guia Completo do Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Criar Forma de Retângulo no Word – Guia Completo do Aspose.Words
url: /pt/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Forma Retangular no Word – Guia Completo do Aspose.Words

Já precisou **criar forma retangular** em um documento Word mas não sabia por onde começar? Você não está sozinho—muitos desenvolvedores encontram essa barreira ao automatizar relatórios ou faturas. Neste tutorial vamos percorrer um exemplo completo, pronto‑para‑executar, que mostra como **adicionar forma ao Word**, aplicar uma sombra sutil e controlar a transparência da forma, tudo com Aspose.Words for .NET.

Ao final do guia você terá um arquivo `.docx` contendo um retângulo limpo com uma sombra polida—perfeito para branding, chamadas de atenção ou simplesmente para deixar seu documento um pouco mais profissional. Nenhuma ferramenta externa necessária, apenas algumas linhas de C#.

## O que você vai precisar

- **Aspose.Words for .NET** (a versão mais recente até o início de 2026). Você pode obtê‑la via NuGet (`Install-Package Aspose.Words`).
- Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou VS Code com a extensão C#).
- Familiaridade básica com a sintaxe C#—nada de especial, apenas as declarações `using` habituais e a criação de objetos.

Se já tem tudo isso, ótimo—vamos começar.

## Criar Forma Retangular – Passos Principais

Abaixo está o código‑fonte completo. Copie‑e‑cole em um novo projeto de console, pressione **F5** e você verá `ShadowDemo.docx` aparecer na pasta que especificar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Por que isso funciona

- **`Document`** é o ponto de entrada; representa todo o arquivo Word.
- **`Shape`** com `ShapeType.Rectangle` indica ao Aspose que queremos um objeto de desenho retangular.
- Definir **`Width`** e **`Height`** dá à forma um tamanho determinístico; caso contrário ela usa um placeholder minúsculo.
- O objeto **`Shadow`** permite ajustar cada aspecto visual: desfoque, distância, direção, cor, transparência e espalhamento. Esse é o coração de *apply shadow to shape*.
- Por fim, **`AppendChild`** insere a forma no primeiro parágrafo do documento, que é a maneira mais simples de *add shape to Word* sem lidar com tabelas ou cabeçalhos.

Quando você abrir `ShadowDemo.docx`, verá um retângulo cinza posicionado confortavelmente no documento, com sua sombra inclinada para baixo‑direita em um ângulo de 45°. A sombra não é um bloco sólido; o raio de desfoque suaviza as bordas, e a transparência a faz parecer uma sombra natural em vez de uma sobreposição dura.

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(A imagem acima mostra o resultado final do trecho de código.)*

## Adicionar Forma ao Documento Word – Opções de Posicionamento

O exemplo usa o **primeiro parágrafo** porque é a forma mais rápida de ver algo na tela. Em cenários reais você pode querer:

- Inserir a forma em uma **seção** ou **cabeçalho/rodapé** específicos.
- Colocá‑la dentro de uma **célula de tabela** para alinhamento com dados tabulares.
- Envolvê‑la com opções de **quebra de texto** (por exemplo, `WrapType.Square`) para que o texto ao redor flua ao redor do retângulo.

Aqui está uma variação rápida que coloca a forma em um novo parágrafo com um estilo personalizado:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Dica profissional:* Sempre adicione a forma **depois** de configurar suas propriedades; caso contrário pode ser necessário chamar `UpdateLayout` para atualizar a aparência visual.

## Aplicar Sombra à Forma – Ajustando o Visual

Sombras podem mudar drasticamente a estética de um documento. A classe `Shadow` expõe várias propriedades:

| Property      | O que controla                                     | Valores típicos |
|---------------|----------------------------------------------------|-----------------|
| `BlurRadius`  | Suavidade das bordas da sombra                     | 2.0 – 10.0      |
| `Distance`    | Quão longe a sombra está deslocada da forma        | 1.0 – 8.0       |
| `Direction`   | Ângulo em graus (0 = esquerda, 90 = cima)          | 0 – 360         |
| `Color`       | Cor da sombra (qualquer `System.Drawing.Color`)   | Gray, Black, Custom |
| `Transparency`| Opacidade (0 = totalmente opaco, 1 = invisível)   | 0.0 – 0.5       |
| `Spread`      | Expansão da sombra antes de aplicar o desfoque    | 0.0 – 1.0       |

Se você deseja um **visual sutil e profissional**, mantenha `BlurRadius` entre 4‑6 e `Transparency` perto de 0.2, como no código acima. Para um **efeito dramático**, aumente `Distance` para 6, defina `Direction` em 135° e reduza `Transparency` para 0.05.

## Definir Transparência da Forma e Espalhamento da Sombra

Transparência não se aplica apenas à sombra; você também pode tornar o próprio retângulo parcialmente translúcido:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Combinar um preenchimento semitransparente com uma sombra suave costuma gerar uma sensação de UI moderna—ótimo para dashboards ou mock‑ups de design incorporados em relatórios.

### Casos Limite a observar

1. **Versões antigas do Word** (pré‑2007) não suportam algumas propriedades de sombra. Se você direciona arquivos `.doc`, considere simplificar a sombra (por exemplo, definir `BlurRadius` como 0).
2. **Monitores de alta DPI** podem renderizar a sombra de forma ligeiramente diferente. Teste no ambiente alvo se a fidelidade visual for crítica.
3. **Formas sobrepostas**—Aspose renderiza sombras na ordem em que são adicionadas. Insira as formas de trás para frente para evitar oclusão indesejada.

## Salvar e Verificar o Resultado

O método `Document.Save` detecta automaticamente o formato de saída a partir da extensão do arquivo. Para um arquivo **`.docx`** você obtém o formato Open XML, que a maioria dos processadores Word modernos entende. Se precisar de uma versão **PDF** com o mesmo estilo visual, basta mudar a extensão:

```csharp
document.Save("ShadowDemo.pdf");
```

Abrir o `ShadowDemo.docx` (ou `ShadowDemo.pdf`) deve mostrar um **retângulo limpo com sombra**, confirmando que você conseguiu *create rectangle shape* e *apply shadow to shape* usando Aspose.Words.

## Perguntas Frequentes

**Q: Posso usar outra forma, como uma elipse?**  
A: Claro. Troque `ShapeType.Rectangle` por `ShapeType.Ellipse` (ou qualquer outro enum `ShapeType`). As propriedades de sombra permanecem as mesmas.

**Q: E se eu precisar que o retângulo seja clicável?**  
A: Você pode atribuir um hyperlink à forma:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Isso funciona no .NET 6+?**  
A: Sim. Aspose.Words 23.11 e posteriores suportam totalmente .NET 6, .NET 7 e .NET 8. Basta referenciar o pacote NuGet adequado.

**Q: Como mudar a cor da sombra para combinar com a minha marca?**  
A: Use qualquer `System.Drawing.Color` que desejar:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Conclusão

Cobrimos tudo o que você precisa para **criar forma retangular** em um documento Word, **adicionar forma ao Word**, **aplicar sombra à forma** e **definir transparência da forma**. O código completo e executável está no topo desta página, e as explicações devem dar confiança suficiente para ajustar tamanhos, cores e parâmetros de sombra em qualquer projeto.

Pronto para o próximo passo? Experimente:

- Várias formas sobrepostas para um efeito de selo.
- Dimensionamento dinâmico baseado no conteúdo do documento (por exemplo, calcular a largura a partir de uma coluna de tabela).
- Exportar o documento para PDF ou HTML preservando a sombra.

Sinta‑se à vontade para deixar um comentário se encontrar algum obstáculo, ou compartilhar suas próprias variações do tema “retângulo com sombra”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}