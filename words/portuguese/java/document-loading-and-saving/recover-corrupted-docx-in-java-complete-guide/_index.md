---
category: general
date: 2026-06-20
description: Recupere arquivos docx corrompidos em Java com Aspose.Words. Aprenda
  como definir o modo de recuperação e carregar o documento com recuperação para uma
  abertura sem problemas.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- load document with recovery
- open word with recovery
- open corrupted docx
language: pt
og_description: Recupere arquivos docx corrompidos em Java usando Aspose.Words. Este
  tutorial mostra como definir o modo de recuperação, carregar o documento com recuperação
  e abrir o docx corrompido com segurança.
og_title: Recuperar docx corrompido em Java – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  headline: Recover corrupted docx in Java – Complete Guide
  type: TechArticle
- description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  name: Recover corrupted docx in Java – Complete Guide
  steps:
  - name: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
    text: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
  - name: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
    text: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
  - name: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
    text: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
  - name: Open Word → *File* → *Open*.
    text: Open Word → *File* → *Open*.
  - name: Select the corrupted `.docx`.
    text: Select the corrupted `.docx`.
  - name: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
    text: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Recovery
- DOCX
title: Recuperar docx corrompido em Java – Guia Completo
url: /pt/java/document-loading-and-saving/recover-corrupted-docx-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recuperar docx corrompido em Java – Guia Completo

Já tentou **recuperar docx corrompido** e encontrou um obstáculo? Neste tutorial vamos mostrar como **recuperar docx corrompido** usando Aspose.Words for Java através de **definir modo de recuperação** e **carregar documento com recuperação**, de modo que o arquivo abra como um documento Word saudável.  

Se você já se perguntou por que alguns arquivos DOCX se recusam a abrir no Word, a resposta costuma ser dano oculto que o carregador padrão não consegue tratar. Vamos percorrer os passos exatos que você precisa, desde adicionar a biblioteca até verificar a contagem de páginas, e você terminará com um documento limpo e utilizável — sem mais pop‑ups de “arquivo está corrompido”.

## O que você aprenderá

- Como **definir modo de recuperação** para instruir o Aspose.Words sobre quão agressivamente ele deve reparar um arquivo quebrado.  
- O código exato necessário para **carregar documento com recuperação** e lidar graciosamente com danos severos.  
- Dicas para cenários de **abrir word com recuperação** e o que fazer quando o arquivo não pode ser salvo.  
- Um exemplo completo e executável que você pode copiar‑colar no seu IDE.  

### Pré‑requisitos

- Java 8 ou superior instalado.  
- Maven ou Gradle para gerenciar dependências (cobriremos Maven).  
- Um arquivo `.docx` corrompido que você queira testar (qualquer arquivo que se recuse a abrir no Microsoft Word serve).  

Nenhum conhecimento profundo da API Aspose é necessário — apenas habilidades básicas em Java. Vamos começar.

![exemplo de recuperação de docx corrompido](recover_corrupted_docx.png "captura de tela de recuperação de docx corrompido")

## Etapa 1: Adicionar Aspose.Words for Java ao seu projeto

Primeiro de tudo — seu projeto precisa do JAR do Aspose.Words. Se você usa Maven, adicione isto ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Usuários Gradle podem acrescentar:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

**Dica profissional:** Sempre verifique o site da Aspose para a versão mais recente; lançamentos mais novos costumam incluir algoritmos de recuperação aprimorados.

## Etapa 2: Definir modo de recuperação – A chave para consertar arquivos danificados

Agora que a biblioteca está no lugar, você precisa dizer a ela **como** se comportar ao encontrar corrupção. É aqui que `setRecoveryMode` entra em ação. O enum `RecoveryMode` oferece duas opções:

| Modo | Descrição |
|------|-----------|
| `RECOVER` | Tenta corrigir o máximo possível, retornando um documento parcialmente reparado. |
| `REJECT` | Lança uma exceção ao encontrar qualquer problema sério, útil quando você precisa de um estado limpo. |

