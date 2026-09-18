---
category: general
date: 2026-09-18
description: Crie um documento em branco e insira formas no Word com Aspose.Words
  – aprenda como adicionar uma forma de triângulo e muito mais.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: pt
lastmod: 2026-09-18
og_description: Crie um documento em branco no Word usando Aspose.Words e aprenda
  a inserir uma forma de triângulo, agrupar formas e outros gráficos. Siga este guia
  completo.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Crie um documento em branco e adicione formas ao Word – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Como criar um documento em branco e adicionar formas ao Word
url: /pt/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento em branco e adicionar formas ao Word

Se você precisa **criar documento em branco** e depois enriquecê-lo com gráficos, este guia mostra exatamente como fazer. Vamos percorrer a criação de um arquivo Word do zero e **adicionar formas ao Word**, incluindo **como inserir forma de triângulo**, usando Aspose.Words for Java.

Você terminará o tutorial com um arquivo *.docx* pronto‑para‑uso que contém uma forma agrupada contendo um triângulo. As etapas cobrem tudo, desde a configuração do projeto até a gravação do **create word document** final. Nenhuma ferramenta externa é necessária além do Aspose.Words.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou posterior instalado  
* Maven ou Gradle para gerenciamento de dependências  
* Uma licença do Aspose.Words for Java (a avaliação gratuita funciona para esta demonstração)  

Se você preferir um sistema de build diferente, ajuste a sintaxe da dependência conforme necessário. O código funciona em qualquer plataforma que suporte Java.

## Criar documento em branco com Aspose.Words

A primeira operação é **criar documento em branco** na memória. Aspose.Words fornece a classe `Document` que representa um arquivo Word sem nenhum conteúdo.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

O construtor `new Document()` cria uma estrutura *.docx* vazia, que você pode posteriormente preencher com parágrafos, tabelas ou gráficos. Como o documento está em branco, você tem controle total sobre cada elemento que adicionar.

## Adicionar formas ao Word – inserindo uma forma de grupo

Uma forma de grupo permite tratar várias imagens como uma única unidade. Isso é útil quando você deseja mover ou redimensionar várias formas juntas.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` é a API principal para adicionar conteúdo. A chamada `insertGroupShape` cria um contêiner de 300 × 300 pontos (aproximadamente 4 × 4 polegadas). Após essa chamada, o cursor fica posicionado *dentro* do grupo, pronto para formas adicionais.

### Por que usar uma forma de grupo?

Agrupar mantém os gráficos relacionados alinhados e facilita a aplicação de formatação uniforme. Se você decidir mover o triângulo mais tarde, todo o grupo se moverá junto, preservando o layout.

## Como inserir forma de triângulo dentro do grupo

Agora abordamos **como inserir triângulo**. O triângulo é um dos valores embutidos de `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

A chamada `moveTo` garante que o ponto de inserção do builder seja o primeiro parágrafo do grupo. `insertShape` então adiciona um triângulo de 60 × 60 pontos. Como o cursor está dentro do grupo, o triângulo torna‑se um filho da forma de grupo.

**Dicas para adicionar forma de triângulo**:

* O tamanho é medido em pontos; 72 pontos equivalem a uma polegada. Ajuste as dimensões conforme o seu layout.  
* Se precisar de uma orientação diferente, use `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` para alinhar a forma dentro do grupo.  
* O triângulo herda os estilos de preenchimento e linha do grupo, a menos que você os sobrescreva com `shape.getFillColor()` ou `shape.getStrokeColor()`.

## Salvar o documento – create word document

Depois de construir os gráficos, você salva o arquivo. Esta etapa finaliza a operação **create word document**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` grava a representação em memória no disco como um documento Word padrão. Você pode abrir `ExtendedGroup.docx` no Microsoft Word, LibreOffice ou em qualquer visualizador que suporte o formato OOXML. O arquivo exibirá uma forma agrupada contendo um triângulo, exatamente como foi criado pelo código.

## Exemplo completo executável

Juntando todas as peças, aqui está o programa completo que você pode copiar, compilar e executar:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Resultado esperado

Ao abrir `ExtendedGroup.docx`, você verá uma única forma de grupo ocupando o centro da página. Dentro desse grupo, um pequeno triângulo aparece na posição padrão. O triângulo pode ser selecionado e movido como parte do grupo, confirmando que **add shapes to word** funcionou como esperado.

## Perguntas comuns e casos de borda

| Pergunta | Resposta |
|----------|----------|
| *Posso adicionar mais de uma forma dentro do grupo?* | Sim. Após inserir o triângulo, mantenha o cursor dentro do grupo e chame `builder.insertShape` novamente com um `ShapeType` diferente. |
| *E se eu precisar que o triângulo seja vermelho?* | Recupere o `Shape` retornado por `insertShape` e chame `shape.getFillColor().setColor(Color.RED)`. |
| *Isso funciona com arquivos .doc mais antigos?* | Aspose.Words salva no formato que você especificar. Use `doc.save("file.doc", SaveFormat.DOC)` para criar um documento Word legado. |
| *Como altero a borda do grupo?* | Use `group.getStrokeColor().setColor(Color.BLUE)` e `group.setLineWeight(2.0)` para personalizar o contorno. |
| *Existe uma maneira de girar o triângulo?* | Chame `shape.getRotation()` para definir um ângulo em graus. |

## Dicas profissionais

* **Reuse the builder** – criar um novo `DocumentBuilder` para cada forma adiciona sobrecarga. Mantenha um único builder por documento.  
* **Unit conversion** – se você trabalha com milímetros, converta‑os para pontos (`points = mm * 2.83465`).  
* **Performance** – para documentos grandes, chame `doc.updatePageLayout()` apenas uma vez após todas as formas serem adicionadas.  

## Conclusão

Agora você sabe como **criar documento em branco**, **adicionar formas ao Word**, e especificamente **como inserir forma de triângulo** usando Aspose.Words for Java. O exemplo completo demonstra o fluxo de trabalho completo, de um arquivo vazio até um **create word document** salvo que contém um triângulo agrupado.

A partir daqui, você pode explorar valores adicionais de `ShapeType`, aplicar estilos personalizados ou combinar múltiplos grupos para criar diagramas complexos. Experimente diferentes tamanhos, cores e posições para dominar a automação do Word em Java.

--- 

*Pronto para automatizar seu próximo relatório? Clone o exemplo, ajuste as dimensões e integre o código em sua própria aplicação hoje.*

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar documento Word em branco com forma de retângulo sombreado – Guia passo a passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Criar forma de retângulo no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}