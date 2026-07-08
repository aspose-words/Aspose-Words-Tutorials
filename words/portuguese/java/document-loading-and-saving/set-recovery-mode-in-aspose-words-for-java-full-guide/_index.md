---
category: general
date: 2026-07-03
description: Defina o modo de recuperação para recuperar arquivos Word corrompidos
  em Java e exiba a contagem de páginas após o carregamento. Aprenda passo a passo
  com Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: pt
og_description: Defina o modo de recuperação no Aspose.Words for Java para recuperar
  arquivos Word corrompidos e exibir a contagem de páginas. Siga o exemplo completo
  agora.
og_title: Defina o Modo de Recuperação no Aspose.Words para Java – Tutorial Completo
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Definir o Modo de Recuperação no Aspose.Words para Java – Guia Completo
url: /pt/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Defina o Modo de Recuperação no Aspose.Words para Java – Guia Completo

Já se perguntou como **definir o modo de recuperação** ao carregar um arquivo `.docx` corrompido com Aspose.Words? Você não é o único coçando a cabeça por causa de documentos Word danificados que se recusam a abrir. Neste tutorial vamos percorrer exatamente isso — como configurar a biblioteca para **recuperar arquivos Word corrompidos** e então **exibir a contagem de páginas** do conteúdo carregado com sucesso.

Cobriremos tudo, desde o pequeno ajuste em `LoadOptions` até o `System.out.println` final que informa quantas páginas sobreviveram à missão de resgate. Sem enrolação, apenas uma solução prática, pronta para copiar‑colar que funciona com a versão mais recente do Aspose.Words 23.12.

## O que Você Vai Aprender

- Por que o modo de recuperação importa e quais opções o Aspose.Words oferece.  
- Como **definir o modo de recuperação** programaticamente usando Java.  
- Maneiras de **exibir a contagem de páginas** após o documento ser carregado, confirmando que a recuperação foi bem‑sucedida.  
- Armadilhas comuns ao lidar com arquivos Word corrompidos e como evitá‑las.  

Antes de mergulharmos, certifique‑se de que você tem:

1. Uma licença válida do Aspose.Words para Java (ou uma chave de avaliação temporária).  
2. Java 17 ou superior instalado na sua máquina.  
3. O arquivo `Corrupted.docx` corrompido que você deseja testar.  

Tem tudo isso? Ótimo — vamos colocar a mão na massa.

> **Dica profissional:** Mesmo que você esteja usando uma versão de avaliação, os recursos de recuperação funcionam exatamente como em uma compilação licenciada.

---

## ## Como Definir o Modo de Recuperação com Aspose.Words para Java

O coração da solução está na classe `LoadOptions`. Por padrão, o Aspose.Words tenta ao máximo carregar um documento, mas quando o arquivo está seriamente danificado você precisa dizer a ele *como* se comportar. É aí que **definir o modo de recuperação** entra em ação.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Por que `RecoveryMode.PARSE`?

- **PARSE** – O Aspose.Words analisa todos os fragmentos que consegue entender, costurando um documento parcialmente funcional. Ideal quando você precisa de *qualquer* conteúdo de um arquivo quebrado.  
- **SKIP** – A biblioteca pula completamente as seções corrompidas, o que pode ser mais rápido, mas pode descartar mais dados.  

Na maioria dos cenários reais, **PARSE** é a escolha mais segura porque maximiza a quantidade de texto, imagens e formatação recuperáveis.

---

## ## Exibir a Contagem de Páginas Após a Recuperação

Uma vez que o documento está carregado, o próximo passo lógico é verificar o sucesso da operação. A métrica mais simples, porém informativa, é a contagem de páginas. O método `Document.getPageCount()` faz exatamente isso.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Se o arquivo estiver completamente ilegível, o Aspose.Words lançará uma exceção *antes* de você chegar a esta linha. Quando você vê uma contagem de páginas `0` ou um número muito baixo, isso geralmente indica que o modo de recuperação teve que descartar grandes trechos do arquivo original.

**Saída esperada (exemplo):**

```
Document loaded, page count = 12
```

Isso indica que a biblioteca conseguiu reconstruir doze páginas a partir da fonte corrompida — bastante sólido para um `.docx` quebrado.

---

