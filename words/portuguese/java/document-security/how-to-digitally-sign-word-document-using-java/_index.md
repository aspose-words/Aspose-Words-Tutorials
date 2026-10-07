---
category: general
date: 2026-09-27
description: Aprenda como assinar digitalmente um documento Word em Java. Este guia
  mostra como adicionar uma assinatura digital a um arquivo Word e como inserir assinatura
  digital em um docx seguindo as melhores práticas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- digitally sign word document
- digital signature for word file
- add digital signature to docx
language: pt
lastmod: 2026-09-27
og_description: Assine digitalmente um documento Word com Java. Siga este tutorial
  para adicionar uma assinatura digital a um arquivo Word e aprenda como inserir assinatura
  digital em um docx de forma segura.
og_image_alt: Screenshot showing a Java program that digitally signs a Word document
og_title: Assine digitalmente documento Word em Java – guia completo passo a passo
schemas:
- author: GroupDocs
  dateModified: '2026-09-27'
  description: Learn how to digitally sign a Word document in Java. This guide shows
    adding a digital signature for Word file and how to add digital signature to docx
    with best practices.
  headline: How to digitally sign Word document using Java
  type: TechArticle
tags:
- Java
- Digital Signature
- Docx
title: Como assinar digitalmente um documento Word usando Java
url: /pt/java/document-security/how-to-digitally-sign-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como assinar digitalmente um documento Word usando Java

Se você precisa **assinar digitalmente um documento Word** em uma aplicação Java, este guia mostra os passos exatos. Você verá como adicionar uma **assinatura digital para arquivo Word** e **adicionar assinatura digital ao docx** de forma segura usando GroupDocs.Signature (ou uma biblioteca similar).  

O processo é simples: carregar o `.docx`, aplicar um certificado PKCS#12, configurar o nível XML‑DSig e salvar o arquivo assinado. Ao final deste tutorial você terá um programa executável que produz uma assinatura XAdES‑EPES compatível.

## Pré-requisitos

- Java 17 ou superior (o código também compila com Java 11)  
- Maven ou Gradle para gerenciamento de dependências  
- Um certificado PKCS#12 (`.pfx`) e sua senha  
- Familiaridade básica com Java I/O  

> **Dica profissional:** Armazene a senha do certificado em um cofre seguro (por exemplo, Azure Key Vault) em vez de codificá‑la diretamente no código.

## Etapa 1: Adicionar a dependência GroupDocs.Signature

Se você estiver usando Maven, adicione o seguinte ao seu `pom.xml`. Para Gradle, a linha `implementation` equivalente está mostrada no comentário.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-signature</artifactId>
    <version>23.10</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.groupdocs:groupdocs-signature:23.10'
```

Esses artefatos fornecem `Document`, `DigitalSignatureUtil` e os enums relacionados usados no exemplo.

## Etapa 2: Carregar o documento Word que você deseja assinar

```java
import com.groupdocs.signature.Signature;
import com.groupdocs.signature.domain.docx.Document;
import com.groupdocs.signature.exception.SignatureException;

public class WordSigner {

