---
category: general
date: 2026-10-26
description: Aprenda como especificar a codificação em Java usando LoadOptions. Este
  guia aborda codificação de caracteres, o método setEncoding e as opções de carregamento
  de documentos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: pt
lastmod: 2026-10-26
og_description: Como especificar a codificação em Java usando Aspose.Words. Siga este
  tutorial completo para carregar documentos com o conjunto de caracteres correto.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Como especificar codificação no Java com Aspose.Words – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Como especificar a codificação ao carregar um documento com Aspose.Words para
  Java
url: /pt/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como especificar a codificação ao carregar um documento com Aspose.Words for Java

Se você precisa **como especificar a codificação** para um arquivo fonte em Java, este tutorial mostra as etapas exatas. Seja o documento usando Big5, UTF‑8 ou outro conjunto de caracteres, você pode controlar o processo de leitura com `LoadOptions`. Ao final do guia, você entenderá por que a codificação de caracteres importa, como aplicar o método `setEncoding` e como verificar se o documento foi carregado corretamente.

Carregar um documento com a codificação de caracteres correta evita texto corrompido e garante que o conteúdo multilíngue seja exibido como pretendido. Este tutorial cobre:

* O papel da **character encoding in Java** ao ler arquivos.
* Como configurar **LoadOptions encoding** para Aspose.Words.
* Código prático que você pode copiar para seu projeto.
* Armadilhas comuns, como codificações incompatíveis e como solucioná‑las.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java Development Kit (JDK) 8 ou superior.
* Maven ou Gradle para gerenciar dependências.
* Aspose.Words for Java 23.10 ou posterior (a versão usada neste guia).
* Um documento de texto de exemplo (`input.doc`) salvo com a codificação desejada (por exemplo, Big5).

Você não precisa de bibliotecas adicionais; o exemplo usa apenas a API central do Aspose.Words.

## Etapa 1: Adicionar Aspose.Words ao seu projeto

Se você usa Maven, adicione a dependência a seguir ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Para Gradle, coloque esta linha no seu `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Incluir a biblioteca torna as classes `LoadOptions`, `Document` e `Encoding` disponíveis.

## Etapa 2: Criar uma instância de `LoadOptions`

`LoadOptions` permite personalizar como o Aspose.Words abre um arquivo. Criar o objeto é a primeira parte de **como especificar a codificação**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

O objeto `LoadOptions` inicia com configurações padrão. Você ajustará suas propriedades na próxima etapa.

## Etapa 3: Definir a codificação de caracteres desejada

O método `setEncoding` define a **character encoding in Java** que o carregador deve usar. Neste exemplo, escolhemos a página de código Big5, que é comum para arquivos de texto em chinês tradicional.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Por que isso importa*: Se os bytes do arquivo forem interpretados com a página de código errada, os caracteres aparecerão como pontos de interrogação ou lixo. Ao chamar explicitamente `setEncoding`, você informa ao Aspose.Words para decodificar o fluxo de bytes usando a tabela de mapeamento Big5.

Você pode substituir `"Big5"` por qualquer nome de charset reconhecido pelo Java, como `"UTF-8"`, `"ISO-8859-1"` ou `"Windows-1252"`. O método lança `UnsupportedEncodingException` se o nome for inválido, portanto você pode querer capturar essa exceção no código de produção.

## Etapa 4: Carregar o documento com as opções configuradas

Agora que **LoadOptions encoding** está definido, passe as opções ao construtor `Document`. Esta etapa completa o fluxo central de **como especificar a codificação**.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Substitua `YOUR_DIRECTORY` pelo caminho absoluto ou relativo do seu arquivo. A instância `Document` agora contém o conteúdo totalmente analisado, respeitando a codificação que você forneceu.

## Etapa 5: Verificar se o texto foi carregado corretamente

Uma verificação rápida ajuda a garantir que a codificação foi aplicada como esperado. Você pode extrair o texto do documento e imprimi‑lo no console:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Se o console mostrar caracteres chineses legíveis (ou o idioma que você espera), a codificação foi bem‑sucedida. Se ainda aparecer saída corrompida, verifique novamente a codificação do arquivo original e confirme que o nome do charset corresponde exatamente.

## Lidando com casos de borda comuns

### 5.1 Carregando a partir de um `InputStream`

Às vezes você recebe um documento como um fluxo (por exemplo, de um serviço web). Você ainda pode controlar a codificação passando o fluxo junto com `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

