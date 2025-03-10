---
title: Adicionar marcas Bidi em documento do Word
linktitle: Adicionar marcas Bidi em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como adicionar marcas bidirecionais (Bidi) em documentos do Word usando o Aspose.Words para .NET com este guia. Garanta a direção correta do texto para conteúdo multilíngue.
weight: 10
url: /pt/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar marcas Bidi em documento do Word

## Introdução

No mundo do processamento de documentos, texto bidirecional (Bidi) pode ser um pouco complicado de gerenciar. Isso é especialmente verdadeiro quando se lida com idiomas que têm direções de texto diferentes, como árabe ou hebraico. Felizmente, o Aspose.Words para .NET facilita o manuseio desses cenários. Neste tutorial, mostraremos como adicionar marcas Bidi a um documento do Word usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de mergulharmos no código, certifique-se de ter o seguinte:

1. Aspose.Words para .NET: Você precisa ter o Aspose.Words para .NET instalado. Você pode baixá-lo do[Página de downloads do Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework ou .NET Core: certifique-se de ter um ambiente .NET compatível configurado para executar os exemplos.
3. Conhecimento básico de C#: Familiaridade com a linguagem de programação C# e operações básicas em .NET.

## Importar namespaces

Para começar, você precisa importar os namespaces necessários. Veja como você pode incluí-los em seu projeto:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Vamos dividir o processo de adicionar marcas Bidi em um documento do Word em etapas claras. Cada etapa guiará você pelo código e seu propósito.

## Etapa 1: configure seu documento

 Comece criando uma nova instância do`Document` classe e uma`DocumentBuilder` para adicionar conteúdo ao documento.

```csharp
// Caminho para o diretório dos seus documentos
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Crie o documento e adicione conteúdo
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Nesta etapa, você inicializa um novo documento do Word e configura um`DocumentBuilder` para facilitar a inserção de conteúdo.

## Etapa 2: adicione conteúdo ao seu documento

Em seguida, adicione algum texto ao seu documento. Aqui, adicionaremos texto em diferentes idiomas para ilustrar o tratamento de texto Bidi.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Aqui, primeiro adicionamos uma frase padrão em inglês. Então, habilitamos a formatação de texto Bidi para o texto subsequente, que é escrito em hebraico e árabe. Isso demonstra como incorporar texto bidirecional.

## Etapa 3: Configurar opções de salvamento para marcas Bidi

 Para garantir que as marcas Bidi sejam salvas corretamente no documento, você precisa configurar o`TxtSaveOptions` e habilitar o`AddBidiMarks` opção.

```csharp
// Adicionar marcas Bidi
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 Nesta etapa, criamos uma instância de`TxtSaveOptions` e definir o`AddBidiMarks`propriedade para`true`. Isso garante que as marcas Bidi sejam incluídas ao salvar o documento como um arquivo de texto.

## Conclusão

Adicionar marcas Bidi aos seus documentos do Word pode ser uma etapa crucial ao lidar com conteúdo multilíngue que inclui idiomas com diferentes direções de texto. Com o Aspose.Words para .NET, esse processo é direto e eficiente. Ao seguir as etapas descritas acima, você pode garantir que seus documentos representem corretamente o texto Bidi, melhorando a legibilidade e a precisão.

## Perguntas frequentes

### O que são marcas Bidi e por que elas são importantes?
Marcas bidi são caracteres especiais usados para controlar a direção do texto em documentos. Elas são essenciais para exibir corretamente idiomas lidos da direita para a esquerda, como árabe e hebraico.

### Posso usar o Aspose.Words for .NET para lidar com outros tipos de problemas de direção de texto?
Sim, o Aspose.Words para .NET fornece suporte abrangente para diversas necessidades de direção e formatação de texto, incluindo idiomas escritos da direita para a esquerda e da esquerda para a direita.

### É possível aplicar a formatação Bidi somente a partes específicas de um documento?
Sim, você pode aplicar a formatação Bidi a parágrafos ou seções específicas do seu documento, conforme necessário.

### Em quais formatos posso salvar o documento com marcas Bidi?
No exemplo fornecido, o documento é salvo como um arquivo de texto. No entanto, o Aspose.Words também suporta salvar documentos em vários formatos, preservando as marcas Bidi.

### Onde posso encontrar mais informações sobre o Aspose.Words para .NET?
 Você pode explorar mais sobre Aspose.Words para .NET através do[Documentação Aspose](https://reference.aspose.com/words/net/) e acessar o[Fórum de suporte](https://forum.aspose.com/c/words/8) para obter ajuda adicional.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
