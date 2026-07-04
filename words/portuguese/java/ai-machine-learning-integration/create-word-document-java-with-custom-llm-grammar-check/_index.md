---
category: general
date: 2026-05-04
description: Crie documentos Word em Java usando Aspose.Words e aprenda como verificar
  a gramática com um LLM personalizado. Guia passo a passo para desenvolvedores Java.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: pt
og_description: Crie um documento Word em Java e veja como verificar a gramática usando
  um LLM personalizado. Tutorial completo de Java com código executável.
og_title: Criar documento Word em Java com verificação gramatical personalizada LLM
tags:
- Java
- Aspose.Words
- LLM
title: Criar documento Word em Java com verificação gramatical personalizada LLM
url: /pt/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word java com Verificação Gramatical de LLM Personalizado

Já se perguntou como **create word document java** projetos que também se revisam? Você não está sozinho—muitos desenvolvedores querem um pipeline único que gere um arquivo *.docx* polido sem precisar de várias ferramentas. Neste tutorial vamos percorrer exatamente isso, mostrando **how to create docx** arquivos com Aspose.Words, conectar um LLM hospedado localmente e, finalmente, **how to check grammar** automaticamente. Ao final, você terá um programa Java autônomo que escreve, valida e salva um documento Word—tudo enquanto **using custom LLM** endpoints que você controla.

## O que você precisará

Antes de mergulharmos, certifique‑se de que você tem o seguinte em sua estação de trabalho:

| Pré‑requisito | Por que é importante |
|--------------|-----------------------|
| Java 17+ (or any recent JDK) | Recursos modernos da linguagem e melhor suporte a módulos |
| Aspose.Words for Java (latest version) | A biblioteca que permite **create word document java** arquivos programaticamente |
| A locally hosted LLM server (e.g., Ollama, LMStudio) listening on `http://localhost:11434/api/generate` | Necessário para o passo **use custom llm** que alimenta a verificação gramatical |
| Maven or Gradle (we’ll use Maven in examples) | Simplifica o gerenciamento de dependências |
| An IDE or text editor (IntelliJ IDEA, VS Code, etc.) | Facilita a codificação e depuração |

Se algum desses parecer desconhecido, não entre em pânico—cada item é gratuito ou tem uma edição comunitária que funciona perfeitamente para fins de aprendizado.

## Etapa 1 – Configurar seu projeto Maven

Para **create word document java** projetos rapidamente, comece com um `pom.xml` Maven mínimo. Este arquivo inclui a biblioteca Aspose.Words e qualquer cliente HTTP que você prefira (usaremos Apache HttpClient).

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Dica profissional:** Se você estiver usando Gradle, as mesmas dependências vão sob `implementation` em `build.gradle`.

Agora execute `mvn clean install` para baixar os jars. Quando a compilação for bem‑sucedida, você estará pronto para escrever código Java que **creates word document java** arquivos.

## Etapa 2 – Escrever a classe Java que **Creates word document java**

Abaixo está o arquivo‑fonte completo, pronto para execução. Ele demonstra todo o fluxo: inicializar um documento em branco, configurar um endpoint LLM personalizado, invocar a verificação gramatical e, finalmente, salvar o resultado.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Por que isso funciona:**  
> * `Document` é a classe central do Aspose.Words que representa um *.docx* na memória.  
> * `AiEndpoint` informa ao módulo de IA da Aspose onde enviar o prompt. Ao apontá‑lo para `localhost:11434` nós **use custom llm** em vez de um serviço em nuvem.  
> * `checkGrammar` com `AiModelType.CUSTOM` encaminha o texto do documento ao LLM, recebe o texto corrigido e reescreve os nós subjacentes do Word.  
> * Por fim, chamamos `save` para gravar o arquivo no disco, fornecendo a você um documento Word polido.

### Saída esperada

Depois de executar `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` você deverá ver:

```
Document saved to output/GrammarChecked.docx
```

Abra o `GrammarChecked.docx` resultante no Microsoft Word (ou LibreOffice). A frase original *“Ths sentence has a typo and a grammer error.”* agora aparecerá como *“This sentence has a typo and a grammar error.”* – prova de que o passo **how to check grammar** foi bem‑sucedido.

## Etapa 3 – Como criar docx com conteúdo diferente (Opcional)

Se você quiser gerar documentos mais ricos—tabelas, imagens ou texto formatado—basta continuar usando `DocumentBuilder`. Aqui está um trecho rápido que demonstra a adição de um título e de uma tabela:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

Você pode inserir esse código em qualquer lugar entre o bloco de criação do documento (Etapa 2.1) e a chamada de verificação gramatical (Etapa 2.3). O LLM ainda receberá o texto completo, podendo corrigir as partes em linguagem natural enquanto deixa as tabelas intactas.

## Etapa 4 – Lidando com problemas de endpoint (Use Custom LLM com segurança)

Quando **using custom llm** endpoints, alguns contratempos são comuns:

| Sintoma | Causa provável | Correção |
|---------|----------------|----------|
| `Connection refused` error | LLM server not running or wrong port | Start Ollama (`ollama serve`) and verify `http://localhost:11434/api/generate` works with `curl`. |
| Response JSON missing `completion` field | Model name mismatch | Ensure the model you set (`llama3.1:8b`) is installed (`ollama list`). |
| Grammar check returns the original text unchanged | Prompt not recognized by LLM | Adjust the model’s system |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}