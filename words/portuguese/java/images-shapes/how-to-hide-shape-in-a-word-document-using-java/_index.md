---
category: general
date: 2026-10-04
description: Aprenda como ocultar formas no Word com Java. Este guia passo a passo
  mostra como ocultar formas no Word, tornar a forma invisível no Word e ocultar formas
  no Microsoft Word programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: pt
lastmod: 2026-10-04
og_description: Como ocultar forma no Word com Java. Siga este guia para ocultar forma
  no Word, tornar a forma invisível no Word e ocultar forma no Microsoft Word em poucas
  linhas de código.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Como ocultar forma em um documento Word usando Java – guia completo
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: Como ocultar forma em um documento Word usando Java
url: /pt/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como ocultar forma em um documento Word usando Java

Se você precisar ocultar uma forma em um arquivo Word, este guia mostra exatamente **como ocultar forma** programaticamente. Seja gerando relatórios, limpando modelos ou preparando documentos para conformidade, você pode tornar uma forma invisível sem removê‑la da estrutura do arquivo.

Nas seções abaixo, você aprenderá como ocultar forma no Word, tornar forma invisível no Word e ocultar forma no Microsoft Word usando a biblioteca Aspose.Words for Java. O tutorial pressupõe que você tenha conhecimentos básicos de Java e um ambiente de desenvolvimento Java funcional.

## Pré-requisitos

* Java Development Kit (JDK) 8 ou mais recente  
* Maven ou Gradle para gerenciamento de dependências  
* Aspose.Words for Java (versão 23.9 ou posterior) – adicione a coordenada Maven `com.aspose:aspose-words:23.9`  
* Um documento Word (`input.docx`) que contém ao menos uma forma (por exemplo, uma imagem, caixa de texto ou SmartArt)

## Etapa 1: Configurar o projeto e importar Aspose.Words

Crie um novo projeto Maven ou adicione a dependência Aspose.Words a um projeto existente.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

A biblioteca fornece as classes `Document`, `NodeType` e `Shape` usadas nas etapas seguintes. Importe‑as no início do seu arquivo fonte Java:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## Etapa 2: Carregar o documento Word

Carregar o documento é a primeira etapa em qualquer fluxo de trabalho de processamento de Word. O construtor `Document` lê o arquivo para a memória, preservando todos os nós, incluindo formas ocultas.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Por que isso importa*: Carregar o arquivo cria um DOM (Document Object Model) que permite navegar, consultar e modificar nós individuais, como formas, parágrafos ou tabelas.

## Etapa 3: Recuperar a forma alvo

Se o documento contém várias formas, você pode localizar uma específica por índice, nome ou outros critérios. Para uma demonstração rápida, o exemplo obtém a primeira forma na hierarquia do documento, incluindo formas que estão aninhadas dentro de tabelas ou grupos.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Por que isso importa*: O método `getChild` com `true` para o parâmetro `isDeep` percorre toda a árvore de nós, garantindo que você capture formas que não são filhos diretos do corpo do documento.

## Etapa 4: Ocultar a forma

Definir a propriedade `Hidden` como `true` indica ao Microsoft Word que exclua a forma da renderização do layout, mantendo‑a na estrutura do documento. A forma não será visível quando o arquivo for aberto no Word, mas permanecerá acessível para processamento posterior.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*Por que isso importa*: Ocultar uma forma é útil quando você precisa preservar a forma para ativação posterior (por exemplo, conteúdo condicional, versionamento) sem exibi‑la ao usuário final.

## Etapa 5: Salvar o documento modificado

Após alterar a visibilidade da forma, grave o documento de volta ao disco. Você pode sobrescrever o arquivo original ou criar um novo; o exemplo grava em `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

Ao abrir `HiddenShape.docx` no Microsoft Word, a forma ficará invisível, porém o layout do documento refletirá seu estado oculto (sem espaço em branco extra).

## Exemplo completo executável

Juntando todas as etapas resulta em um programa autônomo que você pode compilar e executar diretamente.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Resultado esperado**  
Executar o programa gera `HiddenShape.docx`. Abrir esse arquivo no Microsoft Word mostra o conteúdo original, mas a forma que estava presente em `input.docx` não está mais visível. A estrutura do documento ainda contém o nó da forma, que pode ser desocultado posteriormente definindo `shape.setHidden(false)`.

## Por que ocultar uma forma em vez de excluí‑la?

* **Preservar metadados** – Formas frequentemente contêm texto alternativo, hyperlinks ou dados personalizados que você pode precisar mais tarde.  
* **Exibição condicional** – Em cenários de mala‑direta ou geração de relatórios, você pode mostrar a forma apenas para destinatários específicos.  
* **Controle de versão** – Manter a forma oculta permite manter um único modelo enquanto alterna a visibilidade programaticamente.

## Variações comuns e casos extremos

| Situação | Ajuste recomendado |
|-----------|------------------------|
| Múltiplas formas, necessidade de uma específica | Use `doc.getChild(NodeType.SHAPE, index, true)` com o índice apropriado, ou itere através de `doc.getChildNodes(NodeType.SHAPE, true)` e compare com `shape.getName()` ou `shape.getAlternativeText()`. |
| Forma está dentro de um GroupShape | A busca profunda (`true`) já alcança dentro de grupos, mas pode ser necessário fazer cast para `GroupShape` primeiro se você pretende ocultar apenas um membro do grupo. |
| Deseja ocultar todas as formas | Percorra todos os nós de forma e chame `setHidden(true)` dentro do loop. |
| Compatibilidade com versões mais antigas do Word | A flag `Hidden` é suportada desde o Word 2000. Formatos mais antigos (`.doc`) também a respeitam, mas teste na versão alvo se encontrar alterações inesperadas no layout. |

**Dica profissional:** Depois de ocultar uma forma, você pode chamar `doc.updatePageLayout()` se precisar que o layout da página seja recalculado antes de salvar. Isso raramente é necessário porque o Word reflowa automaticamente o conteúdo ao abrir, mas pode ser útil para geração de pré‑visualização no lado do servidor.

## Testando o resultado programaticamente

Se você quiser confirmar que a forma está oculta sem abrir o Word, pode consultar a propriedade após salvar:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## Próximos passos

Agora que você sabe como ocultar forma no Word, considere estes tópicos relacionados:

* **Ocultar forma no Word com base em condições personalizadas** – Combine a flag `Hidden` com campos de mala‑direta para alternar a visibilidade por destinatário.  
* **Tornar forma invisível no Word usando VBA** – Para automação no dispositivo, a mesma propriedade pode ser definida via VBA (`Shape.Visible = msoFalse`).  
* **Ocultar forma no Microsoft Word em massa** – Processar uma pasta de documentos com um loop que aplica o mesmo código a cada arquivo.  

Explorar essas extensões aprofundará seu controle sobre a automação de documentos Word e manterá seus arquivos gerados limpos e profissionais.

--- 

*Este tutorial segue o Google Developer Documentation Style Guide, usa voz ativa, perspectiva de segunda pessoa e fornece uma solução completa e digna de citação tanto para motores de busca quanto para assistentes de IA.*

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma retangular no Word com Java – Guia Completo](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Adicionar sombra a forma no Word – Guia Completo Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}