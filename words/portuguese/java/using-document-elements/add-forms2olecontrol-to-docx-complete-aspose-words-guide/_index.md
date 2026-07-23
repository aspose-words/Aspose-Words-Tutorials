---
category: general
date: 2026-07-23
description: Aprenda como adicionar Forms2OleControl a DOCX usando Aspose.Words. Este
  guia passo a passo mostra como inserir um controle ActiveX CommandButton em Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: pt
lastmod: 2026-07-23
og_description: Adicione Forms2OleControl ao DOCX instantaneamente. Siga este guia
  prático para incorporar um CommandButton ActiveX usando Aspose.Words para Java.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: Adicionar Forms2OleControl ao DOCX – Tutorial Completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: Adicionar Forms2OleControl ao DOCX – Guia Completo do Aspose.Words
url: /pt/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar Forms2OleControl ao DOCX – Guia Completo do Aspose.Words

Já se perguntou como **adicionar Forms2OleControl ao DOCX** sem perder a cabeça? Você não está sozinho. Seja construindo um relatório baseado em modelo ou precisando de um botão clicável dentro de um arquivo Word, incorporar um controle ActiveX é o ingrediente secreto.

Neste tutorial vamos percorrer um exemplo concreto que **adiciona Forms2OleControl ao DOCX** com Aspose.Words para Java. Você verá o código completo, entenderá por que cada linha importa e receberá dicas para lidar com as peculiaridades que costumam atrapalhar os desenvolvedores.

## O que você vai aprender

- Como configurar o Aspose.Words em um projeto Java  
- Os passos exatos para **inserir um controle ActiveX no DOCX** (sim, a palavra‑chave principal novamente)  
- Configurar as propriedades de um CommandButton para que ele se comporte como um elemento de UI real  
- Salvar o documento e verificar se o controle está realmente incorporado  

Nenhuma experiência prévia com ActiveX é necessária, mas um entendimento básico de Java e Maven/Gradle tornará a jornada mais tranquila. Pronto? Vamos mergulhar.

---

## Etapa 1: Configurar o Aspose.Words no seu projeto

Antes de poder **adicionar Forms2OleControl ao DOCX**, você precisa da biblioteca Aspose.Words no classpath. A maneira mais fácil é via Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Dica profissional:** Se você estiver usando Gradle, o equivalente é `implementation 'com.aspose:aspose-words:24.9'`.  

Por que isso importa: o Aspose.Words fornece o método `DocumentBuilder.insertForms2OleControl()` que usaremos para **inserir um controle ActiveX no DOCX**. Sem a biblioteca, o compilador não saberia o que é um `Forms2OleControl`.

---

## Etapa 2: Adicionar Forms2OleControl ao DOCX

Agora vem o núcleo do tutorial—é aqui que realmente **adicionamos Forms2OleControl ao DOCX**. Criaremos um documento novo, instanciamos um `DocumentBuilder` e chamaremos o método de inserção.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**O que está acontecendo aqui?**  

- `new Document()` nos dá uma tela limpa. Pense nisso como uma folha em branco pronta para **inserir controle ActiveX no DOCX**.  
- `builder.insertForms2OleControl()` cria o contêiner OLE de baixo nível que o Aspose.Words chama *Forms2OleControl*. Esta é a única chamada de API que realmente **adiciona Forms2OleControl ao DOCX**.  
- Definir `OleControlType.COMMANDBUTTON` indica ao Word que o objeto OLE deve se comportar como um CommandButton clássico—exatamente como o botão que você arrastaria para um formulário no designer de UI.  
- Por fim, `document.save(...)` grava o arquivo .docx, persistindo o ActiveX incorporado.

---

## Etapa 3: Configurar as propriedades do CommandButton (Por que importa)

Inserir o controle simplesmente cria um espaço em branco. Para torná‑lo útil, você precisa definir algumas propriedades:

| Propriedade | Finalidade | Valor típico |
|-------------|------------|--------------|
| `setOleControlType` | Define o tipo de controle ActiveX (Button, CheckBox, etc.) | `OleControlType.COMMANDBUTTON` |
| `setName` | Identificador interno usado por macros do Word ou scripts VBA | `"MyButton"` |
| `setCaption` | Texto exibido na superfície do botão | `"Click Me"` |

Se você pular essas etapas, o botão aparecerá com um nome genérico e sem rótulo—nada que um usuário queira clicar. Também lembre‑se de que controles ActiveX são **específicos de plataforma**; eles funcionam apenas em máquinas Windows com as bibliotecas COM apropriadas instaladas.  

> **Atenção:** Quando você abrir o DOCX gerado em uma plataforma não‑Windows (por exemplo, macOS), o Word exibirá uma imagem de espaço reservado em vez de um botão real. Essa é uma limitação normal do ActiveX, não um bug no seu código.

---

## Etapa 4: Salvar e verificar o documento

A chamada `document.save(...)` grava um arquivo DOCX padrão que qualquer versão moderna do Microsoft Word pode abrir. Após executar o programa, abra `ActiveXButton.docx`:

1. Localize o botão “Click Me” onde você o inseriu.  
2. Clique com o botão direito no botão → **Properties** para confirmar o nome e a legenda.  
3. Clique no botão; o Word exibirá uma caixa de mensagem simples se você tiver anexado uma macro (fora do escopo deste guia).

Se o botão estiver ausente, verifique se você usou corretamente o **exemplo Aspose.Words Forms2OleControl** e se a pasta de saída existe.  

> **Caso especial:** Se precisar que o botão dispare uma macro, será necessário adicionar código VBA ao documento após a gravação. O Aspose.Words pode injetar VBA usando a API `Document.getBuiltInDocumentProperties()`, mas isso é um tutorial completo por si só.

---

## Variações Comuns e Armadilhas

### Usando um Controle ActiveX Diferente
Se quiser uma caixa de seleção em vez de um botão, basta mudar o tipo de controle:

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### Incorporando Múltiplos Controles
Chame `builder.insertForms2OleControl()` várias vezes, movendo o cursor com `builder.moveTo()` ou inserindo texto entre as chamadas. Cada chamada adiciona um novo contêiner OLE, permitindo construir formulários complexos dentro de um único DOCX.

### Trabalhando com .NET
A mesma lógica se aplica ao C#—os nomes dos métodos são idênticos (`DocumentBuilder.InsertForms2OleControl()`). Se você estiver no .NET, substitua a sintaxe Java pela equivalente em C#, mas o conceito de **incorporar CommandButton em documento Word** permanece inalterado.

---

## Conclusão

Agora você tem um exemplo completo, de ponta a ponta, que **adiciona Forms2OleControl ao DOCX** usando Aspose.Words para Java. Ao criar um documento em branco, inserir o controle ActiveX, configurar suas propriedades e salvar o arquivo, você dominou os passos essenciais para **inserir controle ActiveX no DOCX** e pode estender esse padrão para outros tipos de controle.

Qual o próximo passo? Experimente combinar esta técnica com o mail‑merge do Aspose.Words para gerar formulários personalizados, ou explore a adição de macros VBA para fazer o botão realmente executar algo. O céu é o limite quando você combina o **exemplo Aspose.Words Forms2OleControl** com a lógica de negócios da sua aplicação.

Feliz codificação, e sinta‑se à vontade para deixar um comentário se encontrar algum obstáculo!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add Bookmarks Word with Aspose.Words for Java – Insert, Update, Delete](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}