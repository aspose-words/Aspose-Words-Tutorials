---
"description": "Aprenda como adicionar formas de grupo a documentos do Word usando o Aspose.Words para .NET com este tutorial abrangente passo a passo."
"linktitle": "Adicionar forma de grupo"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Adicionar forma de grupo"
"url": "/pt/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar forma de grupo

## Introdução

Criar documentos complexos com elementos visuais ricos pode, às vezes, ser uma tarefa desafiadora, especialmente quando se trata de formas de grupo. Mas não se preocupe! O Aspose.Words para .NET simplifica esse processo, tornando-o muito fácil. Neste tutorial, mostraremos as etapas para adicionar formas de grupo aos seus documentos do Word. Pronto para começar? Vamos começar!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1. Aspose.Words para .NET: Você pode baixá-lo do [Página de lançamentos do Aspose](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE compatível com .NET.
3. Conhecimento básico de C#: familiaridade com programação em C# é um diferencial.

## Importar namespaces

Para começar, precisamos importar os namespaces necessários para o nosso projeto. Esses namespaces fornecem acesso às classes e métodos necessários para manipular documentos do Word com Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Etapa 1: Inicializar o documento

Antes de mais nada, vamos inicializar um novo documento do Word. Pense nisso como se fosse uma tela em branco onde adicionaremos nossas formas de grupo.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Aqui, `EnsureMinimum()` adiciona um conjunto mínimo de nós necessários para o documento.

## Etapa 2: Crie o objeto GroupShape

Em seguida, precisamos criar um `GroupShape` objeto. Este objeto servirá como um contêiner para outras formas, permitindo-nos agrupá-las.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Etapa 3: adicionar formas ao GroupShape

Agora, vamos adicionar formas individuais ao nosso `GroupShape` contêiner. Começaremos com uma forma de borda de destaque e, em seguida, adicionaremos uma forma de botão de ação.

### Adicionando uma forma de borda de destaque

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

Este trecho de código cria uma forma de borda de destaque com largura e altura de 100 unidades e a adiciona ao `GroupShape`.

### Adicionando um formato de botão de ação

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

Aqui, criamos uma forma de botão de ação, posicionamos e adicionamos ao nosso `GroupShape`.

## Etapa 4: Definir as dimensões do GroupShape

Para garantir que nossas formas se encaixem bem no grupo, precisamos definir as dimensões do `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

Isso define a largura e a altura do `GroupShape` como 200 unidades e define o tamanho das coordenadas adequadamente.

## Etapa 5: Insira o GroupShape no Documento

Agora, vamos inserir nosso `GroupShape` no documento usando `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` fornece uma maneira fácil de adicionar nós, incluindo formas, ao documento.

## Etapa 6: Salve o documento

Por fim, salve o documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

E pronto! Seu documento com formas de grupo está pronto.

## Conclusão

Adicionar formas de grupo aos seus documentos do Word não precisa ser um processo complicado. Com o Aspose.Words para .NET, você pode criar e manipular formas com facilidade, tornando seus documentos mais atraentes e funcionais. Siga os passos descritos neste tutorial e você se tornará um profissional em pouco tempo!

## Perguntas frequentes

### Posso adicionar mais de duas formas a um GroupShape?
Sim, você pode adicionar quantas formas precisar a um `GroupShape`Basta usar o `AppendChild` método para cada forma.

### É possível estilizar as formas dentro de um GroupShape?
Com certeza! Cada forma pode ser estilizada individualmente usando as propriedades disponíveis no `Shape` aula.

### Como posiciono o GroupShape dentro do documento?
Você pode posicionar o `GroupShape` definindo seu `Left` e `Top` propriedades.

### Posso adicionar texto às formas dentro do GroupShape?
Sim, você pode adicionar texto às formas usando o `AppendChild` método para adicionar um `Paragraph` contendo `Run` nós com texto.

### É possível agrupar formas dinamicamente com base na entrada do usuário?
Sim, você pode criar e agrupar formas dinamicamente com base na entrada do usuário ajustando as propriedades e os métodos adequadamente.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}