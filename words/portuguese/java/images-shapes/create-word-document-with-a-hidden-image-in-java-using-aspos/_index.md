---
category: general
date: 2026-09-24
description: Crie um documento Word em Java e aprenda como ocultar imagem, adicionar
  imagem ao Word e inserir imagem oculta com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to hide image
- add image word
- how to hide shape
- insert hidden picture
language: pt
lastmod: 2026-09-24
og_description: Crie documento Word em Java e descubra como ocultar imagem, adicionar
  imagem ao Word e inserir imagem oculta usando Aspose.Words.
og_image_alt: Screenshot of a create word document example with a hidden image
og_title: Criar documento Word com uma imagem oculta – guia passo a passo em Java
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Create word document in Java and learn how to hide image, add image
    word, and insert hidden picture with Aspose.Words.
  headline: Create word document with a hidden image in Java using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Criar documento Word com uma imagem oculta em Java usando Aspose.Words
url: /pt/java/images-shapes/create-word-document-with-a-hidden-image-in-java-using-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word com uma imagem oculta em Java usando Aspose.Words

Se você precisa **criar documento Word** programaticamente, o Aspose.Words para Java torna isso simples. Este tutorial mostra **como ocultar imagem**, **adicionar imagem ao Word** e **inserir imagem oculta** em um único documento mantendo o layout limpo.

A automação de documentos frequentemente requer a inserção de logotipos, marcas d'água ou marcadores de posição que não devem atrapalhar o conteúdo visível. Ao marcar uma forma como oculta, você mantém a imagem no arquivo para uso posterior (por exemplo, para geração condicional de conteúdo) sem mostrá‑la ao usuário final. Você percorrerá todo o fluxo de trabalho, desde a inicialização de um documento até a gravação do arquivo final `.docx`.

## O que você vai aprender

* Como **criar documento Word** do zero usando `Document` e `DocumentBuilder`.
* Os passos exatos para **adicionar imagem ao Word** e então ocultar essa imagem com o método `setHidden(true)`.
* Como a técnica **como ocultar forma** funciona nos bastidores e por que ela é confiável em diferentes versões do Word.
* Maneiras de **inserir imagem oculta** para que a imagem permaneça no arquivo, mas fique invisível no layout.
* Armadilhas comuns, como caminhos de arquivo incorretos, formatos de imagem não suportados e como verificar se a imagem está realmente oculta.

> **Pré‑requisitos** – Você precisa do Java 8+ instalado, um projeto Maven ou Gradle e uma licença válida do Aspose.Words para Java (ou uma licença de avaliação gratuita). Nenhuma outra biblioteca externa é necessária.

## Criar documento Word e inserir uma imagem oculta

A primeira etapa é instanciar um novo objeto `Document`. Esse objeto representa todo o arquivo Word na memória.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa*: `Document` é o contêiner para todas as partes de um arquivo Word (estilos, seções, imagens, etc.). `DocumentBuilder` fornece uma API fluente para adicionar conteúdo sem lidar com estruturas Open XML de baixo nível.

## Como ocultar imagem usando propriedades da forma

Imagens em um documento Word são armazenadas como objetos `Shape`. Definir a flag `Hidden` indica ao Word que a forma deve ser excluída do layout, preservando‑a no arquivo.

```java
        // Step 3: Insert an image into the document
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // Step 4: Mark the inserted shape as hidden so it won't appear in the layout
        imageShape.setHidden(true);
```

*Explicação*:  
* `insertImage` cria uma `Shape` do tipo `Picture`.  
* `setHidden(true)` alterna o atributo “Hidden” do Word, que é respeitado pelo motor de layout. A imagem permanece incorporada, podendo ser revelada posteriormente programaticamente ou via interface do Word.

> **Dica profissional**: Use PNG para qualidade sem perdas e mantenha o tamanho da imagem modesto (menos de 200 KB) para evitar inflar o arquivo `.docx`.

## Adicionar imagem ao Word e verificar o status oculto

Embora a imagem esteja oculta, você pode ainda querer referenciá‑la no texto do documento (por exemplo, “Logotipo da empresa”). É possível adicionar uma legenda ou um parágrafo marcador antes de ocultar a forma.

