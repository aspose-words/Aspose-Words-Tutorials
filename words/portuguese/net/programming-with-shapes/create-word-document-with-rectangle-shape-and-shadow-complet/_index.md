---
category: general
date: 2026-01-02
description: Crie um documento do Word com uma forma retangular, defina a cor de preenchimento
  da forma e salve o arquivo docx usando Aspose.Words. Aprenda a criar um retângulo
  com sombra em minutos.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: pt
og_description: Crie um documento Word com um retângulo personalizado, defina sua
  cor de preenchimento, adicione uma sombra e salve como DOCX. Código completo e explicações.
og_title: Criar documento Word com forma retangular – passo a passo
tags:
- Aspose.Words
- C#
- Document Generation
title: Criar documento Word com forma de retângulo e sombra – Guia completo
url: /pt/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie Documento Word com Forma Retangular e Sombra – Guia Completo

Já se perguntou como **criar documento word** que contenha um retângulo bem estilizado? Talvez você precise de um espaço reservado para um logotipo, um banner colorido ou apenas um indicativo visual em um relatório. Neste tutorial, vamos **adicionar forma retangular**, definir uma cor de preenchimento, aplicar uma sombra sutil e, finalmente, **salvar arquivo docx** – tudo com Aspose.Words para .NET.

Você sairá com um trecho de C# pronto‑para‑executar, uma explicação clara de cada linha e algumas dicas que pode reutilizar em seus próprios projetos. Sem enrolação, apenas uma solução prática que você pode copiar‑colar.

## O que você precisará

- .NET 6 ou superior (o código também funciona no .NET Framework)  
- Visual Studio 2022 (ou qualquer editor de sua preferência)  
- Pacote NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  

Se já tem tudo isso, ótimo – vamos começar.

## Etapa 1 – Inicializar um Novo Documento (Como criar documento word)

A primeira coisa a fazer é **criar documento word** na memória. Pense nisso como abrir uma tela em branco onde você desenhará seu retângulo mais tarde.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Por que isso importa:** `Document` representa todo o arquivo DOCX, enquanto `DocumentBuilder` é um auxiliar conveniente que permite inserir texto, tabelas, imagens e formas sem manipular manualmente a árvore de nós subjacente.

## Etapa 2 – Inserir uma Forma Retangular (Adicionar forma retangular)

Agora vamos **adicionar forma retangular** ao documento. O método `InsertShape` recebe o tipo da forma e suas dimensões em pontos (1 ponto = 1/72 polegada).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Dica profissional:** Se precisar criar uma geometria diferente (elipse, triângulo etc.), basta mudar `ShapeType.Rectangle` para o valor enum desejado.

## Etapa 3 – Configurar a Sombra (Definir cor de preenchimento da forma & sombra)

Uma sombra pode fazer uma forma plana parecer mais tridimensional. Aqui habilitamos a sombra e ajustamos sua aparência.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Por que esses valores?** Um raio de desfoque modesto e uma distância de 5 pontos evitam que a sombra sobrecarregue a forma, enquanto 45° imita uma fonte de luz vindo do canto superior esquerdo – uma convenção comum de UI.

## Etapa 4 – Salvar o Documento (Salvar arquivo docx)

Por fim, **salvamos o arquivo docx** no disco. Ajuste o caminho conforme seu ambiente.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Ao abrir `ShadowDemo.docx` no Word, você deverá ver um retângulo azul‑claro com uma sombra cinza suave, exatamente como a captura de tela abaixo.

![Create Word Document with rectangle shape and shadow](https://example.com/images/rectangle-shadow.png "Create Word Document with rectangle shape and shadow")

*Texto alternativo da imagem:* **Criar Documento Word** mostrando uma forma retangular com sombra.

## Exemplo Completo, Pronto‑para‑Executar (Como criar retângulo e salvar)

Juntando tudo, aqui está o programa completo que você pode copiar para um aplicativo console:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Resultado Esperado

- Um arquivo chamado **ShadowDemo.docx** aparece na pasta de destino.  
- Ao abri‑lo no Microsoft Word, vê‑se uma única página com o texto “Shadow Demo” seguido de um retângulo azul‑claro.  
- O retângulo projeta uma sombra cinza suave em ângulo de 45°, conferindo-lhe um leve aspecto 3‑D.

## Perguntas Frequentes & Casos de Borda

### E se eu precisar de um tamanho diferente?

Basta alterar os argumentos `200, 100` em `InsertShape`. Esses números são a largura e a altura em pontos. Para um quadrado, use valores idênticos.

### Posso tornar a sombra mais pronunciada?

Aumente `BlurRadius` para bordas mais suaves, eleve `Distance` para maior deslocamento ou diminua `Transparency` (ex.: `0.1`) para escurecê‑la.

### Como adiciono uma borda ao redor do retângulo?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Isso é compatível com versões mais antigas do Aspose.Words?

Sim. A classe `ShadowFormat` existe desde as versões iniciais de 2020. Se estiver usando uma versão muito antiga, talvez precise atualizar para acessar todas as propriedades.

## Dicas & Armadilhas

- **Dica profissional:** Sempre descarte documentos grandes (`doc.Dispose()`) quando terminar, especialmente em aplicações web, para liberar recursos nativos.  
- **Cuidado com:** Usar um caminho relativo sem permissões adequadas pode gerar `UnauthorizedAccessException`. Prefira caminhos absolutos ou garanta que o pool de aplicativos tenha acesso de gravação.  
- **Lembre‑se:** A propriedade `FillColor` aceita qualquer `System.Drawing.Color`. Sinta‑se à vontade para usar `Color.FromArgb(255, 173, 216, 230)` para um tom pastel personalizado.

## Próximos Passos

Agora que você sabe como **criar documento word**, **adicionar forma retangular**, **definir cor de preenchimento da forma** e **salvar arquivo docx**, pode experimentar mais:

- Inserir múltiplas formas e organizá‑las com `RelativeHorizontalPosition` e `RelativeVerticalPosition`.  
- Combinar o retângulo com texto usando `Shape.TextBox` para legendas.  
- Exportar o mesmo documento para PDF (`doc.Save("output.pdf")`) para distribuição.

Se quiser aprofundar em gráficos avançados, explore o suporte do Aspose.Words a **WordArt**, **gráficos** e **imagens embutidas**. Cada um segue o mesmo padrão: criar um nó, configurar suas propriedades e salvar.

---

### TL;DR

- Use `Document` e `DocumentBuilder` para **criar documento word**.  
- Chame `InsertShape(ShapeType.Rectangle, …)` para **adicionar forma retangular**.  
- Defina `FillColor` para o fundo desejado.  
- Habilite `ShadowFormat` e ajuste suas propriedades para um visual refinado.  
- Termine com `document.Save("seuCaminho.docx")` para **salvar arquivo docx**.

Boa codificação e divirta‑se deixando seus arquivos Word um pouco mais elegantes!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}