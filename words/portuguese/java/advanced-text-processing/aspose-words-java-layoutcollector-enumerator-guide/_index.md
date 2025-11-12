---
date: '2025-11-12'
description: Aprenda a usar o LayoutCollector e o LayoutEnumerator do Aspose.Words
  for Java para determinar intervalos de páginas, percorrer entidades de layout e
  reiniciar a numeração de páginas em seções contínuas.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: pt
title: 'Aspose.Words Java: Guia do LayoutCollector e LayoutEnumerator'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: Guia de LayoutCollector & LayoutEnumerator

## Introdução  

Você está tendo dificuldade em **determinar o intervalo de páginas**, analisar a paginação ou reiniciar a numeração de páginas em documentos Java complexos? Com **Aspose.Words for Java**, você pode resolver esses problemas rapidamente usando `LayoutCollector` e `LayoutEnumerator`. Neste guia, mostraremos **como usar o LayoutCollector**, **como percorrer o LayoutEnumerator** e como controlar a numeração de páginas em seções contínuas — tudo com código passo a passo que você pode executar hoje.

Você aprenderá a:

1. Usar `LayoutCollector` para **determinar o intervalo de páginas** de qualquer nó.  
2. **Percorrer entidades de layout** com `LayoutEnumerator`.  
3. Implementar callbacks de layout para renderização dinâmica.  
4. **Reiniciar a numeração de páginas** em seções contínuas.  

Vamos começar garantindo que seu ambiente esteja pronto.

## Pré‑requisitos  

### Bibliotecas Necessárias  

> **Nota:** O código funciona com a versão mais recente do Aspose.Words for Java (não é necessário especificar número de versão).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### Ambiente  

- JDK 17 ou superior.  
- IntelliJ IDEA, Eclipse ou qualquer IDE Java de sua preferência.  

### Conhecimentos  

Familiaridade básica com a sintaxe Java e conceitos de programação orientada a objetos ajudará a acompanhar os exemplos.

## Configurando Aspose.Words  

Primeiro, adicione a biblioteca Aspose.Words ao seu projeto e aplique uma licença (ou use a versão de avaliação). O trecho a seguir mostra como carregar a licença e confirmar que a biblioteca está pronta:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Dica:** Mantenha o arquivo de licença fora do controle de versão para proteger suas credenciais.

Agora podemos mergulhar nas duas funcionalidades principais.

## 1. Como Usar LayoutCollector para Análise de Intervalo de Páginas  

`LayoutCollector` permite que você **determine o intervalo de páginas** para qualquer nó em um documento, o que é essencial para a análise de paginação.

### Implementação Passo a Passo  

1. **Criar um novo Document e uma instância de LayoutCollector.**  
2. **Adicionar conteúdo que ocupe várias páginas.**  
3. **Atualizar o layout e consultar as métricas de intervalo de páginas.**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Explicação**

- `DocumentBuilder` insere texto e quebras, criando um documento que naturalmente se estende por várias páginas.  
- `updatePageLayout()` força o Aspose.Words a calcular o layout, garantindo números de página precisos.  
- `getNumPagesSpanned()` devolve o total de páginas cobertas pelo nó fornecido (neste caso, o documento inteiro).

## 2. Como Percorrer LayoutEnumerator  

`LayoutEnumerator` fornece uma **visão estruturada das entidades de layout** (páginas, parágrafos, runs etc.) e permite mover-se para frente ou para trás através delas.

### Implementação Passo a Passo  

1. Carregue um documento existente que contenha entidades de layout.  
2. Crie uma instância de `LayoutEnumerator`.  
3. Mova‑se para o nível de página e, em seguida, percorra para frente e para trás usando métodos auxiliares.

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Nota:** Os métodos `traverseLayoutForward` e `traverseLayoutBackward` são auxiliares recursivos que percorrem a árvore de layout. Você pode customizá‑los para coletar informações como caixas delimitadoras, detalhes de fontes ou metadados personalizados.

## 3. Como Implementar Callbacks de Layout de Página  

Às vezes é necessário reagir a eventos de layout — por exemplo, quando uma seção termina de ser reformatada ou quando a conversão para outro formato é concluída. Implemente a interface `IPageLayoutCallback` para receber essas notificações.

### Implementação Passo a Passo  

1. Defina uma instância de callback nas opções de layout do documento.  
2. Implemente a lógica do callback para tratar os eventos `PART_REFLOW_FINISHED` e `CONVERSION_FINISHED`.  

```java
// 1. Register the callback
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();   // Triggers the callback during layout processing

// 2. Callback implementation
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs args) throws Exception {
        if (args.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            renderPage(args, args.getPageIndex());
        } else if (args.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            System.out.println("Document conversion finished.");
        }
    }

    private void renderPage(PageLayoutCallbackArgs args, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            args.getDocument().save(stream, saveOptions);
        }
    }
}
```

**Explicação**

- `notify()` recebe todos os eventos de layout. Filtramos apenas os eventos de interesse.  
- Quando uma parte termina de ser reformatada, `renderPage()` salva essa página como uma imagem PNG.  

## 4. Como Reiniciar a Numeração de Páginas em Seções Contínuas  

Quando um documento contém seções contínuas, pode ser desejável que a numeração de páginas reinicie apenas em uma nova página. O Aspose.Words permite controlar isso com `ContinuousSectionRestart`.

### Implementação Passo a Passo  

1. Carregue o documento alvo.  
2. Defina a opção `ContinuousSectionPageNumberingRestart`.  
3. Atualize o layout para aplicar a alteração.

```java
// 1. Load the multi‑section document
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");

// 2. Configure page‑numbering restart behavior
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);

// 3. Update layout to reflect the new numbering scheme
doc.updatePageLayout();
System.out.println("Page numbering restart configured for continuous sections.");
```

**Explicação**

- `FROM_NEW_PAGE_ONLY` indica ao Aspose.Words que a numeração deve reiniciar somente quando uma nova página física aparecer, preservando um fluxo contínuo nas seções.

## Aplicações Práticas  

| Cenário | Qual Recurso Ajuda? | Benefício |
|----------|----------------------|-----------|
| **Auditar paginação de documentos** | `LayoutCollector` | Encontrar rapidamente seções que ultrapassam páginas. |
| **Renderizar PDFs com fidelidade visual exata** | `LayoutEnumerator` + callbacks | Acessar detalhes de layout para renderização precisa. |
| **Automatizar inserção de marca‑d’água após cada layout de página** | Callbacks de layout de página | Reagir instantaneamente quando uma página é finalizada. |
| **Gerar relatórios multi‑seção com numeração personalizada** | Reinício de seção contínua | Manter numeração profissional sem edições manuais. |

## Dicas de Performance  

- **Remova nós não utilizados** antes de chamar `updatePageLayout()` para manter o consumo de memória baixo.  
- **Reutilize uma única instância de LayoutCollector** para múltiplas consultas ao invés de recriá‑la.  
- **Limite a profundidade de recursão** nos auxiliares de percurso para evitar estouro de pilha em documentos muito grandes.  

## Conclusão  

Ao dominar **como usar o LayoutCollector**, **como percorrer o LayoutEnumerator** e **como reiniciar a numeração de páginas**, você agora dispõe de uma caixa de ferramentas poderosa para processamento avançado de texto com Aspose.Words for Java. Essas técnicas permitem que você **determine o intervalo de páginas**, **analise a paginação do documento** e **controle o comportamento de layout** com confiança. Aplique-as em relatórios, e‑books ou qualquer fluxo de trabalho automatizado de documentos e você perceberá um aumento notável tanto na precisão quanto na produtividade.

{{< /blocks