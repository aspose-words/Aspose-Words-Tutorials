---
title: Acessar e verificar assinatura em documento do Word
linktitle: Acessar e verificar assinatura em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Acesse e verifique assinaturas digitais em documentos do Word usando o Aspose.Words para .NET com este guia passo a passo abrangente. Garanta a autenticidade do documento sem esforço.
weight: 10
url: /pt/net/programming-with-digital-signatures/access-and-verify-signature/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Acessar e verificar assinatura em documento do Word

## Introdução

Olá, colegas entusiastas de tecnologia! Já se viu em uma situação em que precisava acessar e verificar assinaturas digitais em um documento do Word, mas não tinha ideia de por onde começar? Bem, você está com sorte! Hoje, estamos mergulhando no maravilhoso mundo do Aspose.Words para .NET, uma biblioteca poderosa que torna o manuseio de documentos do Word uma brisa. Vamos guiá-lo pelo processo passo a passo, então, ao final deste guia, você será um profissional na verificação de assinaturas digitais em documentos do Word. Vamos começar!

## Pré-requisitos

Antes de nos aprofundarmos nos detalhes essenciais, há algumas coisas que você precisa ter em mãos:

1. Visual Studio: Certifique-se de ter o Visual Studio instalado na sua máquina. É aqui que você escreverá e executará seu código.
2.  Aspose.Words para .NET: Você precisará ter o Aspose.Words para .NET instalado. Você pode baixá-lo[aqui](https://releases.aspose.com/words/net/) . Não esqueça de obter seu teste gratuito[aqui](https://releases.aspose.com/) se você ainda não fez isso!
3. Um documento do Word assinado digitalmente: Tenha um documento do Word que já esteja assinado digitalmente. Este é o arquivo com o qual você trabalhará para verificar as assinaturas.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Esses namespaces permitirão que você use os recursos do Aspose.Words no seu projeto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.DigitalSignatures;
```

Certo, vamos dividir isso em etapas gerenciáveis. Cada etapa guiará você por uma parte específica do processo. Pronto? Vamos lá!

## Etapa 1: configure seu projeto

Antes de poder verificar uma assinatura digital, você precisa configurar seu projeto no Visual Studio. Veja como:

### Criar um novo projeto

1. Abra o Visual Studio.
2. Clique em Criar um novo projeto.
3. Selecione Aplicativo de console (.NET Core) ou Aplicativo de console (.NET Framework), dependendo de sua preferência.
4. Clique em Avançar, dê um nome ao seu projeto e clique em Criar.

### Instalar Aspose.Words para .NET

1. No Solution Explorer, clique com o botão direito do mouse no nome do seu projeto e selecione Gerenciar pacotes NuGet.
2. No Gerenciador de Pacotes NuGet, procure por Aspose.Words.
3. Clique em Instalar para adicioná-lo ao seu projeto.

## Etapa 2: Carregue o documento do Word assinado digitalmente

Agora que seu projeto está configurado, vamos carregar o documento do Word assinado digitalmente.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Digitally signed.docx");
```

 Substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real para o diretório do seu documento. Este trecho de código inicializa um novo`Document` objeto e carrega seu documento do Word assinado.

## Etapa 3: Acesse as Assinaturas Digitais

Com seu documento carregado, é hora de acessar as assinaturas digitais.

```csharp
foreach (DigitalSignature signature in doc.DigitalSignatures)
{
    Console.WriteLine("* Signature Found *");
    Console.WriteLine("Is valid: " + signature.IsValid);
    Console.WriteLine("Reason for signing: " + signature.Comments); 
    Console.WriteLine("Time of signing: " + signature.SignTime);
    Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
    Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
    Console.WriteLine();
}
```

Este código faz um loop em cada assinatura digital no documento e imprime vários detalhes sobre a assinatura. Vamos dividir o que cada parte faz:

1. Assinatura encontrada: indica que uma assinatura foi encontrada.
2. É válido: verifica se a assinatura é válida.
3. Motivo da assinatura: exibe o motivo da assinatura, se disponível.
4. Hora da assinatura: mostra o registro de data e hora em que o documento foi assinado.
5. Nome do assunto: recupera o nome do assunto do certificado.
6. Nome do emissor: recupera o nome do emissor do certificado.

## Etapa 4: execute seu código

Com tudo configurado, é hora de executar seu código e ver os resultados.


1. Pressione F5 ou clique no botão Iniciar no Visual Studio para executar seu programa.
2. Se o seu documento for assinado digitalmente, você verá os detalhes da assinatura impressos no console.

## Etapa 5: Lidar com possíveis erros

É sempre uma boa ideia lidar com quaisquer erros potenciais que possam ocorrer. Vamos adicionar algum tratamento básico de erros ao nosso código.

```csharp
try
{
    // O caminho para o diretório de documentos.
    string dataDir = "YOUR DOCUMENT DIRECTORY";
    Document doc = new Document(dataDir + "Digitally signed.docx");

    foreach (DigitalSignature signature in doc.DigitalSignatures)
    {
        Console.WriteLine("* Signature Found *");
        Console.WriteLine("Is valid: " + signature.IsValid);
        Console.WriteLine("Reason for signing: " + signature.Comments); 
        Console.WriteLine("Time of signing: " + signature.SignTime);
        Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
        Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
        Console.WriteLine();
    }
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

Isso capturará quaisquer exceções que possam ocorrer e imprimirá uma mensagem de erro.

## Conclusão

E aí está! Você acessou e verificou com sucesso assinaturas digitais em um documento do Word usando o Aspose.Words para .NET. Não é tão assustador quanto parece, certo? Com essas etapas, você pode manipular com confiança assinaturas digitais em seus documentos do Word, garantindo sua autenticidade e integridade. Boa codificação!

## Perguntas frequentes

### Posso usar o Aspose.Words para .NET para adicionar assinaturas digitais a um documento do Word?

Sim, você pode usar o Aspose.Words for .NET para adicionar assinaturas digitais a documentos do Word. A biblioteca fornece recursos abrangentes para adicionar e verificar assinaturas digitais.

### Que tipos de assinaturas digitais o Aspose.Words for .NET pode verificar?

O Aspose.Words para .NET pode verificar assinaturas digitais em arquivos DOCX que usam certificados X.509.

### O Aspose.Words para .NET é compatível com todas as versões do Microsoft Word?

O Aspose.Words para .NET oferece suporte a todas as versões de documentos do Microsoft Word, incluindo DOC, DOCX, RTF e muito mais.

### Como obtenho uma licença temporária para o Aspose.Words para .NET?

 Você pode obter uma licença temporária para Aspose.Words para .NET em[aqui](https://purchase.aspose.com/temporary-license/). Isso permite que você experimente todos os recursos da biblioteca sem nenhuma limitação.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?

 Você pode encontrar documentação detalhada para Aspose.Words para .NET[aqui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
