---
category: general
date: 2026-03-27
description: Crie um documento Word em C# e aprenda como adicionar forma, aplicar
  sombra à forma e definir a distância da sombra. Guia passo a passo para Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: pt
og_description: Crie um documento Word em C# com uma forma retangular e sombra personalizada.
  Siga este tutorial completo para definir a distância e o estilo da sombra.
og_title: Criar documento Word C# – Adicionar forma com sombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar documento Word C# – Adicionar forma com sombra
url: /pt/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word C# – Adicionar Forma com Sombra

Já precisou **create word document c#** que contenha um retângulo bem estilizado? Talvez você esteja criando um modelo de relatório e queira uma sombra sutil para realçar o layout. Neste tutorial vamos percorrer exatamente isso – como adicionar uma forma, aplicar sombra à forma e até ajustar a distância da sombra usando Aspose.Words.

Começaremos com um documento em branco, inseriremos um retângulo, aplicaremos uma sombra predefinida e finalizaremos salvando o arquivo. Ao final você terá um .docx pronto‑para‑usar que pode abrir no Word e ver o efeito instantaneamente. Sem ferramentas externas, apenas código C# puro.

## Pré-requisitos

- .NET 6 (ou qualquer .NET Framework recente) instalado.
- Visual Studio 2022 ou VS Code com extensão C#.
- Pacote NuGet Aspose.Words para .NET (`Aspose.Words` versão 23.12 ou posterior).  
  Você pode adicioná‑lo via o Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

É isso – nenhum DLL extra ou interop COM necessário.

## Passo 1: Inicializar um Novo Documento e Builder – *create word document c#* Básico

Primeiro precisamos de um objeto `Document` que representa o arquivo Word e de um `DocumentBuilder` para editá‑lo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por que este passo importa:** A classe `Document` é o contêiner para todas as partes do Word (páginas, estilos, imagens). O builder é a API de alto nível que abstrai a manipulação de nós de baixo nível, facilitando **create word document c#** sem lidar diretamente com XML.

## Passo 2: Inserir uma Forma Retângulo – *how to create rectangle*  

Agora vamos colocar um retângulo na página. O tamanho é expresso em pontos (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Dica de especialista:** Se precisar de uma forma diferente, basta trocar `ShapeType.Rectangle` por `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. O mesmo código funciona para **how to add shape** de qualquer tipo.

## Passo 3: Aplicar uma Sombra Predefinida e Ajustá‑la – *apply shadow to shape*  

Aspose.Words vem com vários formatos de sombra predefinidos. Usaremos `Preset1` e então personalizaremos distância, desfoque, transparência e cor.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Por que personalizar a sombra?** A propriedade `Distance` controla quão longe a sombra fica do retângulo – pense nisso como o “levante” que você veria em uma renderização 3‑D. Alterar `BlurRadius` suaviza as bordas, enquanto `Transparency` permite criar um visual sutil e profissional. Isso cobre o requisito de **set shadow distance** e mostra como **apply shadow to shape** de forma flexível.

## Passo 4: Salvar o Documento – *create word document c#* Conclusão

Finalmente, grave o documento no disco. Ajuste o caminho para uma pasta onde você tenha permissão de gravação.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Abra o arquivo resultante no Microsoft Word, e você verá um retângulo azul‑claro com uma sombra cinza suave deslocada em 5 pt. Essa é a prova visual de que você **create word document c#** com uma forma estilizada com sucesso.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="exemplo de create word document c# mostrando retângulo com sombra"}

## Variações Opcionais & Casos Limite

| Cenário | O que Alterar | Por que é Importante |
|----------|----------------|----------------|
| **Estilo de sombra diferente** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Fornece um visual mais dramático sem código extra. |
| **Sem predefinição – sombra personalizada** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Controle total sobre direção e profundidade. |
| **Múltiplas formas** | Call `builder.InsertShape` again before saving. | Útil para modelos complexos com ícones, logotipos, etc. |
| **Compatibilidade com versões mais antigas do Aspose** | Use `ShadowEffect` class (available in v20.x). | Garante que seu código funcione em projetos legados. |
| **Salvar como PDF** | `document.Save("ShadowShape.pdf");` | A mesma renderização da sombra aparece na saída PDF. |

> **Pergunta comum:** *E se a sombra não aparecer no Word?*  
> Certifique‑se de que está usando uma versão recente do Aspose.Words (≥ 22.9). Versões mais antigas tinham suporte limitado a sombras. Também verifique se o documento está sendo aberto em uma versão recente do Word (2016+).

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para copiar e colar. Inclui todas as diretivas `using`, comentários e tratamento de erros para uma experiência tranquila.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Execute o programa, navegue até `C:\Temp\ShadowShape.docx`, e você verá o retângulo com a sombra exata que configuramos.

## Recapitulação & Próximos Passos

- Agora você sabe como **create word document c#**, inserir um retângulo e **apply shadow to shape** com uma **set shadow distance** personalizada.  
- O exemplo usa Aspose.Words, que abstrai as complexidades do OpenXML e garante renderização consistente em diferentes versões do Word.  
- Quer ir além? Experimente combinar múltiplas formas, adicionar texto dentro do retângulo ou exportar o mesmo documento como PDF para ver como a sombra se traduz.

### Tópicos Relacionados que Você Pode Explorar

- **How to add shape** a um cabeçalho/rodapé para branding.  
- Usando **Aspose.Words** para inserir gráficos e tabelas programaticamente.  
- Personalizando **shadow effects** em imagens ao invés de formas vetoriais.  
- Automatizando a geração em massa de documentos para faturas ou certificados.

Sinta‑se à vontade para experimentar, quebrar o código e depois reconstruí‑lo – essa é a maneira mais rápida de internalizar os conceitos. Se encontrar algum problema, deixe um comentário abaixo ou consulte a documentação oficial do Aspose.Words para insights mais profundos da API.

Feliz codificação, e aproveite para deixar seus arquivos Word um pouco mais polidos!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}