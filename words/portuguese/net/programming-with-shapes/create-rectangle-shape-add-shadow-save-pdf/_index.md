---
category: general
date: 2026-02-24
description: Crie uma forma retangular em C# usando Aspose.Words, adicione sombra
  à forma e salve o documento como PDF. Aprenda como adicionar sombra e como salvar
  PDF em minutos.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: pt
og_description: Crie uma forma retangular em C# com Aspose.Words, adicione sombra
  à forma e salve o documento como PDF – um guia completo, passo a passo.
og_title: Criar forma retangular, adicionar sombra e salvar PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Criar forma retangular, adicionar sombra e salvar PDF
url: /pt/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular, adicionar sombra e salvar como PDF

Já precisou **criar forma retangular** em um documento Word, mas também queria uma sombra suave e uma saída em PDF? Você não está sozinho. Em muitos projetos de relatórios ou geração de faturas, o acabamento visual — como uma sombra sutil — faz a diferença entre “apenas mais um arquivo” e “documento de nível profissional.”  

Neste tutorial, vamos percorrer exatamente isso: usando **Aspose.Words for .NET** para criar uma forma retangular, adicionar sombra à forma e, finalmente, **salvar o documento como PDF**. Ao final, você terá um aplicativo console C# pronto‑para‑executar que produz um PDF com um retângulo sombreado, e entenderá como ajustar a sombra ou alterar as opções de exportação.

## O que você precisará

- .NET 6 SDK (ou qualquer versão recente do .NET) – a API funciona da mesma forma no .NET Framework 4.x também.  
- Pacote NuGet Aspose.Words for .NET (`Aspose.Words`) – instale‑o com `dotnet add package Aspose.Words`.  
- Um editor de código – Visual Studio, VS Code ou Rider serve.  

Nenhum passo extra de licenciamento para este exemplo; o modo de avaliação gratuito é suficiente para visualizar a saída em PDF.

## Etapa 1: Configurar o projeto e importar namespaces

Primeiro de tudo, vamos criar um projeto console e trazer as classes de que precisaremos.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Por que isso importa:* `Document` e `DocumentBuilder` nos dão a tela, enquanto `Shape` e `ShadowFormat` nos permitem desenhar e estilizar o retângulo. Importá‑los antecipadamente mantém o código posterior organizado.

## Etapa 2: **Criar forma retangular** com as dimensões desejadas

Agora realmente criamos um documento em branco e inserimos um retângulo. Observe como o método `InsertShape` retorna um objeto `Shape` que podemos estilizar imediatamente.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Explicação*: O tamanho é expresso em pontos (1 pt = 1/72 pol). Ajuste os números para se adequar ao seu layout. Também damos à forma um preenchimento azul‑claro para que a sombra se destaque.

## Etapa 3: **Adicionar sombra à forma** – ajuste fino do efeito

Uma sombra não é apenas “ligada/desligada”. Você pode controlar sua cor, desfoque, distância, direção e até transparência. Aqui está uma configuração prática que funciona bem para a maioria dos relatórios.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Por que você pode mudar esses valores:*  
- **BlurRadius** – aumente para um efeito sonhador, diminua para uma borda nítida.  
- **Direction** – 0° aponta para a direita, 90° para baixo, 180° para a esquerda, etc. Gire para combinar com o layout da página.  
- **Transparency** – defina como `0` para uma sombra sólida, `0.5` para meio transparente, etc.

### Como adicionar sombra – abordagens alternativas

Se você precisar de uma **sombra de múltiplas camadas** (por exemplo, uma sombra externa mais escura mais uma interna mais clara), pode criar uma segunda forma, deslocá‑la e definir um `ShadowFormat` diferente. Ou, para um visual rápido “sem desfoque”, defina `BlurRadius = 0`.

## Etapa 4: **Salvar documento como PDF** – a exportação final

Com o retângulo e sua sombra prontos, o último passo é gravar o arquivo como PDF. Aspose.Words lida com a conversão internamente; você apenas chama `Save` com o formato desejado.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Dica*: Se precisar controlar a conformidade do PDF (PDF/A, PDF/X) ou incorporar fontes, use uma sobrecarga:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Essa é a parte de **como salvar pdf** resumidamente.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar‑colar em `Program.cs`. Ele compila e executa como está (apenas certifique‑se de que a pasta de saída exista).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Resultado esperado

Abra o `ShadowRectangle.pdf` gerado. Você verá uma única página com um retângulo azul‑claro, uma sombra cinza suave deslocada 45° para baixo‑direita e bordas limpas. O PDF deve ser visualizável em qualquer leitor moderno (Adobe Acrobat, Edge, Chrome).

![Criar forma retangular com sombra em PDF](/images/shadow-rectangle.png "Criar forma retangular com sombra")

*(O texto alternativo da imagem inclui a palavra‑chave principal para SEO.)*

## Perguntas comuns e tratamento de casos extremos

**O que fazer se a sombra desaparecer no PDF?**  
Certifique‑se de que está usando uma versão recente do Aspose.Words (≥23.3). Versões mais antigas tinham um bug onde certas propriedades de sombra eram ignoradas durante a conversão para PDF.

**Posso mudar a cor da sombra para combinar com a minha marca?**  
Claro — basta substituir `System.Drawing.Color.Gray` por qualquer `Color` que desejar, por exemplo, `Color.FromArgb(128, 0, 0, 255)` para um azul semi‑transparente.

**Como adiciono sombra a outras formas (elipse, estrela, etc.)?**  
O mesmo `ShadowFormat` funciona para qualquer objeto `Shape`. Depois de criar a forma, obtenha seu `ShadowFormat` e defina as propriedades.

**E quanto a questões de DPI ou escala?**  
A renderização do PDF respeita o tamanho em pontos da forma. Se precisar de uma saída de alta resolução (para impressão), ajuste as dimensões da forma adequadamente ou defina `PdfSaveOptions.ImageResolution`.

**Posso exportar para outros formatos, como PNG?**  
Sim — basta chamar `document.Save("output.png", SaveFormat.Png)`. A sombra será renderizada da mesma forma.

## Dicas profissionais e boas práticas

- **Reutilize o builder**: Se você estiver adicionando várias formas, mantenha uma única instância de `DocumentBuilder`; isso é mais barato do que criar muitas.  
- **Salvamento em lote**: Ao gerar muitos PDFs em um loop, reutilize o objeto `PdfSaveOptions` para evitar alocações repetidas.  
- **Teste**: Sempre abra o PDF após salvá‑lo para verificar se a sombra aparece como esperado. Alguns visualizadores de PDF renderizam sombras ligeiramente diferentes; o Adobe Acrobat é a referência mais confiável.  
- **Desempenho**: Para documentos grandes, desative as quebras de página automáticas de `DocumentBuilder.InsertShape` definindo `builder.PageSetup.DifferentFirstPageHeaderFooter = false` se você não precisar delas.

## Conclusão

Cobrimos tudo o que você precisa para **criar forma retangular**, **adicionar sombra à forma** e **salvar o documento como PDF** usando Aspose.Words for .NET. O código é compacto, os conceitos são explicados, e agora você tem uma base sólida para experimentar outras formas, estilos de sombra e opções de exportação.  

Próximos passos? Experimente substituir o retângulo por um arredondado‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}