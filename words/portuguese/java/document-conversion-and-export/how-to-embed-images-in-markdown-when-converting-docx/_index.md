---
category: general
date: 2026-01-11
description: Aprenda como incorporar imagens em Markdown ao converter um arquivo DOCX,
  usando Base64 para imagens pequenas e salvando recursos maiores separadamente.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: pt
og_description: Aprenda a incorporar imagens em Markdown ao converter um arquivo DOCX,
  usando Base64 para imagens pequenas e salvando recursos maiores separadamente.
og_title: Como Incorporar Imagens em Markdown ao Converter DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: Como incorporar imagens em Markdown ao converter DOCX
url: /pt/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Incorporar Imagens em Markdown ao Converter DOCX

Já se perguntou **como incorporar imagens** em um arquivo Markdown que se origina de um documento Word? Você não está sozinho. A maioria dos desenvolvedores encontra um obstáculo quando a conversão remove imagens ou as armazena de forma que quebra o layout final.  

Neste guia, percorreremos um exemplo completo, pronto‑para‑executar, que mostra **como incorporar imagens** como URIs de dados Base64 para gráficos pequenos, enquanto ativos maiores são gravados em uma pasta lateral. Ao longo do caminho, também abordaremos **convert docx to markdown**, falaremos sobre **how to convert docx** com Aspose.Words e explicaremos a diferença entre incorporar imagens como Base64 versus exportá‑las como arquivos separados.  

> **Dica profissional:** Se você só precisa de uma prova de conceito rápida, o código abaixo funciona pronto para uso com uma única dependência Maven.

---

## O que Você Precisa

- **Java 17** (ou qualquer JDK recente) – a API é centrada em Java, mas os conceitos se traduzem para outras linguagens.
- **Aspose.Words for Java** – uma biblioteca comercial que suporta a conversão DOCX → Markdown.
- Um **sample DOCX** contendo uma mistura de ícones pequenos e fotos maiores.
- Uma pasta onde você deseja que o Markdown e seus recursos residam.

Sem frameworks adicionais, sem scripts externos. Apenas Java puro e Aspose.Words.

---

## Etapa 1 – Adicionar Aspose.Words ao Seu Projeto (convert docx to markdown)

Se você estiver usando Maven, insira o trecho a seguir no seu `pom.xml`. Sinta‑se à vontade para substituir a versão pela última liberação disponível no momento da leitura.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Por que isso importa:** Aspose.Words cuida do trabalho pesado de analisar a estrutura DOCX, extrair imagens e renderizar a sintaxe Markdown. Tentar criar seu próprio analisador seria um buraco negro que provavelmente você não precisa entrar.

---

## Etapa 2 – Carregar o Documento DOCX Fonte

Primeiro, aponte a API para o arquivo Word que você deseja transformar. O construtor `Document` faz todo o trabalho — sem necessidade de análise XML manual.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Observe que o comentário explica *por que* esta linha é crucial: sem uma instância `Document` não há nada para converter.

---

## Etapa 3 – Preparar MarkdownSaveOptions com um Callback de Salvamento de Recurso

Este é o coração de **como incorporar imagens** corretamente. O callback fornece um ponto de extensão para cada recurso (imagem, estilo, etc.) que o conversor deseja gravar.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Por que um callback?

- **Controle:** Você decide se uma imagem se torna uma string Base64 embutida ou um arquivo separado.
- **Desempenho:** Ícones pequenos se tornam parte do Markdown, eliminando requisições HTTP extras.
- **Portabilidade:** Imagens maiores permanecem como arquivos externos, mantendo o tamanho do Markdown razoável.

---

## Etapa 4 – Salvar o Documento como Markdown

Finalmente, instrua o Aspose.Words a gravar o arquivo Markdown usando as opções que acabamos de configurar.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Executar o programa produz duas coisas:

1. `output.md` – a representação Markdown do seu DOCX original.
2. Uma pasta `markdown_resources` contendo quaisquer imagens grandes que não foram incorporadas.

---

## Exemplo Completo Funcional (Todas as Etapas em Um Só Lugar)

Abaixo está o arquivo fonte completo, pronto para copiar‑colar no seu IDE. Substitua `YOUR_DIRECTORY` pelo caminho real na sua máquina.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Saída esperada:** Abra `output.md` em qualquer visualizador Markdown. Ícones pequenos aparecem embutidos, por exemplo:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Imagens maiores são referenciadas assim:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

Isso é exatamente o que você precisa para **incorporar imagens** enquanto ainda mantém o tamanho do arquivo manejável.

---

## Perguntas Frequentes & Casos Limítrofes

### E se uma imagem for JPEG ao invés de PNG?

O callback acima sempre prefixa a URI com `image/png`. Para JPEGs, você pode inspecionar os primeiros bytes de `args.getData()` ou usar `args.getFileName()` para inferir o tipo MIME correto:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Posso mudar o limite de tamanho?

Claro. O limite de `10_000` bytes é apenas um exemplo. Se você tem uma largura de banda generosa, aumente para 50 KB ou mais. Por outro lado, diminua se precisar de arquivos Markdown ultra‑leves.

### Isso funciona com tabelas ou outros objetos do Word?

Sim. Aspose.Words converte automaticamente tabelas, listas e até notas de rodapé para Markdown. O callback de recurso intercepta apenas imagens, portanto você não precisa de código extra para outros elementos.

### E quanto a nomes de arquivos não‑ASCII?

A API codifica com segurança nomes de arquivos Unicode ao gravar na pasta `markdown_resources`. Apenas certifique‑se de que seu sistema de arquivos suporta UTF‑8 (a maioria dos sistemas operacionais modernos suporta).

---

## Dicas Profissionais para uma Conversão Suave

- **Mantenha a pasta de saída limpa.** Execute `Files.createDirectories` apenas uma vez por conversão, ou exclua a pasta antes de cada execução se quiser um início limpo.
- **Valide o Markdown.** Ferramentas como `markdown` podem capturar caracteres estranhos introduzidos por strings Base64 malformadas.
- **Trave a versão do Aspose.Words.** Uma versão específica garante que seu código continue funcionando mesmo após uma grande mudar o comportamento padrão.
- **Use uma entrada .gitignore** para `markdown_resources/

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}