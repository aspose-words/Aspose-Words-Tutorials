---
category: general
date: 2026-09-27
description: Crie um docx contendo ActiveX em Java usando Aspose.Words. Aprenda a
  inserir um botão de comando ActiveX passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: pt
lastmod: 2026-09-27
og_description: Criar docx contendo ActiveX em Java com Aspose.Words. Siga este guia
  para inserir um botão de comando ActiveX e salvar o documento.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Criar docx contendo ActiveX em Java – guia completo
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Como criar docx contendo ActiveX com Java e Aspose.Words
url: /pt/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar docx contendo ActiveX com Java e Aspose.Words

Se você precisa **criar docx contendo ActiveX**, este guia mostra uma solução completa. Você aprenderá como **inserir um botão de comando ActiveX** em um arquivo Word usando Aspose.Words for Java, e então salvar o resultado como um .docx que pode ser aberto no Microsoft Word.

Gerar um documento Word programaticamente evita a edição manual e garante consistência em relatórios, contratos ou modelos de formulários. As etapas abaixo cobrem tudo, desde a configuração do projeto até o tratamento de armadilhas comuns, para que você possa integrar a técnica em qualquer aplicação Java.

## Pré-requisitos

* Java Development Kit (JDK) 8 ou superior instalado.
* Maven 3.6+ (ou outra ferramenta de construção que preferir).
* Um arquivo de licença do Aspose.Words for Java (a avaliação gratuita funciona para testes).
* Microsoft Word instalado na máquina alvo se você quiser verificar visualmente o controle ActiveX.

Esses itens são necessários porque o Aspose.Words fornece a API que cria o documento, enquanto o Word é necessário para renderizar o controle ActiveX.

## Etapa 1: Configurar o projeto Maven

Crie um novo projeto Maven ou adicione a dependência do Aspose.Words a um `pom.xml` existente:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Dica profissional:** Mantenha a versão do Aspose.Words sincronizada com as notas de versão oficiais para se beneficiar de correções de bugs e novos recursos ActiveX.

## Etapa 2: Escrever o código Java que cria o documento

Crie uma classe chamada `ActiveXDocxCreator`. O código abaixo inclui todas as importações necessárias, um método `main` e comentários detalhados que explicam cada operação.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Por que cada linha importa

* `Document` é o contêiner para todo o conteúdo do Word. Criar uma nova instância fornece uma tela limpa.
* `DocumentBuilder` fornece uma API fluente para inserir elementos; ela rastreia automaticamente o ponto de inserção.
* `insertForms2OleControl()` cria um placeholder genérico de controle OLE. O Aspose.Words o trata como um contêiner ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` informa ao Word que o placeholder deve ser renderizado como um CommandButton.
* `setCaption("Click Me")` define o texto exibido no botão.
* `setLeft` e `setTop` posicionam o botão em relação às margens da página. Ajuste esses valores conforme seu layout.
* `setWidth` e `setHeight` são opcionais, mas melhoram a aparência do botão, especialmente quando o tamanho padrão é muito pequeno.
* `doc.save` grava a estrutura em memória em um arquivo .docx físico que o Word pode abrir.

## Etapa 3: Verificar o documento gerado

Abra `output/ActiveXCommandButton.docx` no Microsoft Word:

1. O documento deve exibir uma única página com um botão rotulado **Click Me** posicionado próximo ao canto superior esquerdo.
2. Se o botão não aparecer, verifique se **os controles ActiveX estão habilitados** no Centro de Confiabilidade do Word (Arquivo → Opções → Centro de Confiabilidade → Configurações do Centro de Confiabilidade → Configurações de ActiveX).
3. O botão funciona apenas nas versões do Word para Windows que suportam ActiveX. No macOS ou no Word baseado na web, o controle será exibido como uma imagem estática.

## Etapa 4: Tratando casos de borda comuns

| Situação | Motivo | Ação recomendada |
|-----------|--------|--------------------|
| O botão está ausente ao abrir o arquivo | As configurações de segurança do Word bloqueiam ActiveX | Habilite “Executar todos os controles sem restrições” para locais confiáveis. |
| O .docx gerado não pode ser aberto | Versão incompatível do Aspose.Words | Atualize para a versão mais recente do Aspose.Words; versões antigas podem não incorporar as partes OLE necessárias corretamente. |
| Você precisa que o botão execute uma macro | ActiveX sozinho não contém código de macro | Combine o controle ActiveX com uma macro VBA que trate o evento `Click`. Use o método `DocumentBuilder.insertOleObject` para incorporar um modelo habilitado para macro. |
| O layout fica desalinhado em diferentes tamanhos de página | As coordenadas são pontos absolutos | Use `builder.getPageSetup().setPageWidth` e `setPageHeight` para padronizar o tamanho da página antes de posicionar o controle. |

## Etapa 5: Estendendo a solução

Você pode inserir outros controles ActiveX alterando o enum `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

O Aspose.Words também suporta a inserção de **caixas de texto ActiveX**, **list boxes** e **combo boxes**. Os mesmos métodos de posicionamento (`setLeft`, `setTop`, `setWidth`, `setHeight`) se aplicam.

Se precisar colocar múltiplos controles, chame `builder.insertForms2OleControl()` repetidamente e ajuste as coordenadas de cada controle conforme necessário.

## Arquivo de código completo

Abaixo está o arquivo completo `ActiveXDocxCreator.java` pronto para copiar‑e‑colar:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Executar este programa produz um **docx contendo ActiveX** que você pode distribuir aos usuários finais que precisam de formulários interativos.

## Conclusão

Agora você sabe como **criar docx contendo ActiveX** usando Java e Aspose.Words, e como **inserir um botão de comando ActiveX** programaticamente. O tutorial abordou a configuração do projeto, o código-fonte completo, etapas de verificação e estratégias para lidar com problemas típicos.

A partir daqui, você pode explorar:

* Adicionar macros VBA para responder ao clique do botão.
* Incorporar outros controles ActiveX, como caixas de seleção ou combo boxes.
* Automatizar a geração de formulários de várias páginas com dados dinâmicos.

Experimente diferentes coordenadas, tamanhos e tipos de controle para adequar ao layout específico do seu documento. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}