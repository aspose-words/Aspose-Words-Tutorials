---
category: general
date: 2026-10-10
description: Crie opções de assinatura e assine um documento Word usando XAdES EPES
  em Java. Aprenda a assinar um documento do Office com um certificado em poucos passos
  claros.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: pt
lastmod: 2026-10-10
og_description: Crie opções de assinatura e assine um documento Word usando XAdES
  EPES em Java. Este guia mostra como assinar documentos do Office de forma segura
  com um certificado.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Criar opções de assinatura e assinar um documento Word com XAdES EPES
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: Criar opções de assinatura e assinar um documento Word com XAdES EPES
url: /pt/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar opções de assinatura e assinar um documento Word com XAdES EPES

Se você precisa **criar opções de assinatura** para um arquivo DOCX, este guia mostra como assinar um documento Word usando o nível XAdES‑EPES em Java. Você obterá um exemplo completo e executável que assina um documento Office com um certificado PFX em apenas algumas linhas de código.

Assinar documentos office é uma necessidade comum para fluxos de trabalho legais, processamento automatizado de contratos e troca segura de documentos. Neste tutorial você aprenderá:

* Como configurar `SignatureOptions` para XAdES‑EPES.
* Como chamar `DigitalSignatureUtil.sign` para **assinar documentos Word**.
* Como lidar com armadilhas comuns, como carregamento de certificado e erros de senha.

> **Pré-requisito** – Java 17 ou superior, a biblioteca GroupDocs.Signature for Java (ou uma biblioteca XAdES compatível) e um arquivo de certificado `.pfx` válido.

---

## O que você precisará

| Item | Reason |
|------|--------|
| Java 17+ | Recursos modernos da linguagem e APIs de segurança aprimoradas |
| GroupDocs.Signature for Java (or equivalent) | Fornece `SignatureOptions`, `XmlDsigLevel` e `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | Fornece a chave privada para a assinatura digital |
| Password for the certificate | Necessária para desbloquear a chave privada |
| An unsigned DOCX file (`Unsigned.docx`) | O documento fonte que você deseja **assinar documento office** |

Certifique-se de que o JAR da biblioteca está no seu classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Etapa 1: Importar as classes necessárias

Comece importando as classes que lidam com assinaturas e I/O de arquivos.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Essas importações dão acesso à API usada para **criar opções de assinatura** e para executar a operação real de assinatura.

---

## Etapa 2: Criar opções de assinatura

O objeto `SignatureOptions` contém toda a configuração necessária para o processo de assinatura, como o nível da assinatura, aparência visual e configurações de timestamp.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Criar uma nova instância de `SignatureOptions` é o primeiro passo em **como assinar docx** porque isola cada solicitação de assinatura, evitando efeitos colaterais entre documentos.

---

## Etapa 3: Especificar o nível de assinatura XAdES EPES

XAdES‑EPES (Assinatura Eletrônica baseada em Política Explícita) é uma política amplamente aceita para assinaturas de documentos Office. Definir o nível informa à biblioteca qual perfil criptográfico usar.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Por que XAdES‑EPES? Ele incorpora a política de assinatura diretamente na assinatura, tornando o documento assinado autônomo e compatível com muitas regulamentações de assinatura eletrônica.

---

## Etapa 4: Assinar o arquivo DOCX

Agora invoque `DigitalSignatureUtil.sign`. Este método lê o arquivo de origem, aplica a assinatura e grava a saída assinada.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**O que acontece nos bastidores?**  
1. A biblioteca carrega o arquivo `.pfx` e extrai a chave privada usando a senha fornecida.  
2. Ela cria uma estrutura XML‑DSig que corresponde ao perfil XAdES‑EPES.  
3. A assinatura é incorporada ao pacote DOCX, preservando o layout original do documento.  

Se a senha do certificado estiver errada ou o arquivo não puder ser lido, uma `IOException` será lançada, que você deve tratar conforme mostrado.

---

## Etapa 5: Verificar o documento assinado (opcional)

Após a assinatura, você pode querer confirmar que a assinatura está presente e válida. O GroupDocs fornece uma API de verificação, mas uma verificação manual rápida pode ser feita com o Microsoft Word:

1. Abra `SignedXades.docx` no Word.  
2. Clique em **Arquivo → Informações → Ver assinaturas**.  
3. O Word deve exibir uma marca de verificação verde indicando uma assinatura digital válida.

A verificação automatizada com a biblioteca fica assim:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Executar a etapa de verificação lhe dá confiança programática de que **assinar documento office** foi bem-sucedido.

---

## Exemplo completo e executável

Juntando todas as peças, aqui está uma classe Java autônoma que você pode copiar, colar e executar.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Saída esperada**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Se algo der errado, o console exibirá uma mensagem de erro clara, ajudando a solucionar problemas de certificado ou caminhos de arquivo.

---

## Perguntas comuns e tratamento de casos extremos

| Question | Answer |
|----------|--------|
| **Posso usar um nível de assinatura diferente?** | Sim. Substitua `XmlDsigLevel.XAdES_EPES` por `XAdES_BES`, `XAdES_T`, etc., dependendo das necessidades de conformidade. |
| **E se meu certificado estiver armazenado em um keystore ao invés de um arquivo .pfx?** | Carregue o `KeyStore` manualmente, extraia o `PrivateKey` e o `Certificate`, então passe-os para uma sobrecarga de `sign` que aceita um objeto `KeyStore`. |
| **Como adiciono uma imagem de assinatura visível?** | Use `signatureOptions.setSignatureImage("path/to/image.png")` antes de chamar `sign`. |
| **O processo de assinatura é thread‑safe?** | O método `DigitalSignatureUtil.sign` é sem estado; você pode chamá‑lo com segurança a partir de múltiplas threads, desde que cada thread use sua própria instância de `SignatureOptions`. |
| **E se o DOCX contiver assinaturas existentes?** | A biblioteca adicionará uma nova entrada de pacote de assinatura, preservando as assinaturas anteriores. Verifique se a política de assinatura permite múltiplas assinaturas, se necessário. |

---

## Dicas e melhores práticas (E‑E‑A‑T)

* **Dica profissional:** Armazene a senha do seu certificado em um cofre seguro (ex.: Azure Key Vault) ao invés de codificá‑la diretamente.  
* **Atenção:** Separadores de caminho de arquivo no Windows (`\`) vs. Unix (`/`). Use `Paths.get(...)` para construir caminhos independentes de plataforma.  
* **Desempenho:** Assinar arquivos DOCX grandes pode ser limitado por I/O; considere fazer streaming do arquivo de entrada se processar muitos documentos em lote.  
* **Conformidade:** XAdES‑EPES está em conformidade com a regulamentação EU eIDAS; verifique os requisitos legais locais antes de escolher um nível de assinatura.

---

## Conclusão

Neste tutorial você aprendeu como **criar opções de assinatura** e **assinar um documento Word** com o nível XAdES‑EPES usando Java. O exemplo completo cobre o carregamento do certificado, a configuração das opções, a chamada de assinatura e a verificação opcional, proporcionando uma solução pronta para uso de **como assinar docx** em produção.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Opções de Carregamento em Java – Detectar Fontes Ausentes e Como Carregar DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Usando Opções e Configurações de Documento no Aspose.Words para Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Como Criar Intervalos Editáveis em Documentos Somente‑Leitura Usando Aspose.Words para Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}