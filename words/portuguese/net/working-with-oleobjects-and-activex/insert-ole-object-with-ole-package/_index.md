---
title: Inserir objeto Ole no Word com pacote Ole
linktitle: Inserir objeto Ole no Word com pacote Ole
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como inserir objetos OLE em documentos do Word usando o Aspose.Words para .NET. Siga nosso guia detalhado passo a passo para incorporar arquivos perfeitamente.
weight: 10
url: /pt/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir objeto Ole no Word com pacote Ole

## Introdução

Se você já quis incorporar um arquivo em um documento do Word, você está no lugar certo. Seja um arquivo ZIP, uma planilha do Excel ou qualquer outro tipo de arquivo, incorporá-lo diretamente em seu documento do Word pode ser incrivelmente útil. Pense nisso como ter um compartimento secreto em seu documento onde você pode guardar todos os tipos de tesouros. E hoje, vamos explicar como fazer isso usando o Aspose.Words para .NET. Pronto para se tornar um mago do Word? Vamos mergulhar!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1. Aspose.Words para .NET: Se você ainda não fez isso, baixe-o em[aqui](https://releases.aspose.com/words/net/).
2. Um ambiente de desenvolvimento: Visual Studio ou qualquer outro ambiente de desenvolvimento .NET.
3. Noções básicas de C#: Você não precisa ser um especialista, mas saber usar C# ajudará.
4. Um diretório de documentos: uma pasta onde você pode armazenar e recuperar documentos.

## Importar namespaces

Primeiro, vamos colocar nossos namespaces em ordem. Você precisa incluir os seguintes namespaces no seu projeto:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Vamos dividir isso em etapas menores para que seja fácil de acompanhar.

## Etapa 1: configure seu documento

Imagine que você é um artista com uma tela em branco. Primeiro, precisamos da nossa tela em branco, que é o nosso documento Word. Veja como você a configura:

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Este código inicializa um novo documento do Word e configura um DocumentBuilder, que usaremos para inserir conteúdo em nosso documento.

## Etapa 2: leia seu objeto antigo

Em seguida, vamos ler o arquivo que você quer incorporar. Pense nisso como pegar o tesouro que você quer esconder no seu compartimento secreto:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Esta linha lê todos os bytes do seu arquivo ZIP e os armazena em uma matriz de bytes.

## Etapa 3: Insira o objeto Ole

Agora vem a parte mágica. Vamos incorporar o arquivo em nosso documento do Word:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Aqui, criamos um fluxo de memória a partir da matriz de bytes e usamos o`InsertOleObject` método para incorporá-lo ao documento. Também definimos o nome do arquivo e o nome de exibição para o objeto incorporado.

## Etapa 4: Salve seu documento

Por fim, vamos salvar nossa obra-prima:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Isso salva o documento com seu arquivo incorporado no diretório especificado.

## Conclusão

E aí está! Você incorporou com sucesso um objeto OLE em um documento do Word usando o Aspose.Words para .NET. É como adicionar uma joia escondida dentro do seu documento que pode ser revelada a qualquer momento. Essa técnica pode ser incrivelmente útil para uma variedade de aplicações, desde documentação técnica até relatórios dinâmicos. 

## Perguntas frequentes

### Posso incorporar outros tipos de arquivo usando este método?
Sim, você pode incorporar vários tipos de arquivos, como planilhas do Excel, PDFs e imagens.

### Preciso de uma licença para o Aspose.Words?
 Sim, você precisa de uma licença válida. Você pode obter uma[licença temporária](https://purchase.aspose.com/temporary-license/) para avaliação.

### Como posso personalizar o nome de exibição do objeto OLE?
 Você pode definir o`DisplayName` propriedade do`OlePackage` para personalizá-lo.

### O Aspose.Words é compatível com o .NET Core?
Sim, o Aspose.Words suporta tanto o .NET Framework quanto o .NET Core.

### Posso editar o objeto OLE incorporado no documento do Word?
Não, você não pode editar o objeto OLE diretamente no Word. Você precisa abri-lo em seu aplicativo nativo.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