As mesmas **document loading options** se aplicam, e a chamada `setEncoding` permanece inalterada.

### 5.2 Alternativa quando a codificação é desconhecida

Se você não conseguir determinar o charset do arquivo fonte, pode tentar uma biblioteca de detecção (como ICU4J) antes de definir a codificação. Quando tiver uma suposição, invoque `setEncoding` com esse valor. Essa abordagem reduz o risco de texto decodificado incorretamente.

### 5.3 Lidando com codificações não suportadas

Java suporta uma ampla variedade de páginas de código, mas algumas codificações legadas podem estar ausentes. Nesse caso, considere converter o arquivo para UTF‑8 externamente (por exemplo, usando `iconv`) antes de carregá‑lo com Aspose.Words. Após a conversão, você pode omitir a chamada `setEncoding` porque UTF‑8 é o padrão para a maioria das APIs modernas.

## Dica profissional: Reutilizar `LoadOptions` para processamento em lote

Se você precisar carregar muitos documentos que compartilham o mesmo charset, crie uma única instância de `LoadOptions` e reutilize‑a:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Reutilizar o objeto reduz a sobrecarga de criação de objetos e garante codificação consistente em todo o lote.

## Exemplo completo executável

Abaixo está o programa completo que incorpora todas as etapas, inclui as importações necessárias e trata possíveis exceções.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Saída esperada** (supondo que o arquivo fonte contenha texto chinês codificado em Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Se a saída exibir símbolos ilegíveis, revise o nome do charset ou verifique a codificação original do arquivo.

## Perguntas frequentes

**Isso funciona com outros formatos de documento (DOCX, RTF, HTML)?**  
Sim. O mesmo objeto `LoadOptions` se aplica a qualquer formato suportado pelo Aspose.Words. O único requisito é que o arquivo subjacente realmente use o charset especificado.

**E se eu precisar mudar a codificação após o documento ser carregado?**  
A codificação afeta apenas a fase de leitura. Uma vez que o objeto `Document` existe, sua representação interna em Unicode é independente do charset original. Para mudar a codificação de saída, ajuste o `SaveOptions` ao gravar o arquivo.

**Posso usar esta abordagem com outras bibliotecas (por exemplo, Apache POI)?**  
O Apache POI lida com sua própria detecção de charset para formatos binários mais antigos, mas o conceito de fornecer um charset a um carregador é semelhante. Para Aspose.Words, `LoadOptions` é a forma oficial de controlar **como especificar a codificação**.

## Conclusão

Agora você sabe **como especificar a codificação** ao carregar um documento com Aspose.Words for Java. Ao criar um objeto `LoadOptions`, chamar o método `setEncoding` e passar as opções ao construtor `Document`, você garante que os bytes do arquivo sejam interpretados corretamente. Essa prática elimina texto corrompido, suporta conteúdo multilíngue e integra‑se perfeitamente com processamento em lote ou fluxos de trabalho baseados em streams.

Explore tópicos relacionados como **document loading options**, **saving with specific encodings** e **handling Unicode in Java** para aprofundar seu domínio do processamento de texto. Experimente diferentes nomes de charset, combine a abordagem com conversão para PDF ou integre‑a a um serviço web que aceita uploads em várias codificações.

Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como converter texto RTF com codificação UTF-8 em Java usando Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Como definir opções no Aspose.Words for Java – guia completo](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recuperar documento Word DOCX corrompido usando Aspose.Words LoadOptions – Guia Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}