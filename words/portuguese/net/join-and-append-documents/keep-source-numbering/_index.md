---
"description": "Aprenda a importar documentos preservando a formatação usando o Aspose.Words para .NET. Guia passo a passo com exemplos de código."
"linktitle": "Manter numeração de origem"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Manter numeração de origem"
"url": "/pt/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Manter numeração de origem

## Introdução

Ao trabalhar com Aspose.Words para .NET, a importação de documentos de uma fonte para outra, preservando a formatação, pode ser tratada de forma eficiente usando o `NodeImporter` aula. Este tutorial guiará você pelo processo passo a passo.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:
- Visual Studio instalado na sua máquina.
- Aspose.Words para .NET instalado. Caso contrário, baixe-o em [aqui](https://releases.aspose.com/words/net/).
- Conhecimento básico de programação em C# e .NET.

## Importar namespaces

Primeiro, inclua os namespaces necessários no seu projeto:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Etapa 1: Configure seu projeto

Comece criando um novo projeto C# no Visual Studio e instale o Aspose.Words por meio do Gerenciador de Pacotes NuGet.

## Etapa 2: Inicializar documentos
Crie instâncias da fonte (`srcDoc`) e destino (`dstDoc`) documentos.

```csharp
// Caminho para o diretório do seu documento 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Etapa 3: Configurar opções de importação
Configure opções de importação para manter a formatação de origem, incluindo parágrafos numerados.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Etapa 4: Importar parágrafos
Percorra os parágrafos do documento de origem e importe-os para o documento de destino.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Etapa 5: Salve o documento
Salve o documento mesclado no local desejado.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Conclusão

Concluindo, usar o Aspose.Words para .NET para importar documentos preservando a formatação é simples com o `NodeImporter` classe. Este método garante que seus documentos mantenham sua aparência e estrutura originais perfeitamente.

## Perguntas frequentes

### Posso importar documentos com estilos de formatação diferentes?
Sim, o `NodeImporter` A classe suporta a importação de documentos com estilos de formatação variados.

### E se meus documentos contiverem tabelas e imagens complexas?
O Aspose.Words para .NET manipula estruturas complexas como tabelas e imagens durante operações de importação.

### O Aspose.Words é compatível com todas as versões do .NET?
O Aspose.Words oferece suporte às versões .NET Framework e .NET Core para integração perfeita.

### Como posso lidar com erros durante a importação de documentos?
Use blocos try-catch para lidar com exceções que podem ocorrer durante o processo de importação.

### Onde posso encontrar documentação mais detalhada sobre o Aspose.Words para .NET?
Visite o [documentação](https://reference.aspose.com/words/net/) para guias abrangentes e referências de API.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}