Aqui está o código que **define modo de recuperação** para a opção permissiva `RECOVER`:

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create LoadOptions and set the desired recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Use RECOVER to attempt fixing,
                                                          // REJECT to fail on severe damage

        // Step 2.2: Load the possibly corrupted document using the configured options
        Document doc = new Document("C:/files/corrupted.docx", loadOptions);

        // Step 2.3: Work with the loaded document (e.g., display page count)
        System.out.println("Loaded with " + doc.getPageCount() + " pages");
    }
}
```

**Por que isso importa:** Sem definir o modo de recuperação, o Aspose.Words usa `REJECT` por padrão, o que significa que seu programa lançará uma exceção assim que detectar uma parte quebrada. Ao **definir modo de recuperação** explicitamente, você permite que a biblioteca corrija nós XML ausentes, restaure relacionamentos faltantes e, de modo geral, “limpe” o arquivo.

## Etapa 3: Carregar documento com recuperação – Juntando tudo

O trecho acima já demonstra **carregar documento com recuperação**, mas vamos detalhá‑lo para clareza:

1. **Instanciar `LoadOptions`** – este objeto contém todas as flags que você deseja que o carregador respeite.  
2. **Chamar `setRecoveryMode`** – escolhemos `RECOVER` porque queremos a melhor chance de abrir o arquivo.  
3. **Passar as opções ao construtor `Document`** – o Aspose.Words lê o arquivo, aplica a lógica de recuperação e devolve um objeto `Document` utilizável.

Se preferir uma abordagem mais defensiva, pode envolver o carregamento em um bloco try‑catch e recuar para `REJECT` caso `RECOVER` produza um resultado insatisfatório:

```java
try {
    Document doc = new Document("C:/files/corrupted.docx", loadOptions);
    System.out.println("Recovered document has " + doc.getPageCount() + " pages.");
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
    // Optional: retry with REJECT mode to see if the file is beyond repair
}
```

## Etapa 4: Verificar o documento reparado

Depois que o documento for carregado, você vai querer garantir que o conteúdo esteja razoável. Verificações comuns incluem:

- **Contagem de páginas** – uma checagem rápida de sanidade (`doc.getPageCount()`).  
- **Extração de texto** – `doc.getText()` para ver se o corpo principal está intacto.  
- **Salvar uma cópia** – gravar a versão recuperada no disco para inspeção posterior.

```java
// Save the recovered file for manual verification
doc.save("C:/files/recovered.docx");

// Print first 200 characters of text to the console
String preview = doc.getText().substring(0, Math.min(200, doc.getText().length()));
System.out.println("Preview of recovered text:\n" + preview);
```

Se a pré‑visualização parecer distorcida, o arquivo pode ter sofrido danos irreversíveis. Nesse caso, considere usar o modo `REJECT` para evitar propagar dados corrompidos.

## Etapa 5: Opcional – Abrir Word com recuperação (abordagem manual)

Às vezes você não quer escrever código; só precisa **abrir word com recuperação** manualmente. O próprio Microsoft Word oferece o recurso “Abrir e Reparar”:

1. Abra o Word → *Arquivo* → *Abrir*.  
2. Selecione o `.docx` corrompido.  
3. Clique na seta ao lado de *Abrir* e escolha **Abrir e Reparar**.

Embora isso funcione para muitos usuários, carece da automação e capacidade de processamento em lote da abordagem Java que acabamos de cobrir. Use o método manual para correções ocasionais; confie no Aspose.Words quando precisar processar dezenas ou centenas de arquivos programaticamente.

## Casos limites e armadilhas comuns

- **Corrupção severa** – Se o arquivo estiver sem seu `[Content_Types].xml` central, nem mesmo `RECOVER` ajuda. Espere uma exceção e notifique o usuário.  
- **Arquivos protegidos por senha** – O modo de recuperação não ignora criptografia. Você deve fornecer a senha via `LoadOptions.setPassword("yourPwd")` antes de tentar a recuperação.  
- **Documentos grandes** – Carregar um DOCX massivo com `RECOVER` pode consumir mais memória. Considere aumentar o heap da JVM (`-Xmx2g`) se encontrar `OutOfMemoryError`.  

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode compilar e executar diretamente. Substitua o caminho do arquivo pela localização do seu DOCX corrompido.

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        try {
            // Create LoadOptions and set recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Attempt to fix

            // Load the corrupted document
            Document doc = new Document("C:/files/corrupted.docx", loadOptions);

            // Verify and display basic info
            System.out.println("Recovered document loaded successfully.");
            System.out.println("Page count: " + doc.getPageCount());

            // Save a clean copy
            doc.save("C:/files/recovered.docx");
            System.out.println("Recovered file saved as recovered.docx");

            // Show a short text preview
            String text = doc.getText();
            System.out.println("Text preview (first 200 chars):");
            System.out.println(text.substring(0, Math.min(200, text.length())));
        } catch (Exception ex) {
            System.err.println("Failed to recover the document: " + ex.getMessage());
        }
    }
}
```

**Saída esperada (quando a recuperação for bem‑sucedida):**

```
Recovered document loaded successfully.
Page count: 12
Recovered file saved as recovered.docx
Text preview (first 200 chars):
Lorem ipsum dolor sit amet, consectetur adipiscing elit...
```

Se o documento estiver além do reparo, você verá uma mensagem de erro clara em vez de um stack trace, graças ao `try‑catch` ao redor.

## Conclusão

Agora você sabe como **recuperar docx corrompido** em Java usando Aspose.Words. Ao **definir modo de recuperação** para `RECOVER` e então **carregar documento com recuperação**, você pode reparar automaticamente muitos problemas comuns que impediriam a abertura de um arquivo Word. Seja para **abrir word com recuperação** programaticamente ou apenas para **abrir docx corrompido** manualmente, as técnicas apresentadas aqui fornecem uma base sólida.

**Próximos passos:**  

- Experimente

## O que você deve aprender a seguir?

Os tutoriais abaixo abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Recuperar docx corrompido – Guia completo para corrigir e processar documentos](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [Como carregar HTML e salvar como DOCX usando Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Como mesclar vários arquivos DOCX usando Aspose.Words for Java](/words/english/java/document-merging/using-document-merging/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}