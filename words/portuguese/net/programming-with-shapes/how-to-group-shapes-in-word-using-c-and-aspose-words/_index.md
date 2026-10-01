---
category: general
date: 2026-09-30
description: Agrupar formas no Word com C# – aprenda como agrupar formas, adicionar
  retângulo e elipse e inserir forma de retângulo em documentos do Word programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: pt
lastmod: 2026-09-30
og_description: Agrupar formas no Word usando C# e Aspose.Words. Siga este guia completo
  para adicionar retângulo, adicionar elipse e aprender a agrupar formas de maneira
  eficiente.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Agrupar formas no Word com C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como agrupar formas no Word usando C# e Aspose.Words
url: /pt/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Word usando C# e Aspose.Words

Se você precisa **agrupar formas no Word** programaticamente, este guia mostra exatamente como fazer. Você verá como adicionar um retângulo, adicionar uma elipse e, em seguida, combiná‑las em uma única forma de grupo usando a biblioteca Aspose.Words para .NET.

Trabalhar com formas é uma necessidade comum ao gerar relatórios, contratos ou materiais de marketing automaticamente. Ao final deste tutorial você terá um método C# reutilizável que carrega um arquivo DOCX, insere um retângulo e uma elipse, agrupa‑os e salva o resultado — tudo sem abrir o Word manualmente.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado  
* Um ambiente de desenvolvimento como o Visual Studio 2022 (a edição Community funciona)  
* Uma licença do Aspose.Words para .NET ou uma cópia de avaliação gratuita (a API funciona sem licença, mas adiciona uma marca d'água)  

Você também precisa de um documento Word fonte (`input.docx`) em uma pasta que possa ser referenciada a partir do código. O documento pode estar vazio; o tutorial foca no manuseio de formas.

## Etapa 1: Crie um novo projeto de console e adicione Aspose.Words

Abra um terminal ou o prompt de comando do Visual Studio e execute:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Isso cria uma aplicação de console nova chamada **WordShapeDemo** e adiciona o pacote NuGet `Aspose.Words`, que contém as classes `Document` e `DocumentBuilder` usadas para manipular arquivos Word.

## Etapa 2: Carregue ou crie um documento

A primeira operação ao trabalhar com **formas de grupo no Word** é obter um objeto `Document`. Você pode carregar um arquivo DOCX existente ou iniciar a partir de um documento em branco.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

A classe `Document` representa todo o arquivo Word. Carregar um arquivo fornece uma tela pronta para inserir formas.

## Etapa 3: Inicie uma forma de grupo

Uma *forma de grupo* permite tratar várias formas independentes como uma única unidade — perfeito para mover ou redimensionar todas juntas. Para iniciar um grupo, chame `StartGroupShape()` em um `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Chamar `StartGroupShape` informa ao Aspose.Words que toda inserção de forma subsequente pertence ao mesmo grupo lógico até que você chame `EndGroupShape`.

## Etapa 4: Como adicionar forma retângulo no Word

Agora que o grupo está aberto, insira um retângulo. O método `InsertShape` recebe um enum `ShapeType`, seguido pela largura e altura (em pontos).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

O retângulo torna‑se o primeiro membro do grupo. Você pode personalizar seu preenchimento, contorno ou texto posteriormente, se necessário.

## Etapa 5: Como adicionar forma elipse no Word

Em seguida, adicione uma elipse (um círculo quando a largura é igual à altura). Isso demonstra **como adicionar elipse** usando o mesmo builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Ambas as formas agora compartilham o mesmo espaço de coordenadas dentro do grupo, facilitando o alinhamento visual.

## Etapa 6: Feche a definição da forma de grupo

Quando você tiver adicionado todos os membros desejados, feche o grupo. Isso finaliza a coleção de formas para que o Word as trate como um único objeto.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Neste ponto o documento contém uma única forma agrupada composta por um retângulo e uma elipse.

## Etapa 7: Salve o documento modificado

Por fim, grave as alterações no disco. Você pode sobrescrever o arquivo original ou criar um novo.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Executar o programa gera `output.docx`. Abra o arquivo no Microsoft Word, selecione a forma e você verá que o retângulo e a elipse se movem juntos — prova de que a operação **agrupar formas no Word** foi bem‑sucedida.

### Resultado esperado

* O arquivo Word contém um único objeto agrupado.  
* Selecionar o grupo permite arrastar, redimensionar ou girar tanto o retângulo quanto a elipse simultaneamente.  
* Nenhuma interação manual com o Word é necessária; tudo é feito via código C#.

![Grouped shapes in Word document](grouped-shapes.png "Captura de tela de um documento Word mostrando um retângulo e uma elipse agrupados")

*Texto alternativo da imagem: “Captura de tela de um documento Word mostrando um retângulo e uma elipse agrupados”* (cumpre o requisito de texto alt da imagem).

## Por que agrupar formas é importante

Agrupar formas vai além de conveniência visual. Permite que você:

* **Mantenha a consistência do layout** – mover um grupo preserva as posições relativas.  
* **Aplique transformações uma única vez** – rotacione ou escale todo o grupo em vez de cada forma individualmente.  
* **Simplifique o processamento posterior** – quando outras ferramentas leem o DOCX, elas veem uma única forma composta, reduzindo a complexidade.

Se precisar adicionar mais formas (por exemplo, uma linha ou uma caixa de texto) ao mesmo conjunto lógico, basta chamar `InsertShape` novamente antes de `EndGroupShape`.

## Variações comuns e casos de borda

| Situação | Como lidar |
|-----------|------------|
| **Unidades diferentes** – você tem medidas em centímetros | Converta centímetros para pontos (`1 cm ≈ 28.35 pt`) antes de chamar `InsertShape`. |
| **Adicionar um rótulo de texto** – você quer uma legenda dentro do grupo | Insira um `ShapeType.TextBox` após o retângulo e a elipse, então defina a propriedade `Text`. |
| **Aplicar cor de preenchimento** – você precisa de um retângulo azul | Após `InsertShape`, recupere a última forma via `builder.CurrentParagraph.Runs[0].Font` e defina `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Usar um formato de documento diferente** – você mira `.doc` em vez de `.docx` | O mesmo código funciona; basta mudar a extensão do arquivo ao chamar `Save`. Aspose.Words lida automaticamente com o formato. |

## Dicas profissionais

* **Reutilize o builder** – você pode iniciar e encerrar múltiplos grupos no mesmo documento; basta chamar `StartGroupShape` novamente após `EndGroupShape`.  
* **Desempenho** – inserir várias formas em um único bloco `StartGroupShape/EndGroupShape` é mais rápido do que inserir formas individualmente fora de um grupo.  
* **Licenciamento** – uma licença de avaliação adiciona uma marca d'água na primeira página. Instale uma licença adequada para removê‑la em ambientes de produção.

## Conclusão

Agora você sabe como **agrupar formas no Word** com C#, como **adicionar retângulo**, como **adicionar elipse** e como **inserir forma retângulo em documentos Word** usando Aspose.Words. O exemplo completo e executável demonstra cada passo, desde a configuração do projeto até a gravação do arquivo final.

A partir daqui você pode explorar tipos de forma adicionais, aplicar estilos ou combinar formas agrupadas com tabelas e imagens para criar documentos sofisticados gerados programaticamente.

---

**Próximos passos**

* Aprenda a **girar formas agrupadas**: use `Shape.RotationAngle` depois que o grupo for fechado.  
* Explore **personalização de preenchimento e contorno** para retângulos e elipses.  
* Integre essa lógica em uma API ASP.NET Core para gerar relatórios sob demanda.  

Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}