```java
        // Optional: Add a caption that explains the hidden image
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)"); // This text is visible
```

*Por que você pode fazer isso*: Alguns fluxos de trabalho exigem um marcador textual para que processos subsequentes localizem a imagem oculta sem analisar as partes binárias do documento.

## Inserir imagem oculta e salvar o arquivo

Por fim, persista o documento no disco. A imagem oculta permanece incorporada, mas invisível quando o arquivo é aberto no Microsoft Word.

```java
        // Step 5: Save the document with the hidden shape
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

*Verificação*: Abra `HiddenShapeDemo.docx` no Word. Você deverá ver a legenda “Logotipo da empresa (oculto)”, mas nenhuma imagem visível. Para confirmar que a imagem existe, abra o arquivo como um arquivo ZIP (`.docx` são contêineres ZIP) e inspecione `word/media`. O PNG que você adicionou estará presente.

## Casos de borda comuns e como tratá‑los

| Situação | O que observar | Correção recomendada |
|-----------|-------------------|-----------------|
| **Caminho de imagem inválido** | `FileNotFoundException` em `insertImage` | Use `Paths.get(...).toAbsolutePath()` ou verifique `Files.exists()` antes da inserção. |
| **Formato de imagem não suportado** (ex.: BMP) | Aspose lança `UnsupportedImageFormatException` | Converta a imagem para PNG ou JPEG antes de chamar `insertImage`. |
| **Flag oculto ignorada** (versões raras do Word) | A imagem ainda aparece no layout | Garanta que está usando Aspose.Words 22.9+ onde `setHidden` mapeia para o atributo OOXML correto (`<w:hidden/>`). |
| **Tamanho de imagem grande** | Documento fica lento | Redimensione a imagem usando `imageShape.setWidth(100); imageShape.setHeight(50);` antes de ocultá‑la. |

## Exemplo completo, executável

Abaixo está o programa completo que você pode copiar, ajustar os caminhos e executar diretamente.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document document = new Document();

        // 2. Prepare a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Insert the image (replace with your actual file)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // 4. Hide the shape so it doesn't affect layout
        imageShape.setHidden(true);

        // 5. (Optional) Add a visible caption for context
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)");

        // 6. Save the result
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

**Saída esperada**: Ao abrir `HiddenShapeDemo.docx` no Microsoft Word, o documento contém o texto “Logotipo da empresa (oculto)” e nenhuma imagem visível. O PNG oculto pode ser confirmado dentro da pasta `word/media` do `.docx` compactado.

## Como ocultar forma vs. como ocultar imagem

Na terminologia do Word, tanto imagens quanto desenhos são tratados como **formas**. O método `setHidden(true)` funciona para qualquer tipo de forma, portanto a mesma abordagem se aplica a gráficos vetoriais, caixas de texto ou gráficos. Se precisar ocultar uma forma que não seja imagem, basta obter a referência `Shape` (por exemplo, via `builder.insertShape(ShapeType.LINE, 100, 0)`) e chamar `setHidden(true)`.

## Próximos passos e tópicos relacionados

* **Substituir imagem oculta em tempo de execução** – Carregue o documento posteriormente, localize a forma oculta pelo seu `Name` ou `AlternativeText` e troque os dados da imagem.  
* **Conteúdo condicional** – Combine formas ocultas com Mail Merge para mostrar ou ocultar imagens com base em campos de dados.  
* **Trabalhando com WordprocessingML** – Inspecione o XML subjacente (`<w:pict>` e `<w:hidden/>`) se precisar de ajustes de baixo nível.  

Essas extensões permitem que você construa pipelines sofisticados de geração de documentos enquanto mantém a lógica central de **criar documento Word** limpa e fácil de manter.

---

*Agora você sabe como criar um documento Word, adicionar uma imagem e ocultar essa imagem usando Aspose.Words para Java. Experimente inserir múltiplas imagens ocultas, alternar sua visibilidade ou integrar a técnica em um sistema de relatórios maior.*

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Insert Inline Image In Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert Floating Image In Word Document](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}