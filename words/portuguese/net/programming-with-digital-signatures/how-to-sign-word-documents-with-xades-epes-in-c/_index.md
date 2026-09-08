---
category: general
date: 2026-09-08
description: Como assinar documentos Word usando um fluxo de trabalho de assinatura
  digital docx, carregar certificado pfx e criar assinatura XAdES em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: pt
lastmod: 2026-09-08
og_description: Como assinar documentos Word usando um fluxo de assinatura digital
  docx, carregar certificado pfx e criar assinatura XAdES em C#. Siga o exemplo completo.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Como assinar documentos Word com XAdES EPES em C# – guia passo a passo
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: Como assinar documentos do Word com XAdES EPES em C#
url: /pt/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como assinar documentos Word com XAdES EPES em C#

Se você precisa **how to sign word** arquivos programaticamente, este guia mostra uma solução completa e pronta para produção. Você aprenderá como carregar um certificado PFX, configurar um digital signature docx e criar uma assinatura XAdES‑EPES que pode ser verificada pelo Microsoft Word e validadores de terceiros.

O exemplo usa a biblioteca GroupDocs.Signature para .NET, mas os conceitos se aplicam a qualquer API que suporte XAdES. Ao final do tutorial, você terá um `Signed_XAdES_EPES.docx` assinado pronto para distribuição.

## O que você precisará

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)
- Um arquivo de certificado PFX válido (`.pfx`) que contém uma chave privada
- A senha do arquivo PFX
- Um documento Word (`.docx`) que você deseja assinar
- Pacote NuGet **GroupDocs.Signature** (instale com `dotnet add package GroupDocs.Signature`)

## Etapa 1: Instalar o pacote NuGet necessário

```bash
dotnet add package GroupDocs.Signature
```

O pacote fornece a classe `Document`, `XadesSignatureOptions` e tipos auxiliares para criar um arquivo **digitally sign word**.

## Etapa 2: Carregar o documento Word não assinado

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Carregar o documento fornece um modelo de objeto que você pode manipular antes de aplicar a assinatura.

## Etapa 3: Carregar o certificado PFX (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Dica profissional:** Se o certificado estiver armazenado no repositório de certificados do Windows, você pode recuperá‑lo com `X509Store` em vez de carregar um arquivo. A abordagem `load pfx certificate` funciona em qualquer plataforma, incluindo contêineres Linux.

## Etapa 4: (Opcional) Adicionar uma linha de assinatura visual

Uma indicação visual ajuda os destinatários a ver onde a assinatura aparece no Word.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Se você preferir uma assinatura invisível, pode pular esta etapa. O **digital signature docx** ainda será criptograficamente válido.

## Etapa 5: Configurar opções XAdES‑EPES (create xades signature)

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

A flag `XadesSignatureType.XAdES_EPES` indica à biblioteca que a assinatura deve ser incorporada de acordo com o perfil EPES (Explicit Policy-based Electronic Signature), amplamente aceito pelas regulamentações da UE e‑IDAS.

## Etapa 6: Aplicar a assinatura digital

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

O método `Sign` realiza todo o trabalho criptográfico: calcula o hash das partes do documento, cria a estrutura XML‑DSig e insere o envelope XAdES no arquivo Word.

## Etapa 7: Salvar o documento assinado

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

Após salvar, abra `Signed_XAdES_EPES.docx` no Microsoft Word. Você deverá ver uma linha de assinatura (se você adicionou uma) e uma barra de status **digitally sign word** indicando que o arquivo está assinado e a assinatura é válida.

## Exemplo completo, executável

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console.

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### Saída esperada

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Abrir o arquivo no Word exibe uma faixa verde “Signed” e, se você adicionou a linha visual, a linha de assinatura aparece no local especificado.

## Lidando com armadilhas comuns

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| **Senha do certificado está errada** | O construtor `X509Certificate2` lança uma `CryptographicException`. | Verifique a senha ou use um gerenciador de segredos seguro (Azure Key Vault, AWS Secrets Manager). |
| **Word mostra “Signature is invalid”** | O documento foi alterado após a assinatura, ou a política de assinatura está ausente. | Garanta que o arquivo seja salvo **depois** da assinatura e não seja editado novamente. Incorpore a política XAdES correta se exigida pelo seu regulador. |
| **Linha de assinatura não visível** | O documento usa um layout de seção diferente. | Anexe o `SignatureLine` ao parágrafo correto ou crie um novo parágrafo antes de adicioná‑lo. |
| **Desempenho reduzido em documentos grandes** | Assinaturas XAdES calculam hash de todas as partes do pacote. | Use APIs de streaming (`SignAsync`) ou aumente os recursos da máquina para arquivos muito grandes (>50 MB). |

## Expandindo a solução

- **Múltiplos signatários** – chame `Sign` repetidamente com diferentes certificados e defina `SignatureId` para diferenciar cada signatário.
- **Timestamping** – adicione um objeto `TimestampOptions` ao `XadesSignatureOptions` para incorporar um timestamp confiável.
- **Políticas personalizadas** – forneça um arquivo de política XML via `XadesSignatureOptions.PolicyFilePath` para conformidade com padrões específicos.

## Conclusão

Agora você sabe **how to sign word** documentos programaticamente, como **load pfx certificate**, e como **create xades signature** usando o GroupDocs.Signature. O tutorial cobriu cada passo, desde o carregamento do documento até a gravação da saída assinada, com dicas práticas para casos comuns.  

Em seguida, explore tópicos relacionados como PDFs **digitally sign word**, integrar a verificação **digital signature docx**, ou adicionar suporte a **timestamp** para atender a requisitos avançados de conformidade. Boa assinatura!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}