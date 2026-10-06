---
category: general
date: 2026-01-03
description: Crie uma forma retangular no Word com C# e adicione sombra à forma. Aprenda
  como inserir forma no Word, adicionar sombra à forma e gerar documentos do Word
  programaticamente.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: pt
og_description: Crie uma forma retangular no Word com C# e adicione sombra à forma.
  Siga este guia para inserir forma no Word, configurar sombras e gerar documentos
  programaticamente.
og_title: Criar forma retangular no Word usando C# – Tutorial completo
tags:
- C#
- Word Automation
- Aspose.Words
title: Criar forma de retângulo no Word usando C# – Guia passo a passo
url: /pt/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie forma retangular no Word usando C# – Tutorial Completo

Já precisou **criar forma retangular** em um documento Word, mas não sabia por onde começar? Você não está sozinho—muitos desenvolvedores enfrentam o mesmo obstáculo quando querem **adicionar sombra à forma** para um visual mais refinado. Neste tutorial, vamos percorrer passo a passo como **inserir forma no Word**, aplicar uma sombra sutil e, finalmente, **c# generate word document** que você pode distribuir aos usuários.

Vamos cobrir tudo, desde a configuração do projeto até o ajuste das propriedades da sombra, e terminaremos com um exemplo de código pronto‑para‑executar. Sem enrolação, apenas as partes práticas que fazem o trabalho.

## O que você vai aprender

- Como **criar forma retangular** com Aspose.Words (ou Open XML) em C#  
- As propriedades exatas que você precisa para **add shadow to shape** e dar profundidade  
- Onde posicionar a forma usando `DocumentBuilder`  
- Como salvar o arquivo para que ele abra corretamente no Microsoft Word  
- Dicas, armadilhas e variações para cenários do mundo real  

### Pré‑requisitos

- .NET 6.0 ou superior (o código funciona em .NET Core e .NET Framework)  
- Um pacote NuGet que possa manipular arquivos Word – usaremos **Aspose.Words for .NET** porque sua API é concisa. Se preferir o Open XML SDK, os conceitos são os mesmos, apenas as classes mudam.  
- Visual Studio, VS Code ou qualquer IDE C# de sua preferência  

> **Dica de especialista:** Se o orçamento está apertado, a Aspose oferece um trial gratuito perfeito para aprendizado. Basta substituir a linha de licença por um comentário ao testar.

## Etapa 1: Instale a Biblioteca de Processamento de Word

Primeiro, adicione a biblioteca ao seu projeto. Abra um terminal na pasta da solução e execute:

```bash
dotnet add package Aspose.Words
```

Se estiver usando o Open XML SDK, o comando seria `dotnet add package DocumentFormat.OpenXml`. O restante deste guia assume Aspose.Words, mas trocar as chamadas de API é simples.

## Etapa 2: Crie um Novo Documento em Branco

Com a biblioteca pronta, podemos **criar forma retangular** iniciando com um objeto `Document` limpo. Pense nisso como uma tela em branco.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

O `DocumentBuilder` nos oferece uma maneira de alto nível para inserir conteúdo sem mergulhar nas árvores de nós de baixo nível.

## Etapa 3: Insira a Forma Retangular

Com o builder em mãos, podemos **insert shape in Word**. O método `InsertShape` recebe o tipo de forma e suas dimensões (largura, altura) em pontos.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Neste ponto o retângulo aparece no documento, mas parece um pouco plano. É aqui que a próxima etapa entra.

## Etapa 4: Adicione Sombra à Forma

Sombras dão à forma uma sensação de profundidade. O objeto `Shadow` permite ajustar nitidez, distância, ângulo, cor e transparência. Abaixo está uma configuração completa que funciona bem para a maioria dos relatórios.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Por que esses valores?**  
- **BlurRadius** de `5.0` mantém a borda suave sem ficar borrada.  
- **Distance** de `4.0` desloca a sombra o suficiente para ser perceptível.  
- **Angle** `45` imita iluminação natural vindoura do canto superior esquerdo, uma convenção comum de UI.  
- **Transparency** `0.3` impede que a sombra sobreponha o preenchimento da forma.

