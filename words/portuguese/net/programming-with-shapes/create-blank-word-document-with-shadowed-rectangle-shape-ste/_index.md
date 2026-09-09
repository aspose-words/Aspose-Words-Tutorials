---
category: general
date: 2026-01-08
description: Crie um documento Word em branco e aprenda como adicionar sombra a uma
  forma retangular. Insira arquivos Word de forma e adicione sombra à forma em C#
  usando Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: pt
og_description: Crie um documento Word em branco e veja como adicionar sombra a uma
  forma retangular usando C#. Código completo, explicações e dicas.
og_title: Criar Documento Word em Branco – Adicionar Forma de Retângulo com Sombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar Documento Word em Branco com Forma de Retângulo Sombreado – Guia Passo
  a Passo
url: /pt/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word em Branco com Forma de Retângulo com Sombra – Tutorial Completo

Já precisou **criar documentos Word** em branco programaticamente e depois decorá‑los com um elegante retângulo sombreado? Você não está sozinho. Muitos desenvolvedores se deparam com um obstáculo ao descobrir que inserir formas e aplicar efeitos não é tão simples quanto digitar texto.  

Neste guia, percorreremos todo o processo — desde a criação de um `.docx` vazio até **como adicionar sombra** a um objeto **rectangle shape word**, e finalmente **inserir conteúdo shape word** com um efeito refinado de **add shape shadow**. Ao final, você terá um trecho pronto para uso que funciona com a versão mais recente do Aspose.Words para .NET.

## O que você precisará

- **Aspose.Words for .NET** (v24.10 ou mais recente) – a biblioteca que alimenta tudo abaixo.  
- Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou a CLI `dotnet`).  
- Conhecimento básico de C# – se você consegue escrever “Hello World”, está pronto.  

Nenhum pacote NuGet adicional é necessário; tudo está dentro de `Aspose.Words` e `System.Drawing`.

## Etapa 1: Criar um Documento Word em Branco

A primeira coisa a fazer é instanciar um objeto `Document` vazio. Pense nele como uma tela em branco — assim como abrir um novo arquivo Word manualmente.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Por que isso importa:*  
Uma instância `Document` representa o documento Word inteiro. Começar com um documento em branco lhe dá controle total sobre cada elemento que você adicionará depois, de parágrafos a formas.

## Etapa 2: Definir uma Forma de Retângulo (Rectangle Shape Word)

Agora precisamos de uma forma para trabalhar. Um retângulo é a geometria mais simples e funciona bem para banners, marcadores de posição ou mock‑ups simples de UI.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Por que isso importa:*  
Definir `Width` e `Height` permite controlar a área visual da forma. O `ShapeType.Rectangle` indica ao Aspose que renderize uma caixa clássica — perfeito para demonstrar **add shape shadow** mais tarde.

## Etapa 3: Aplicar uma Sombra à Forma (How to Add Shadow)

Sombras dão profundidade, fazendo um retângulo plano parecer um objeto físico. Aspose.Words expõe a propriedade `Shadow` onde você pode ajustar cor, distância, desfoque e transparência.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Por que isso importa:*  
Cada propriedade influencia a pista visual:

- **Enabled** – sem isso, as outras configurações são ignoradas.  
- **Color** – escolha um tom que combine com o tema do seu documento.  
- **Distance** – valores maiores afastam a sombra.  
- **BlurRadius** – números maiores tornam a sombra mais suave.  
- **Transparency** – ajuste fino da opacidade para sutileza.

Sinta‑se à vontade para experimentar; para um efeito dramático, aumente `Distance` para `10` e defina `Transparency` como `0.5`.

## Etapa 4: Inserir a Forma no Documento (Insert Shape Word)

Com o retângulo pronto, precisamos de um local para inseri‑lo. O ponto mais simples é o primeiro parágrafo do corpo do documento.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Por que isso importa:*  
`FirstSection.Body.FirstParagraph` está sempre presente em um novo `Document`. Ao anexar a forma aqui, você garante que a forma apareça no topo do arquivo — útil para cabeçalhos ou banners de título.