## ## Casos Limítrofes & Armadilhas Comuns

### 1️⃣ Seções de Cabeçalho/Rodapé Corrompidas
Às vezes apenas o corpo principal é analisado enquanto cabeçalhos e rodapés são perdidos. Se você depende deles para branding, pode ser necessário reinjetá‑los após a recuperação.

### 2️⃣ Imagens Que Não Carregam
Imagens incorporadas costumam ser removidas quando o contêiner zip (o formato subjacente do `.docx`) está danificado. Você pode detectar isso iterando sobre `doc.getSections()` e verificando `Section.getBody().getParagraphs()` em busca de objetos `Shape`.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Se o laço não imprimir nada, o modo de recuperação provavelmente pulou as imagens.

### 3️⃣ Documentos Grandes e Memória
Recuperar um arquivo corrompido de 200 páginas pode consumir muita memória. Considere aumentar o tamanho do heap da JVM (`-Xmx2g`) quando antecipar documentos volumosos.

### 4️⃣ Restrições de Licença
A versão de avaliação limita certos recursos, mas **recuperação** funciona plenamente. Contudo, a contagem de páginas impressa pode ser limitada a algumas páginas na avaliação. Sempre teste com uma compilação licenciada para produção.

---

## ## Exemplo Completo de Ponta a Ponta (Executável)

Abaixo está um programa autônomo que você pode inserir em qualquer projeto Maven ou Gradle. Ele inclui a declaração de dependência necessária para o Aspose.Words 23.12.

### Trecho do `pom.xml` Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Arquivo fonte Java `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**O que isso faz:**

1. **Define o modo de recuperação** – o núcleo do nosso tutorial.  
2. Carrega o arquivo corrompido usando as `LoadOptions` configuradas.  
3. **Exibe a contagem de páginas**, fornecendo feedback imediato.  
4. Salva uma versão limpa (`Recovered.docx`) para que você possa abri‑la no Word posteriormente.

Execute o programa com:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Você deverá ver a contagem de páginas impressa no console, confirmando que a recuperação foi bem‑sucedida.

---

## ## Visão Geral Visual (Imagem)

![set recovery mode flow diagram](https://example.com/images/recovery-mode-flow.png "Diagram illustrating how set recovery mode works in Aspose.Words for Java")

*O texto alternativo inclui a palavra‑chave principal **set recovery mode** para atender ao SEO.*

---

## ## Perguntas Frequentes

**Q: E se `RecoveryMode.PARSE` ainda lançar uma exceção?**  
A: Isso geralmente significa que o arquivo está além de qualquer reparo — talvez o contêiner zip esteja completamente danificado. Nesses casos, pode ser necessário usar uma ferramenta de reparo de terceiros antes de entregá‑lo ao Aspose.Words.

**Q: Posso combinar `RecoveryMode.PARSE` com callbacks personalizados de carregamento de documento?**  
A: Absolutamente. Implemente `IWarningCallback` para capturar quaisquer avisos que o Aspose.Words emita durante o processo de análise. Isso fornece insight sobre quais partes foram puladas.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**Q: Alterar o modo de recuperação afeta o arquivo original?**  
A: Não. O Aspose.Words trabalha em uma cópia na memória; o arquivo fonte permanece intacto a menos que você chame explicitamente `doc.save()`.

---

## ## Conclusão

Cobremos como **definir o modo de recuperação** no Aspose.Words para Java, por que `PARSE` costuma ser a melhor escolha para salvar um documento quebrado e como **exibir a contagem de páginas** para validar o resultado. Seguindo o exemplo completo, você agora tem uma solução pronta‑para‑executar que pode **recuperar arquivos Word corrompidos** e fornecer feedback imediato sobre o sucesso da operação.

Próximos passos? Experimente trocar para `RecoveryMode.SKIP` e observe a diferença, teste com arquivos grandes e com múltiplas seções, ou integre a lógica em um serviço web que repare automaticamente documentos enviados pelos usuários. O mesmo padrão funciona para PDFs (usando Aspose.PDF) e até para recuperação de texto puro com outras bibliotecas — basta lembrar da ideia central: configure o carregador, tente a recuperação e valide com uma métrica simples como a contagem de páginas.

Feliz codificação, e que seus documentos permaneçam intactos!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Combine Multiple Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}