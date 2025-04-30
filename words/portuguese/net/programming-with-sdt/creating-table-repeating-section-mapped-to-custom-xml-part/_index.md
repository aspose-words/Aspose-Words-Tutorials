---
"description": "Aprenda a criar uma tabela com uma seção repetida mapeada para um CustomXmlPart em um documento do Word usando o Aspose.Words para .NET."
"linktitle": "Criando uma seção de repetição de tabela mapeada para uma parte XML personalizada"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Criando uma seção de repetição de tabela mapeada para uma parte XML personalizada"
"url": "/pt/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Criando uma seção de repetição de tabela mapeada para uma parte XML personalizada

## Introdução

Neste tutorial, abordaremos o processo de criação de uma tabela com uma seção repetida mapeada para uma parte XML personalizada usando o Aspose.Words para .NET. Isso é particularmente útil para gerar documentos dinamicamente com base em dados estruturados.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:
1. Biblioteca Aspose.Words para .NET instalada. Você pode baixá-la do [Site Aspose](https://releases.aspose.com/words/net/).
2. Um conhecimento básico de C# e XML.

## Importar namespaces

Certifique-se de incluir os namespaces necessários em seu projeto:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Etapa 1: Inicializar o Documento e o DocumentBuilder

Primeiro, crie um novo documento e inicialize um `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Adicionar parte XML personalizada

Adicione uma parte XML personalizada ao documento. Este XML contém os dados que queremos mapear para nossa tabela:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Etapa 3: Crie a estrutura da tabela

Em seguida, use o `DocumentBuilder` para criar o cabeçalho da tabela:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Etapa 4: Criar Seção Repetitiva

Criar um `StructuredDocumentTag` (SDT) para a seção de repetição e mapeie-a para os dados XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Etapa 5: Criar item de seção repetitivo

Crie um SDT para o item da seção repetitiva e adicione-o à seção repetitiva:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Etapa 6: Mapear dados XML para células da tabela

Crie SDTs para o título e o autor, mapeie-os para os dados XML e anexe-os à linha:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Etapa 7: Salve o documento

Por fim, salve o documento no diretório especificado:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Conclusão

Seguindo esses passos, você criou com sucesso uma tabela com uma seção de repetição mapeada para uma parte XML personalizada usando o Aspose.Words para .NET. Isso permite a geração dinâmica de conteúdo com base em dados estruturados, tornando a criação de documentos mais flexível e eficiente.

## Perguntas frequentes

### O que é um StructuredDocumentTag (SDT)?
Um SDT, também conhecido como controle de conteúdo, é uma região delimitada em um documento que é usada para conter dados estruturados.

### Posso usar outros tipos de dados na parte XML personalizada?
Sim, você pode estruturar sua parte XML personalizada com qualquer tipo de dado e mapeá-los adequadamente.

### Como adiciono mais linhas à seção de repetição?
A seção de repetição replica automaticamente a estrutura da linha para cada item no caminho XML mapeado.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}