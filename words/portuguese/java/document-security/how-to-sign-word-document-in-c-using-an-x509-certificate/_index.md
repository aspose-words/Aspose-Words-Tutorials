---
category: general
date: 2026-08-20
description: Aprenda a assinar documentos Word com uma assinatura digital para arquivos
  de contrato. Este guia aborda o carregamento de certificado X509 a partir de um
  PFX e a criação da assinatura.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word document
- load x509 certificate
- digital signature for contract
- how to sign document
- load certificate from pfx
language: pt
lastmod: 2026-08-20
og_description: Assine documento Word com uma assinatura digital para arquivos de
  contrato. Siga este guia passo a passo para carregar um certificado a partir de
  um PFX e criar uma assinatura XAdES EPES.
og_image_alt: Diagram showing how to sign word document using an X509 certificate
og_title: Assinar documento Word em C# – carregar certificado X509 e aplicar assinatura
  digital
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to sign word document with a digital signature for contract
    files. This guide covers loading x509 certificate from a PFX and creating the
    signature.
  headline: How to sign word document in C# using an X509 certificate
  type: TechArticle
tags:
- digital signature
- C#
- X509Certificate2
title: Como assinar um documento Word em C# usando um certificado X509
url: /pt/java/document-security/how-to-sign-word-document-in-c-using-an-x509-certificate/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como assinar documento Word em C# usando um certificado X509

Se você precisar **assinar documento Word** programaticamente, este tutorial mostra uma solução completa, pronta‑para‑executar. Você aprenderá como **carregar certificado x509** de um arquivo *.pfx*, configurar o nível da assinatura e gerar uma assinatura XML compatível com padrões que pode ser anexada a um contrato.  

As etapas abaixo funcionam com .NET 6+ e a biblioteca gratuita GroupDocs.Signature for .NET, que abstrai os detalhes de baixo nível do XML‑DSig enquanto ainda oferece controle total sobre o processo de assinatura.

## Pré-requisitos

- .NET 6 SDK ou posterior instalado  
- Visual Studio 2022 (ou qualquer IDE que suporte .NET)  
- Um certificado X509 válido em formato **PFX** (`certificate.pfx`) com uma senha conhecida  
- O pacote NuGet `GroupDocs.Signature` (instale com `dotnet add package GroupDocs.Signature`)  

> **Por que esses pré-requisitos?**  
> A classe `X509Certificate2` pode ler um PFX somente quando a chave privada é exportável, e o GroupDocs.Signature lida com o nível XAdES EPES necessário para muitos cenários de **digital signature for contract**.

## Etapa 1: Carregar o certificado de assinatura (carregar certificado x509)

```csharp
using System.Security.Cryptography.X509Certificates;

// Replace with the actual path to your PFX file and its password
string certPath = @"C:\Certificates\certificate.pfx";
string certPassword = "yourPassword";

// Load the certificate that contains the private key
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
    X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);
```

**Explicação**  
`X509Certificate2` lê o **carregar certificado a partir de pfx** arquivo e disponibiliza a chave privada para assinatura. As flags garantem que a chave seja armazenada no repositório da máquina, o que evita problemas de permissão em serviços Windows.

**Dica profissional:** Se você receber uma `CryptographicException` sobre acesso à chave, verifique se a conta que executa o código tem permissão de leitura no arquivo PFX e se a chave está marcada como exportável.

## Etapa 2: Inicializar o SignatureHelper e atribuir o certificado

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

// Create the helper that will perform the signing
SignatureHelper signer = new SignatureHelper();

// Attach the previously loaded certificate
signer.SetCertificate(certificate);
```

**Explicação**  
`SignatureHelper` é um wrapper leve ao redor do GroupDocs.Signature que simplifica o fluxo de trabalho. Ao chamar `SetCertificate`, você informa à biblioteca qual chave privada usar para a operação de **como assinar documento**.

## Etapa 3: Escolher o nível de assinatura XAdES (digital signature for contract)

```csharp
// XAdES_EPES is commonly required for contract signing because it embeds
// the signing certificate and timestamp information directly in the XML.
signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

**Explicação**  
XAdES‑EPES (Explicit Policy‑Based Electronic Signature) atende à maioria dos requisitos legais para uma **digital signature for contract**. A biblioteca criará automaticamente os elementos `<QualifyingProperties>` necessários.

## Etapa 4: Carregar o documento Word que será assinado

```csharp
using GroupDocs.Signature.Domain;

// The document you want to sign – a .docx contract, for example
string docPath = @"C:\Contracts\contract.docx";
Document document = new Document(docPath);
```

