---
category: general
date: 2026-07-20
description: Como adicionar um botão a um documento Word usando Aspose.Words. Aprenda
  a inserir um botão Forms2OleControl com DocumentBuilder em minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: pt
lastmod: 2026-07-20
og_description: Como adicionar um botão a um documento Word com Aspose.Words. Siga
  este guia prático para incorporar um Forms2OleControl CommandButton usando Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Como adicionar um botão a um documento Word – Tutorial completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Como adicionar um botão ao documento do Word – Guia passo a passo
url: /pt/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Adicionar um Botão a um Documento Word – Tutorial Completo do Aspose.Words

Já se perguntou **como adicionar um botão a um documento Word** sem abrir a interface e clicar por aí? Você não está sozinho. Muitos desenvolvedores precisam incorporar controles interativos programaticamente — pense em um botão “Enviar” em um modelo que será preenchido mais tarde por um usuário final. A boa notícia? Com o Aspose.Words para Java você pode fazer isso em poucas linhas.

Neste tutorial vamos percorrer passo a passo as etapas exatas para inserir um `Forms2OleControl` do tipo **CommandButton** usando o `DocumentBuilder`. Ao final, você terá um arquivo `.docx` pronto‑para‑uso que mostra um botão clicável rotulado “Click Me”. Sem mistério, apenas código claro e o raciocínio por trás de cada linha.

## O Que Você Vai Aprender

- Como criar um novo documento Word do zero.  
- Como usar **DocumentBuilder** para colocar um **Forms2OleControl**.  
- Por que você deve definir a legenda do botão e dimensioná‑lo da maneira que fazemos.  
- Como salvar e verificar o resultado.  
- Armadilhas comuns (por exemplo, bibliotecas ausentes, tipos de controle não suportados) e como evitá‑las.

**Pré‑requisitos** – Você precisa de Java 8+ (ou mais recente) e da biblioteca Aspose.Words para Java (versão 23.12 ou posterior). Uma IDE como IntelliJ IDEA ou Eclipse tornará as coisas mais suaves, mas qualquer editor de texto funciona.

---

## Etapa 1: Configurar Seu Projeto e Importar Dependências

Antes que qualquer código seja executado, o Maven (ou Gradle) precisa saber onde buscar o Aspose.Words. Adicione este trecho ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Se preferir Gradle, o equivalente é:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Dica de especialista:** Use a versão mais recente; versões antigas podem não conter a API `Forms2OleControl`.

Depois que a dependência for resolvida, você está pronto para escrever código Java.

---

## Etapa 2: Criar um Novo Documento e Obter um DocumentBuilder

A classe `Document` representa todo o pacote `.docx`, enquanto `DocumentBuilder` é o pincel que você usa para pintar conteúdo nele. Pense no `DocumentBuilder` como o “cursor” que sabe onde o próximo elemento deve ser inserido.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:** Inicializar um `Document` novo lhe dá uma tela limpa. O builder aponta automaticamente para o primeiro parágrafo, então você não precisa gerenciar seções ou páginas manualmente.

---

## Etapa 3: Inserir um Forms2OleControl do Tipo CommandButton

Agora vem a estrela do show: `insertForms2OleControl`. Este método cria um controle OLE (Object Linking and Embedding) que o Word trata como um elemento de formulário. Passaremos três argumentos:

1. `Forms2OleControlType.COMMANDBUTTON` – indica ao Word que queremos um botão.  
2. `100` – largura em pontos (≈1,39 polegadas).  
3. `30` – altura em pontos (≈0,42 polegadas).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Como funciona:** Nos bastidores, o Aspose.Words cria o XML apropriado na parte `word/document.xml`, referenciando o objeto OLE. As dimensões fornecidas são respeitadas pelo motor de layout do Word, de modo que o botão aparece exatamente onde o cursor do builder está posicionado.

---

## Etapa 4: Definir a Legenda (Texto) no Botão

