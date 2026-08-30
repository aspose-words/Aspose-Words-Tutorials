---
category: general
date: 2026-05-26
description: Abra documento Word corrompido em Java com Aspose.Words. Aprenda como
  definir o modo de recuperação e recuperar arquivos Word corrompidos de forma confiável.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: pt
og_description: Abra documento Word corrompido em Java usando Aspose.Words. Este guia
  mostra como definir o modo de recuperação e recuperar arquivos Word corrompidos
  de forma eficiente.
og_title: Abrir documento Word corrompido – Definir modo de recuperação em Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Abrir Documento Word Corrompido – Definir Modo de Recuperação em Java
url: /pt/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Abrir Documento Word Corrompido – Definir Modo de Recuperação em Java

Já tentou abrir um documento Word corrompido e viu o programa travar com uma exceção? Você não está sozinho—esses arquivos .docx quebrados podem ser uma verdadeira dor de cabeça. A boa notícia é que o Aspose.Words for Java oferece controle granular para que você possa **open corrupted word document** sem que o aplicativo falhe, e ainda decidir se deseja avisos, recuperação silenciosa ou uma rejeição rígida.

Neste tutorial, percorreremos todo o processo: desde a criação do `LoadOptions` correto, até a escolha do valor apropriado de **set recovery mode**, e finalmente confirmar que o documento foi realmente carregado. Ao final, você saberá **how to recover corrupted word file** programaticamente, sem necessidade de copiar‑colar manualmente.

> **O que você precisará**  
> * Java 8 ou mais recente (a API funciona também com Java 11)  
> * Aspose.Words for Java 23.9 (ou a versão mais recente)  
> * Um arquivo .docx corrompido de exemplo—basta renomear qualquer arquivo válido para simular corrupção se você não tiver um à mão  

Vamos mergulhar.

## Abrir Documento Word Corrompido – Visão Geral Passo a Passo

Abaixo está o fluxo de alto nível que implementaremos:

1. **Create `LoadOptions`** – este objeto informa ao Aspose.Words como se comportar quando encontra problemas.  
2. **Set recovery mode** – escolha `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS` ou `REJECT_CORRUPTED`.  
3. **Load the document** usando as opções configuradas.  
4. **Verify** se o carregamento foi bem‑sucedido (por exemplo, imprima a contagem de páginas).  

Cada passo é explicado em detalhe, com trechos de código que você pode copiar‑colar diretamente no seu IDE.

## Definir Modo de Recuperação para Diferentes Cenários

Aspose.Words define três estratégias de recuperação dentro de `LoadOptions.RecoveryMode`:

| Mode | Behaviour | When to use |
|------|-----------|-------------|
| `RECOVER_WITH_WARNINGS` | Tenta carregar o documento, mas exibe quaisquer problemas como avisos no console. | Você quer ver *o que* deu errado sem abortar. |
| `RECOVER_WITHOUT_WARNINGS` | Corrige silenciosamente o que for possível e suprime avisos. | Ambientes de produção onde os logs devem permanecer limpos. |
| `REJECT_CORRUPTED` | Lança uma exceção no momento em que a corrupção é detectada. | Pipelines de validação estritos que precisam falhar rapidamente. |

Escolher o modo correto é a essência de **set recovery mode** adequadamente. Na maioria das sessões de depuração, `RECOVER_WITH_WARNINGS` é a escolha ideal porque informa exatamente quais partes foram reparadas.

## Como Recuperar Arquivo Word Corrompido Usando Aspose.Words

Abaixo está um **programa Java completo e executável** que demonstra todo o processo. Sinta‑se à vontade para colocá‑lo em um arquivo `RecoveryModeDemo.java`, ajustar o caminho e executar.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Por que cada linha importa

* **`LoadOptions loadOptions = new LoadOptions();`** – sem este objeto, o Aspose.Words usa a recuperação padrão, que *rejeita* arquivos corrompidos. Criá‑lo fornece o ponto de extensão para mudar esse comportamento.  
* **`setRecoveryMode(...)`** – esta é a chamada **set recovery mode** que decide se avisos aparecem, permanecem ocultos ou causam uma exceção.  
* **`new Document(path, loadOptions);`** – o construtor aceita o `LoadOptions` que acabamos de configurar, portanto a biblioteca sabe como tratar o arquivo quebrado desde o início.  
* **`doc.getPageCount()`** – uma verificação rápida de sanidade. Se o documento carregar e retornar a contagem de páginas, você conseguiu **how to recover corrupted word file** com sucesso.  
* **`doc.save(...)`** – opcional, mas útil; você pode gravar a versão reparada de volta ao disco para uso posterior.  

## Tratando Casos Limítrofes Comuns

### 1. Arquivo Não Encontrado

Se o caminho estiver errado, `Document` lança uma `FileNotFoundException`. Envolva o carregamento em um bloco try‑catch e registre uma mensagem amigável:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Corrupção Irrecuperável

Mesmo com `RECOVER_WITH_WARNINGS`, algumas estruturas estão além do reparo. Nesse caso, o Aspose.Words ainda carrega o que puder, mas você verá avisos como “Cannot read paragraph properties”. Preste atenção à saída do console; esses avisos frequentemente apontam para seções ausentes que você pode precisar reconstruir manualmente.

### 3. Arquivos Grandes e Desempenho

A recuperação adiciona uma pequena sobrecarga porque a biblioteca analisa o arquivo duas vezes—uma vez para detectar problemas, outra para reconstruir. Para documentos de vários gigabytes, considere fazer streaming do arquivo ou aumentar o heap da JVM (`-Xmx2g`) para evitar `OutOfMemoryError`.

## Dicas Profissionais – Tornando a Recuperação Robusta

* **Log warnings to a file** – redirecione `System.err` para um logger para que você tenha um registro de auditoria do que foi corrigido.  
* **Validate after recovery** – execute `doc.updatePageLayout();` e então verifique novamente a contagem de páginas; às vezes o layout muda após corrigir seções quebradas.  
* **Automate batch recovery** – envolva a demonstração em um loop que processa uma pasta de arquivos corrompidos, usando o mesmo `LoadOptions` a cada vez.  

## Conclusão

Agora você sabe exatamente **how to recover corrupted word file** usando Aspose.Words for Java. Ao criar uma instância de `LoadOptions`, **set recovery mode** para a estratégia que se adapta ao seu cenário, e carregar o documento com essas opções, você pode abrir **open corrupted word document** com segurança sem que sua aplicação falhe. O código de exemplo acima é uma solução completa, pronta‑para‑executar, que imprime a contagem de páginas e ainda salva uma cópia limpa.

Qual é o próximo passo? Experimente trocar o modo de recuperação para `RECOVER_WITHOUT_WARNINGS` e compare a saída do console, ou experimente carregar documentos criptografados (você precisará fornecer uma senha via

## Tutoriais Relacionados

- [Aspose.Words Java&#58; Guia Abrangente para Processamento de Documentos Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Como Converter Word para PDF Usando Aspose.Words para Java](/words/english/java/document-converting/using-document-converting/)
- [Como Comparar Dois Arquivos Word com Aspose.Words para Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}