Se precisar de um efeito mais dramático, aumente `BlurRadius` e diminua `Transparency`. Para um leve levante quase invisível, inverta esses números.

## Etapa 5: Salve o Documento

Por fim, grave o arquivo no disco. O método `Save` detecta o formato a partir da extensão do arquivo, então `.docx` gera o formato Word moderno.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Abra `ShadowRectangle.docx` no Microsoft Word e você verá um retângulo nítido com uma sombra suave — exatamente o que você queria ao perguntar “**how to add shape**” com acabamento profissional.

![Criar forma retangular com sombra no Word](placeholder-image.png "Criar forma retangular com sombra no Word")

*Texto alternativo da imagem: criar forma retangular com sombra no Word*

## Exemplo Completo em Funcionamento

Juntando tudo, aqui está o programa completo, pronto‑para‑executar. Copie‑e‑cole em um aplicativo console e pressione **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Resultado Esperado

- O `ShadowRectangle.docx` gerado contém **uma forma retangular** centralizada onde o cursor estava posicionado.  
- O retângulo exibe uma **sombra preta suave, 30 % transparente** deslocada em um ângulo de 45°.  
- Nenhum outro conteúdo é adicionado, mantendo o arquivo leve e fácil de incorporar em relatórios maiores.

## Perguntas Frequentes & Casos de Borda

### E se eu precisar de uma forma diferente?

Substitua `ShapeType.Rectangle` por qualquer outro valor do enum `ShapeType` (por exemplo, `Ellipse`, `Triangle`). A API de sombra funciona da mesma forma, então você pode reutilizar a configuração.

### Como altero a cor de preenchimento?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Posso adicionar a forma a um parágrafo específico?

Sim. Mova o `DocumentBuilder` para o parágrafo alvo com `builder.MoveToParagraph(index)` antes de chamar `InsertShape`. Isso garante que a forma apareça exatamente onde você precisa.

### E quanto aos formatos Word mais antigos (.doc)?

Basta mudar a extensão:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

O recurso de sombra é suportado no Word 2003 e posteriores, então você ainda verá o efeito.

### Usando Open XML SDK em vez de Aspose?

Os passos permanecem: crie um `WordprocessingDocument`, adicione um elemento `Drawing`, defina as propriedades `<a:shadow>`. O XML é mais verboso, mas os mesmos conceitos (tamanho, desfoque, distância, ângulo) se aplicam.

## Dicas para Evitar Armadilhas

- **Não esqueça a licença** se estiver usando a versão paga da Aspose; caso contrário, aparecerá uma marca d'água.  
- **Unidades são pontos**, não pixels. Um pixel típico de tela ≈ 0.75 pt, então ajuste as dimensões conforme necessário.  
- **Propriedades de sombra são ignoradas** se o `WrapType` da forma estiver definido como `Inline`. Use `WrapType = WrapType.Square` para formas flutuantes que respeitam a renderização da sombra.  
- **Salvar em um compartilhamento de rede** pode exigir permissões adequadas; sempre teste o caminho primeiro.

## Conclusão

Agora você sabe como **criar forma retangular** em um documento Word usando C#, **add shadow to shape**, e **c# generate word document** com aparência polida desde o início. Os passos principais — instalar a biblioteca, instanciar `Document`, inserir a forma, configurar a sombra e salvar — são fáceis de memorizar e adaptáveis a outras formas, cores ou até dados dinâmicos.

Qual o próximo passo? Experimente sobrepor múltiplas formas, incorporar imagens ou gerar um relatório completo com tabelas e gráficos. Você também pode explorar formatação condicional — alterando a intensidade da sombra com base em valores de dados — para tornar seus documentos não apenas funcionais, mas visualmente atraentes.

Sinta-se à vontade para experimentar e, se encontrar alguma peculiaridade, deixe um comentário abaixo. Boa codificação, e que seus documentos Word tenham sempre a sombra perfeita!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}