Se precisar inserir a forma em outro lugar, você pode localizar um `Paragraph` ou `Run` específico e usar `InsertAfter` ou `InsertBefore`.

## Etapa 5: Salvar o Arquivo Word

A etapa final é persistir o documento em memória no disco. Escolha uma pasta onde você tenha permissão de escrita e dê ao arquivo um nome significativo.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Por que isso importa:*  
Chamar `Save` grava um arquivo `.docx` totalmente compatível. Abra‑o no Microsoft Word, LibreOffice ou qualquer visualizador, e você verá um retângulo com uma sombra cinza suave — exatamente o que configuramos.

## Exemplo Completo em Funcionamento

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console. Ele inclui todas as diretivas `using`, a criação da forma, configuração da sombra, inserção e salvamento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Saída esperada:**  
Abra `ShadowedRectangle.docx` e você verá um retângulo cinza claro centralizado no topo da página com uma sombra sutil deslocada em 5 pts. Sem texto extra, apenas a forma — exatamente o que o código produz.

## Perguntas Frequentes & Casos Limite

### E se eu precisar de uma forma diferente?

Substitua `ShapeType.Rectangle` por qualquer outro valor do enum `ShapeType` (`Ellipse`, `Triangle`, `Star`, etc.). As propriedades de sombra funcionam da mesma maneira.

### Posso adicionar múltiplas sombras?

Aspose.Words suporta apenas uma única sombra por forma. Se precisar de efeitos em camadas, crie duas formas sobrepostas com configurações de sombra diferentes.

### Como isso funciona no .NET Core?

A mesma API funciona no .NET 6/7/8. Basta garantir que você referencie o pacote **Aspose.Words.NETCore** (ou o pacote padrão, que agora é multiplataforma).

### O `System.Drawing` ainda é suportado no Linux?

`System.Drawing.Common` é apenas para Windows a partir do .NET 6. Para projetos multiplataforma, use `Aspose.Drawing` (um NuGet separado) ou mantenha‑se nas cores definidas pelo próprio `Aspose.Words`.

### E quanto ao dimensionamento DPI?

As dimensões da forma estão em pontos (1 pt = 1/72 polegada). Se precisar de dimensionamento pixel‑perfect para um DPI específico, calcule os pontos como `pixels * 72 / dpi`.

## Dicas Profissionais & Armadilhas

- **Dica profissional:** Defina `rectangleShape.WrapType = WrapType.Inline;` se quiser que a forma flua com o texto em vez de ficar flutuando acima dele.  
- **Cuidado:** Esquecer de habilitar a sombra (`Enabled = true`). As outras configurações serão silenciosamente ignoradas.  
- **Nota de desempenho:** Adicionar muitas formas em um loop apertado pode ser lento. Agrupe‑as em uma única `Section` e chame `document.UpdatePageLayout()` uma vez ao final.  
- **Verificação de versão:** A API de sombra foi introduzida no Aspose.Words 20.2. Se você estiver em uma versão mais antiga, atualize para evitar propriedades ausentes.

## Conclusão

Criamos um documento **Word em branco**, construímos uma **rectangle shape word**, aprendemos **como adicionar sombra**, e finalmente inserimos conteúdo **shape word** com um efeito refinado de **add shape shadow** — tudo usando Aspose.Words para .NET.  

O trecho está totalmente executável, funciona no Windows e no .NET multiplataforma, e pode ser estendido para outras formas, cores ou até GIFs animados. Em seguida, você pode explorar adicionar texto dentro do retângulo, aplicar preenchimentos em gradiente ou gerar um relatório completo com várias formas estilizadas.  

Tem mais ideias? Experimente trocar a sombra cinza por uma azul, aumente o desfoque para um visual sonhador, ou combine várias formas em um logotipo personalizado. O céu é o limite, e agora você tem os blocos de construção para isso.  

Feliz codificação, e que seus documentos estejam sempre nítidos (com a quantidade certa de sombra)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}