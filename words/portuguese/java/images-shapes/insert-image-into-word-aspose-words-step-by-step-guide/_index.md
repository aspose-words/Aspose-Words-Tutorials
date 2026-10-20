---
category: general
date: 2026-07-26
description: Inserir imagem no Word usando Aspose.Words e aprender como ocultar a
  imagem no documento. Exemplo completo em Java com explicação passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert image into word
- hide shape in word
- hide image word
- how to hide image word
language: pt
lastmod: 2026-07-26
og_description: Insira imagem no Word com Aspose.Words e oculte a imagem no Word instantaneamente.
  Este guia orienta você através do código Java completo.
og_image_alt: Screenshot showing insert image into Word document using Aspose.Words
og_title: Inserir Imagem no Word – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert image into Word using Aspose.Words and learn how to hide image
    word in the document. Complete Java example with step-by-step explanation.
  headline: Insert Image into Word – Aspose.Words Step-by-Step Guide
  type: TechArticle
- description: Insert image into Word using Aspose.Words and learn how to hide image
    word in the document. Complete Java example with step-by-step explanation.
  name: Insert Image into Word – Aspose.Words Step-by-Step Guide
  steps:
  - name: 1. What if the image path is wrong?
    text: 'Aspose.Words throws `FileNotFoundException`. Wrap the `insertImage` call
      in a try‑catch block and give a clear error message:'
  - name: 2. Can I hide an **inline** image?
    text: 'Not directly. Inline images are stored as `InlineShape` objects and don’t
      expose a hidden property. If you must hide an inline picture, convert it to
      a `Shape` first:'
  - name: 3. Does the hidden flag affect PDF export?
    text: When you convert the Word file to PDF using Aspose.Words (`doc.save("out.pdf")`),
      hidden shapes are **not** rendered by default. If you need them in the PDF,
      call `doc.getLayoutOptions().setHideHiddenElements(false)` before saving.
  - name: 4. How to unhide the shape later?
    text: Simply set `picture.setHidden(false)` and resave. If you’re toggling visibility
      at runtime (e.g., a macro), you can locate the shape by its name or index and
      flip the flag.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Inserir Imagem no Word – Guia Passo a Passo do Aspose.Words
url: /pt/java/images-shapes/insert-image-into-word-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Imagem no Word – Guia Passo a Passo do Aspose.Words

Já se perguntou **como inserir imagem no Word** mantendo o arquivo organizado? Talvez você precise de um logotipo que permaneça oculto a menos que alguém o revele explicitamente. Neste tutorial vamos mostrar exatamente isso — como inserir uma imagem em um documento Word e, em seguida, ocultar a forma para que não atrapalhe o layout.  

Também abordaremos **ocultar forma no Word** e responderemos à comum pergunta “**como ocultar imagem word**” que surge ao automatizar relatórios ou contratos. Ao final, você terá um programa Java pronto‑para‑executar que realiza ambas as tarefas em uma única passagem limpa.

## Pré‑requisitos

Antes de começarmos, certifique‑se de que você tem:

- **Java 17** (ou qualquer JDK recente) instalado na sua máquina.  
- Biblioteca **Aspose.Words for Java** – você pode obter o JAR mais recente no Maven Central (`com.aspose:aspose-words:23.9` a partir de julho 2026).  
- Um **logo.png** (ou qualquer imagem) armazenado em algum lugar que você possa referenciar, por exemplo, `C:/temp/logo.png`.  
- Noções básicas de sintaxe Java – nada complexo é necessário.

Se algum desses itens lhe for desconhecido, pause e instale o JDK ou adicione a dependência do Aspose primeiro; o restante do guia assume que tudo já está configurado.

## Configuração do Projeto

Crie um novo projeto Maven (ou Gradle, se preferir) e adicione a dependência do Aspose.Words:

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Depois que o Maven resolver o JAR, você está pronto para escrever o código.

## Etapa 1: Inserir Imagem no Word

A primeira coisa que precisamos é um objeto `Document` novo e um `DocumentBuilder` que nos permita adicionar conteúdo. É aqui que a operação **insert image into word** acontece.

```java
import com.aspose.words.*;

public class InsertAndHideImage {
    public static void main(String[] args) throws Exception {

        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a convenient cursor to add elements
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the image as a Shape (not an InlineShape)
        // The path can be absolute or relative to the project root
        Shape picture = builder.insertImage("C:/temp/logo.png");

        // ------------------------------------------------------------
        // At this point the image is visible in the document layout.
        // ------------------------------------------------------------
```

**Por que usar `Shape` em vez de `InlineShape`?**  
Um `Shape` vive na camada de desenho, o que nos fornece o método `setHidden(true)` que precisaremos mais tarde. Imagens inline fazem parte do fluxo de texto e não expõem uma flag de ocultação, portanto não são adequadas para o cenário “hide image word”.

