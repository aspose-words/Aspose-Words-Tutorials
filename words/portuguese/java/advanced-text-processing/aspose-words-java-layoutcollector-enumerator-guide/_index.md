---
date: '2025-11-12'
description: Aprenda a usar o LayoutCollector e o LayoutEnumerator do Aspose.Words
  for Java para analisar a paginação, percorrer o layout do documento, implementar
  callbacks de layout e reiniciar a numeração de páginas em seções contínuas.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: pt
title: Análise de Paginação em Java com Ferramentas de Layout do Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Análise de Paginação em Java com as Ferramentas de Layout do Aspose.Words

## Introdução  

Se você precisa **analisar a paginação** ou **percorrer o layout de um documento** em uma aplicação Java, o Aspose.Words for Java oferece duas APIs poderosas: **`LayoutCollector`** e **`LayoutEnumerator`**. Essas classes permitem descobrir quantas páginas um nó ocupa, percorrer cada entidade de layout, reagir a eventos de layout e até reiniciar a numeração de páginas em seções contínuas. Neste guia, percorreremos cada recurso passo a passo, mostraremos trechos de código reais e explicaremos os resultados esperados para que você possa aplicá‑los imediatamente.

Você aprenderá a:

* **usar LayoutCollector** para obter a página inicial e final de qualquer nó (use layoutcollector page span)  
* **percorrer o layout do documento** com LayoutEnumerator (traverse document layout)  
* **implementar callbacks de layout** para reagir a eventos de paginação (implement layout callback)  
* **reiniciar a numeração de páginas** em seções contínuas (restart page numbering sections)  

Vamos começar.

## Pré‑requisitos  

### Bibliotecas Necessárias  

| Ferramenta de Build | Dependência |
|---------------------|-------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Observação:** O número da versão é mantido por compatibilidade; o código funciona com qualquer versão recente do Aspose.Words for Java.

### Ambiente  

* JDK 8 ou superior  
* Uma IDE como IntelliJ IDEA ou Eclipse  

### Conhecimento  

Programação básica em Java e familiaridade com Maven/Gradle são suficientes para seguir os exemplos.

## Configurando o Aspose.Words  

Antes de chamar qualquer API de layout, a biblioteca deve estar licenciada (ou em modo de avaliação). O trecho abaixo mostra a inicialização mínima:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*O código não modifica nenhum documento; ele simplesmente prepara o ambiente do Aspose.*  

Agora podemos mergulhar nos recursos principais.

## Recurso 1: Usando **LayoutCollector** para Analisar a Paginação  

`LayoutCollector` mapeia cada nó em um `Document` para as páginas que ele ocupa. Esta é a forma mais confiável de **use layoutcollector page span** para análise de paginação.

### Implementação passo a passo  

1. **Crie um novo documento e anexe um LayoutCollector.**  
2. **Insira conteúdo que force a paginação** (por exemplo, quebras de página, quebras de seção).  
3. **Atualize o layout** com `updatePageLayout()`.  
4. **Consulte o coletor** para a página inicial, página final e total de páginas abrangidas.

#### 1️⃣ Inicializar Document e LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Popular o Document  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Atualizar Layout e Recuperar Métricas  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Saída esperada**

```
Document spans 5 pages.
```

> **Por que funciona:** `updatePageLayout()` força o Aspose.Words a recomputar o layout, após o que o