Um botão sem rótulo é confuso — imagine um botão de elevador silencioso. O método `setCaption` define o texto visível:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Você pode mudar a legenda para qualquer coisa: “Submit”, “Approve” ou até mesmo uma string localizada. A legenda é armazenada nas propriedades do objeto OLE, então o Word a renderiza nativamente.

---

## Etapa 5: Salvar o Documento e Verificar o Resultado

Por fim, grave o arquivo no disco. Escolha uma pasta onde você tenha permissão de escrita; caso contrário, você encontrará um `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Abra `button-demo.docx` no Microsoft Word. Você deverá ver um botão rotulado **Click Me** posicionado no topo do documento. Clicar nele no Word acionará o comportamento padrão do OLE (geralmente uma mensagem de espaço reservado, a menos que você vincule uma macro).

---

## Casos de Borda Comuns e Como Lidiar com Eles

| Situação | Por Que Acontece | Solução |
|-----------|----------------|-----|
| **Tipo `Forms2OleControl` ausente** | Versões antigas do Aspose.Words não expunham esse enum. | Atualize para 23.12+ ou posterior. |
| **Botão aparece como imagem** | Configurações de segurança do Word bloqueiam controles OLE. | Habilite “Confiar no acesso ao modelo de objeto do projeto VBA” no Centro de Confiabilidade, ou use um `.docm` habilitado para macro. |
| **Tamanho incorreto** | Confusão entre pontos e pixels. | Lembre‑se que 1 ponto = 1/72 polegada. Ajuste os números conforme necessário. |
| **Salvar lança `FileNotFoundException`** | O caminho não existe. | Garanta que o diretório (`output/`) seja criado antes de `doc.save`. Use `new File("output").mkdirs();`. |

---

## Expandindo o Exemplo: Adicionando Vários Botões ou Outros Controles

Se precisar de mais de um botão, basta mover o cursor do builder com `builder.moveTo` ou `builder.writeln()` antes de chamar `insertForms2OleControl` novamente.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Você também pode inserir um **CheckBox**, **ComboBox** ou **ListBox** trocando `Forms2OleControlType.COMMANDBUTTON` pelo valor enum apropriado (`CHECKBOX`, `COMBOBOX`, etc.). Os mesmos parâmetros de largura/altura se aplicam.

---

## Como Isso Se Encaixa em Fluxos de Trabalho Maiores de Automação Word

- **Geração de Modelos:** Crie um modelo de contrato que inclua um botão “Aprovar” para aprovação posterior.  
- **Relatórios:** Gere um relatório diário com um botão “Atualizar Dados” que dispara uma macro.  
- **Distribuição de Formulários:** Envie um questionário com controles interativos pré‑populados.

Todos esses cenários se beneficiam da **automação Word** que demonstramos. Ao incorporar controles programaticamente, você elimina a edição manual e reduz erros humanos.

---

## Código Fonte Completo (Pronto para Copiar e Colar)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Saída esperada:** Quando você abrir `output/button-demo.docx` no Microsoft Word, verá dois botões — “Click Me” e “Submit” — empilhados verticalmente no topo do arquivo.

---

## Conclusão

Respondemos **como adicionar um botão a um documento Word** usando o Aspose.Words para Java, passo a passo. Partindo de um `Document` vazio, utilizamos **DocumentBuilder** para inserir um `Forms2OleControl` do tipo **CommandButton**, definimos uma legenda amigável e salvamos o resultado. A abordagem escala para múltiplos controles e se integra perfeitamente a pipelines maiores de **automação Word**.

Pronto para o próximo desafio? Experimente trocar o botão por um **CheckBox**, ou vincular uma macro para reagir quando o usuário clicar no botão em um arquivo `.docm`. O mesmo padrão se aplica — basta mudar o enum e ajustar a legenda.

Se encontrar algum obstáculo, verifique novamente a versão da biblioteca e as permissões da pasta de saída. Sinta‑se à vontade para deixar um comentário abaixo com dúvidas ou compartilhar seu próprio caso de uso. Feliz codificação!

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}