**Explicação**  
`Document` representa o arquivo Word na memória. Pode ser qualquer arquivo `.docx`; o mesmo código funciona para PDFs ou outros formatos OpenXML se você alterar a extensão do arquivo.

## Etapa 5: Gerar o arquivo de assinatura XML

```csharp
// Destination for the generated XML signature
string signaturePath = @"C:\Contracts\signature.xml";

// Perform the signing operation
signer.SignDocument(document, signaturePath);

// Optional: verify that the file was created
if (System.IO.File.Exists(signaturePath))
{
    Console.WriteLine($"Signature saved to: {signaturePath}");
}
```

**Explicação**  
`SignDocument` cria um arquivo XML que está em conformidade com o perfil XAdES EPES. O `signature.xml` resultante pode ser enviado junto com o arquivo Word original ou incorporado posteriormente usando uma parte XML personalizada.

**Saída esperada**

```
Signature saved to: C:\Contracts\signature.xml
```

O arquivo XML conterá elementos como `<Signature>`, `<SignedInfo>` e `<X509Data>` que referenciam o **carregar certificado x509** carregado.

## Exemplo completo e executável

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;

class Program
{
    static void Main()
    {
        // 1. Load the signing certificate (load x509 certificate)
        string certPath = @"C:\Certificates\certificate.pfx";
        string certPassword = "yourPassword";
        X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
            X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);

        // 2. Initialize the SignatureHelper and assign the certificate
        SignatureHelper signer = new SignatureHelper();
        signer.SetCertificate(certificate);

        // 3. Set the XAdES signature level (digital signature for contract)
        signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 4. Load the Word document that will be signed
        string docPath = @"C:\Contracts\contract.docx";
        Document document = new Document(docPath);

        // 5. Generate the XML signature file
        string signaturePath = @"C:\Contracts\signature.xml";
        signer.SignDocument(document, signaturePath);

        // Confirmation
        Console.WriteLine(File.Exists(signaturePath)
            ? $"Signature saved to: {signaturePath}"
            : "Failed to create signature file.");
    }
}
```

Salve o arquivo como `Program.cs`, execute `dotnet run` e você obterá um arquivo XML assinado pronto para verificação legal.

## Variações comuns e casos limites

| Cenário | O que mudar | Por quê |
|----------|----------------|-----|
| **Assinar um PDF em vez de Word** | Substitua `Document` por `PdfDocument` e ajuste a extensão do arquivo. | GroupDocs.Signature suporta múltiplos formatos; o fluxo de assinatura permanece idêntico. |
| **Usar um certificado da Windows Store** | Carregue o certificado via `X509Store` em vez de um arquivo PFX. | Útil quando a chave privada nunca sai da máquina por razões de conformidade. |
| **Adicionar um timestamp** | Chame `signer.SetTimestampProvider(new Rfc3161TimestampProvider(url))`. | Muitos fluxos de trabalho de contrato exigem um timestamp confiável para provar quando a assinatura foi aplicada. |
| **Incorporar a assinatura dentro do .docx** | Use `signer.SignDocument(document, signaturePath, new XmlSignatureOptions { EmbedIntoDocument = true })`. | Incorporar simplifica a distribuição porque apenas um arquivo é necessário. |

## Dicas para uso em produção

- **Proteja o PFX** – armazene-o no Azure Key Vault ou AWS Secrets Manager em vez do sistema de arquivos.  
- **Valide a cadeia de certificados** antes de assinar para garantir que o assinante seja confiável.  
- **Registre a operação de assinatura** (impressão digital do certificado, hash do documento, timestamp) para trilhas de auditoria exigidas pela maioria das políticas de **digital signature for contract**.  

## Conclusão

Agora você sabe como **assinar documento Word** programaticamente, como **carregar certificado x509** de um arquivo PFX e como produzir arquivos **digital signature for contract** compatíveis com padrões. O exemplo cobre todo o fluxo de **como assinar documento**, desde o carregamento do certificado até a geração da assinatura, e inclui variações comuns que você pode encontrar em projetos reais.

**Próximos passos**

- Explore outros níveis de assinatura como XAdES‑T ou XAdES‑LT para validade de longo prazo.  
- Tente incorporar a assinatura XML diretamente no arquivo Word usando a opção `EmbedIntoDocument`.  
- Integre a lógica de verificação (`signer.VerifyDocument`) para confirmar assinaturas em contratos recebidos.

Sinta-se à vontade para adaptar o código à sua própria estrutura de projeto, e boas assinaturas!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Detectar assinatura digital em documento Word](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Acessar e verificar assinatura em documento Word](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Assinando linha de assinatura existente em documento Word](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}