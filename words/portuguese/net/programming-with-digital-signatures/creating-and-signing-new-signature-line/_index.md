---
title: Criando e assinando uma nova linha de assinatura
linktitle: Criando e assinando uma nova linha de assinatura
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como criar e assinar digitalmente uma linha de assinatura em um documento do Word usando o Aspose.Words para .NET com este tutorial passo a passo. Perfeito para automação de documentos.
weight: 10
url: /pt/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criando e assinando uma nova linha de assinatura

## Introdução

Olá! Então, você tem um documento do Word e precisa adicionar uma linha de assinatura e então assiná-lo digitalmente. Parece complicado? De jeito nenhum! Graças ao Aspose.Words para .NET, você pode fazer isso perfeitamente com apenas algumas linhas de código. Neste tutorial, nós o guiaremos por todo o processo, desde a configuração do seu ambiente até salvar seu documento com uma assinatura novinha em folha. Pronto? Vamos mergulhar!

## Pré-requisitos

Antes de começarmos o código, vamos garantir que você tenha tudo o que precisa:
1.  Aspose.Words para .NET - Você pode[baixe aqui](https://releases.aspose.com/words/net/).
2. Um ambiente de desenvolvimento .NET - Visual Studio é altamente recomendado.
3. Um documento para assinar - Crie um documento simples do Word ou use um existente.
4.  Um arquivo de certificado - Isso é necessário para assinaturas digitais. Você pode usar um`.pfx` arquivo.
5. Imagens para a linha de assinatura - Opcionalmente, um arquivo de imagem para a assinatura.

## Importar namespaces

Primeiro, precisamos importar os namespaces necessários. Este passo é crucial, pois configura o ambiente para usar as funcionalidades do Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Etapa 1: Configurando o diretório de documentos

Todo projeto precisa de um bom começo. Vamos configurar o caminho para seu diretório de documentos. É aqui que seus documentos serão salvos e recuperados.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Criando um novo documento

Agora, vamos criar um novo documento do Word usando Aspose.Words. Este será nosso canvas onde adicionaremos a linha de assinatura.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 3: Inserindo a linha de assinatura

 É aqui que a mágica acontece. Inserimos uma linha de assinatura em nosso documento usando o`DocumentBuilder` aula.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Etapa 4: Salvando o documento com a linha de assinatura

Uma vez que a linha de assinatura esteja no lugar, precisamos salvar o documento. Este é um passo intermediário antes de prosseguirmos para assiná-lo.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Etapa 5: Configurando opções de assinatura

Agora, vamos configurar as opções para assinar o documento. Isso inclui especificar o ID da linha de assinatura e a imagem a ser usada.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Etapa 6: Carregando o certificado

Assinaturas digitais exigem um certificado. Aqui, carregamos o arquivo de certificado que será usado para assinar o documento.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Etapa 7: Assinando o documento

 Este é o passo final. Usamos o`DigitalSignatureUtil`class para assinar o documento. O documento assinado é salvo com um novo nome.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Conclusão

E aí está! Com essas etapas, você criou com sucesso um novo documento do Word, adicionou uma linha de assinatura e assinou digitalmente usando o Aspose.Words para .NET. É uma ferramenta poderosa que torna a automação de documentos muito fácil. Não importa se você está lidando com contratos, acordos ou quaisquer documentos formais, esse método garante que eles sejam assinados e autenticados com segurança.

## Perguntas frequentes

### Posso usar outros formatos de imagem para a linha de assinatura?
Sim, você pode usar vários formatos de imagem como PNG, JPG, BMP, etc.

###  É necessário usar um`.pfx` file for the certificate?
 Sim, um`.pfx` arquivo é um formato comum para armazenar informações criptográficas, incluindo certificados e chaves privadas.

### Posso adicionar várias linhas de assinatura em um único documento?
Absolutamente! Você pode inserir várias linhas de assinatura repetindo a etapa de inserção para cada assinatura.

### E se eu não tiver um certificado digital?
Você precisará obter um certificado digital de uma autoridade de certificação confiável ou gerar um usando ferramentas como o OpenSSL.

### Como verifico a assinatura digital no documento?
Você pode abrir o documento assinado no Word e acessar os detalhes da assinatura para verificar a autenticidade e a integridade da assinatura.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