## Etapa 2: Ocultar Forma no Word

Agora que a imagem está na página, vamos ocultá‑la. Esta é a resposta central para **hide shape in word**.

```java
        // Hide the shape so it won’t appear in the layout
        picture.setHidden(true);

        // Optional: set wrap type to inline if you need it to behave like text
        // picture.setWrapType(WrapType.INLINE);
```

Definir `Hidden` como `true` indica ao Word que a forma deve ser tratada como objeto oculto. Na interface, os usuários podem alternar *Show hidden content* (Arquivo → Opções → Exibição) para visualizá‑la. Isso é exatamente o que você quer quando precisa de um logotipo que só aparece no modo “rascunho” ou quando uma macro o revela posteriormente.

## Etapa 3: Salvar o Documento

Concluímos persistindo o arquivo. O `.docx` resultante conterá a imagem oculta.

```java
        // Save the document to disk
        doc.save("C:/temp/HiddenShape.docx");

        System.out.println("Document created successfully with a hidden image.");
    }
}
```

Execute o programa (`mvn compile exec:java` ou o botão de execução da sua IDE). Abra `HiddenShape.docx` no Microsoft Word:

- Por padrão, você não verá o logotipo — perfeito para um layout limpo.  
- Se habilitar **Show hidden content**, a imagem aparecerá, confirmando que `setHidden(true)` funcionou.

## Etapa 4: Verificar a Imagem Oculta (Opcional)

Para completude, vamos adicionar uma rápida verificação que checa a flag oculta após recarregar o arquivo. Isso ajuda a responder “**how to hide image word**” quando você precisa confirmar programaticamente.

```java
        // Reload the document to verify hidden status
        Document loaded = new Document("C:/temp/HiddenShape.docx");
        Shape loadedPicture = (Shape) loaded.getChildNodes(NodeType.SHAPE, true).get(0);

        System.out.println("Is the picture hidden? " + loadedPicture.isHidden());
```

Executar este trecho imprime `true`, provando que o atributo oculto sobreviveu ao ciclo de ida‑e‑volta.

## Perguntas Frequentes & Casos Limite

### 1. E se o caminho da imagem estiver errado?

Aspose.Words lança `FileNotFoundException`. Envolva a chamada `insertImage` em um bloco try‑catch e forneça uma mensagem de erro clara:

```java
try {
    Shape picture = builder.insertImage("C:/temp/logo.png");
} catch (Exception e) {
    System.err.println("Image not found. Check the file path.");
    return;
}
```

### 2. Posso ocultar uma imagem **inline**?

Não diretamente. Imagens inline são armazenadas como objetos `InlineShape` e não expõem uma propriedade hidden. Se precisar ocultar uma imagem inline, converta‑a primeiro para um `Shape`:

```java
InlineShape inline = builder.insertImage("C:/temp/logo.png");
Shape shape = (Shape) inline.getParentNode();
shape.setHidden(true);
```

### 3. A flag oculta afeta a exportação para PDF?

Ao converter o arquivo Word para PDF usando Aspose.Words (`doc.save("out.pdf")`), formas ocultas **não** são renderizadas por padrão. Se precisar delas no PDF, chame `doc.getLayoutOptions().setHideHiddenElements(false)` antes de salvar.

### 4. Como tornar a forma visível novamente?

Basta definir `picture.setHidden(false)` e salvar novamente. Se você estiver alternando a visibilidade em tempo de execução (por exemplo, via macro), pode localizar a forma pelo nome ou índice e inverter a flag.

## Dicas Profissionais para Código Pronto para Produção

- **Use um nome descritivo** para a forma: `picture.setName("CompanyLogo");` — facilita buscas futuras.  
- **Armazene imagens como recursos** dentro do seu JAR e carregue‑as via `getResourceAsStream`, evitando caminhos de arquivo codificados.  
- **Envolva toda a operação em uma transação** (`doc.startTrackChanges()` / `doc.stopTrackChanges()`) se estiver editando um documento existente e precisar reverter em caso de erro.  
- **Habilite o modo de compatibilidade** (`doc.getCompatibilityOptions().setEnableLegacyBehavior(true)`) somente se você mirar versões muito antigas do Word; caso contrário, mantenha o padrão para melhor fidelidade.

## Exemplo Completo Funcional

Abaixo está a classe Java completa, autocontida, que você pode copiar‑colar em qualquer IDE. Ela inclui todos os imports, tratamento de erros e a etapa de verificação.



## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Insert Inline Image In Word Document](/words/english/net/add-content-using-documentbuilder/insert-inline-image/)
- [Insert Floating Image In Word Document](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}