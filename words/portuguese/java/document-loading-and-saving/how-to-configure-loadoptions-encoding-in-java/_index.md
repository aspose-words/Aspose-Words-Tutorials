---
category: general
date: 2026-10-20
description: Configure a codificação do LoadOptions em Java para ler documentos corretamente
  e altere a codificação do documento para UTF‑8 usando o Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: pt
lastmod: 2026-10-20
og_description: Configure a codificação do LoadOptions em Java para garantir o tratamento
  correto de caracteres e aprenda como alterar a codificação do documento para UTF‑8
  usando o Aspose.Words.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: Configure a codificação de LoadOptions em Java – guia completo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Como configurar a codificação do LoadOptions no Java
url: /pt/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como configurar a codificação LoadOptions em Java

Se você precisar **configurar a codificação LoadOptions** em Java, este guia mostra como definir o conjunto de caracteres correto e então **alterar a codificação do documento para UTF-8** usando Aspose.Words. A codificação correta evita texto corrompido ao carregar arquivos que utilizam páginas de código legadas, como Big5, Shift_JIS ou Windows‑1252.

Você aprenderá a:

* criar uma instância `LoadOptions` com uma codificação específica,
* carregar um documento fonte que usa essa codificação,
* salvar o documento em uma codificação diferente (UTF‑8) sem perda de dados,
* verificar se a conversão foi bem‑sucedida.

O tutorial assume que você tem um ambiente básico de desenvolvimento Java e uma licença válida do Aspose.Words for Java. Nenhuma ferramenta externa é necessária.

## Pré‑requisitos

| Requisito | Por que é importante |
|-------------|----------------|
| Java 17 ou posterior | Fornece recursos modernos da linguagem e suporte de longo prazo. |
| Aspose.Words for Java (v23.9 ou mais recente) | A classe `LoadOptions` está nesta biblioteca. |
| Um documento fonte codificado com uma página de código legada (por exemplo, Big5) | Demonstrar a necessidade de codificação personalizada. |
| Uma IDE ou ferramenta de build (Maven/Gradle) | Facilita a compilação e execução do exemplo. |

Adicione a dependência Aspose.Words ao seu `pom.xml` se você usar Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Configurar a codificação LoadOptions

O primeiro passo é informar ao Aspose.Words qual conjunto de caracteres esperar ao ler o arquivo. Isso é feito configurando o objeto `LoadOptions`.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Por que isso importa:** Quando um documento é salvo com uma codificação legada, o carregador padrão assume UTF‑8. Definindo explicitamente a codificação, você evita mojibake (caracteres corrompidos) e preserva o texto original.

### Dica profissional
Se você não tem certeza de qual codificação um arquivo usa, pode inspecionar sua marca de ordem de byte (BOM) ou perguntar ao provedor do documento. Codificações legadas comuns incluem `Big5`, `Shift_JIS` e `Windows-1252`.

## Carregar o documento com as opções configuradas

Agora que `LoadOptions` está pronto, carregue o arquivo fonte. O construtor que aceita um caminho de arquivo e uma instância `LoadOptions` garante que a codificação personalizada seja aplicada.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Por que isso importa:** O objeto `Document` agora contém o texto exatamente como aparece no arquivo original, porque o carregador respeitou a página de código Big5 que você forneceu.

## Alterar a codificação do documento para UTF-8

Aspose.Words armazena texto internamente como Unicode, de modo que o ato de salvar o documento determina a codificação externa. Para produzir um arquivo UTF‑8, basta salvar sem especificar uma codificação adicional — UTF‑8 é o padrão para formatos modernos Office Open XML. No entanto, você pode forçá‑lo explicitamente para maior clareza.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Se precisar produzir uma representação em texto puro (por exemplo, `.txt`) com UTF‑8, passe um objeto `SaveOptions`:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Por que isso importa:** Salvar como UTF‑8 garante que qualquer sistema downstream — serviços web, bancos de dados ou editores modernos — possa ler o arquivo sem etapas adicionais de conversão.

## Verificar a conversão

Uma maneira rápida de confirmar que a mudança de codificação foi bem‑sucedida é ler o arquivo salvo novamente com um leitor UTF‑8 e imprimir alguns caracteres.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Se a saída exibir caracteres legíveis (sem símbolos �), a conversão funcionou como esperado.

## Exemplo completo executável

Abaixo está um programa autocontido que reúne todas as etapas. Substitua os caminhos de arquivo pelos seus próprios.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Saída esperada**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Se os caracteres aparecerem corretamente, você configurou com sucesso a **codificação LoadOptions** e **alterou a codificação do documento para UTF-8**.

## Armadilhas comuns e como evitá‑las

| Sintoma | Causa | Correção |
|---------|-------|-----|
| Caracteres corrompidos após o carregamento | `LoadOptions` não definido ou nome de charset errado | Garanta que `loadOptions.setEncoding(Charset.forName("Big5"))` corresponda à página de código do arquivo fonte. |
| `UnsupportedEncodingException` | Nome do charset escrito incorretamente | Use o nome exato listado em `Charset.availableCharsets()`. |
| Arquivo de saída ainda mostra mojibake | Salvo em formato legado (por exemplo, `.rtf`) sem opções UTF‑8 | Use `TxtSaveOptions` com `setEncoding("UTF-8")` ou salve como `.docx`. |
| Desempenho reduzido em arquivos grandes | Recriar `LoadOptions` para cada documento | Reutilize uma única instância `LoadOptions` ao processar muitos arquivos com a mesma codificação fonte. |

## Conclusão

Agora você sabe como **configurar a codificação LoadOptions** em Java para ler documentos codificados legacy e como **alterar a codificação do documento para UTF-8** para consumo seguro downstream. A abordagem funciona para qualquer página de código suportada pela classe `Charset` do Java, tornando‑a uma solução flexível para aplicações multilíngues.

Em seguida, você pode explorar:

* **Conversão em lote** – percorrer uma pasta de documentos e aplicar a mesma lógica de codificação.  
* **Detecção de codificação** – usar bibliotecas como juniversalchardet para detectar automaticamente o charset de origem antes de configurar `LoadOptions`.  
* **Preservação de formatação** – experimentar salvar em PDF ou HTML mantendo a conformidade UTF‑8.

Sinta‑se à vontade para adaptar o código à arquitetura do seu projeto e deixar a robusta API Aspose.Words lidar com o trabalho pesado de manipulação de documentos.

![Code snippet showing configuration of LoadOptions encoding and document save](/images/encoding-demo.png){: .align-center alt="Configurar a codificação LoadOptions em exemplo de código Java"}

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Como converter texto RTF com codificação UTF-8 em Java usando Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Recuperar documento Word DOCX corrompido usando Aspose.Words LoadOptions – Guia Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}