    public static void main(String[] args) {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        try {
            // Load the Word document into the GroupDocs model
            Document document = new Document(inputPath);
            System.out.println("Document loaded successfully.");
            // Continue with signing...
            signDocument(document);
        } catch (SignatureException e) {
            System.err.println("Failed to load the document: " + e.getMessage());
        }
    }
```

**Por que isso importa:** Carregar o arquivo no objeto `Document` da biblioteca fornece acesso total aos campos de assinatura e à manipulação de conteúdo sem alterar o arquivo original no disco.

## Etapa 3: Aplicar uma assinatura digital usando um certificado PKCS#12

```java
    private static void signDocument(Document document) {
        // Path to your .pfx certificate and its password
        String certPath = "YOUR_DIRECTORY/cert.pfx";
        String certPassword = "pwd";

        try {
            // Apply an XML‑DSig signature (XAdES‑EPES will be set later)
            DigitalSignatureUtil.sign(
                document,
                certPath,
                certPassword,
                SignatureType.XML_DSIG
            );
            System.out.println("Digital signature applied.");
        } catch (SignatureException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // Proceed to configure the signature level
        configureSignatureLevel(document);
    }
```

**Explicação:**  
- `SignatureType.XML_DSIG` indica à biblioteca que deve criar uma assinatura XML‑DSig, que é necessária para conformidade XAdES.  
- Usar um certificado PKCS#12 garante que a assinatura seja criptograficamente forte e possa ser validada por ferramentas padrão (por exemplo, Microsoft Word, Adobe Acrobat).

## Etapa 4: Definir o nível XAdES‑EPES para maior conformidade

```java
    private static void configureSignatureLevel(Document document) {
        // The signing operation creates a signature field automatically
        if (document.getSignatureFields().isEmpty()) {
            System.err.println("No signature fields were created.");
            return;
        }

        // Grab the first (and usually only) signature field
        SignatureSignatureField signatureField = document.getSignatureFields().get(0);

        // Set the XML‑DSig level to XAdES‑EPES (Enhanced Electronic Signature)
        signatureField.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
        System.out.println("Signature level set to XAdES‑EPES.");

        // Save the signed document
        saveSignedDocument(document);
    }
```

**Por que XAdES‑EPES?**  
XAdES‑EPES adiciona carimbos de tempo e informações de política de assinatura, tornando a assinatura legalmente admissível em muitas jurisdições. É o nível recomendado quando você precisa de **assinatura digital para arquivo Word** que esteja em conformidade com e‑IDAS ou regulamentos semelhantes.

## Etapa 5: Salvar o documento assinado

```java
    private static void saveSignedDocument(Document document) {
        String outputPath = "YOUR_DIRECTORY/SignedXAdES.docx";

        try {
            document.save(outputPath);
            System.out.println("Signed document saved to: " + outputPath);
        } catch (SignatureException e) {
            System.err.println("Failed to save signed document: " + e.getMessage());
        }
    }
}
```

**Resultado:** Após executar o programa, `SignedXAdES.docx` contém um campo de assinatura visível. Abrir o arquivo no Microsoft Word exibirá *Signed and all signatures are valid* se a cadeia de certificados for confiável.

### Saída esperada no console

```
Document loaded successfully.
Digital signature applied.
Signature level set to XAdES‑EPES.
Signed document saved to: YOUR_DIRECTORY/SignedXAdES.docx
```

## Manipulando múltiplos campos de assinatura (avançado)

Se o seu modelo já contém vários marcadores de posição de assinatura, você pode iterar sobre eles:

```java
for (SignatureSignatureField field : document.getSignatureFields()) {
    field.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
}
```

Isso garante **adicionar assinatura digital ao docx** em cada local necessário, útil para fluxos de trabalho com múltiplos assinantes.

## Armadilhas comuns e como evitá‑las

| Problema | Causa | Correção |
|----------|-------|----------|
| *Campo de assinatura não criado* | Usando um tipo de assinatura não‑XML (por exemplo, `SignatureType.CMS`) | Sempre use `SignatureType.XML_DSIG` quando planejar definir níveis XAdES |
| *Word exibe “Signature is not valid”* | Cadeia de certificados não confiável na máquina local | Importe os certificados raiz/intermediários para o repositório Trusted Root do Windows |
| *Tamanho do arquivo aumenta excessivamente* | Salvando o documento sem compressão | Chame `document.save(outputPath, SaveOptions.create().setCompress(true))` |

## Exemplo completo executável (copiar‑colar)

```java
import com.groupdocs.signature.Signature;
import com.groupdocs.signature.domain.SignatureSignatureField;
import com.groupdocs.signature.domain.docx.Document;
import com.groupdocs.signature.domain.enums.SignatureType;
import com.groupdocs.signature.domain.enums.XmlDsigLevel;
import com.groupdocs.signature.exception.SignatureException;

public class WordSigner {

    public static void main(String[] args) {
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String certPath  = "YOUR_DIRECTORY/cert.pfx";
        String certPwd   = "pwd";
        String outputPath = "YOUR_DIRECTORY/SignedXAdES.docx";

        try {
            // 1️⃣ Load the document
            Document document = new Document(inputPath);
            System.out.println("Document loaded.");

            // 2️⃣ Apply XML‑DSig signature
            DigitalSignatureUtil.sign(document, certPath, certPwd, SignatureType.XML_DSIG);
            System.out.println("Signature applied.");

            // 3️⃣ Set XAdES‑EPES level
            if (!document.getSignatureFields().isEmpty()) {
                SignatureSignatureField sigField = document.getSignatureFields().get(0);
                sigField.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
                System.out.println("XAdES‑EPES level set.");
            } else {
                System.err.println("No signature fields found.");
            }

            // 4️⃣ Save the signed file
            document.save(outputPath);
            System.out.println("Signed document saved at " + outputPath);
        } catch (SignatureException e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

Execute a classe com `java -cp target/your‑jar.jar WordSigner`. O programa criará `SignedXAdES.docx` contendo uma **assinatura digital para arquivo Word** totalmente compatível.

## Conclusão

Agora você sabe como **assinar digitalmente um documento Word** usando Java, desde o carregamento do arquivo até a aplicação de um certificado PKCS#12, definição do nível XAdES‑EPES e salvamento do resultado. Esta solução completa permite **adicionar assinatura digital ao docx** em qualquer fluxo de trabalho empresarial.

### O que vem a seguir?

- Explore **digital signature for Word file** com servidores de carimbo de tempo (RFC 3161) para validação de longo prazo.  
- Combine múltiplas assinaturas para processos de aprovação com várias partes.  
- Integre a rotina de assinatura em um endpoint REST Spring Boot para oferecer serviços de “sign‑on‑the‑fly”.

Sinta‑se à vontade para experimentar diferentes tipos de certificado, políticas de assinatura, ou até mesmo mudar para `SignatureType.CMS` se precisar de uma assinatura CMS destacada em vez de XML‑DSig. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Detectar assinatura digital em documento Word](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Acessar e verificar assinatura em documento Word](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Assinar linha de assinatura existente em documento Word](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}