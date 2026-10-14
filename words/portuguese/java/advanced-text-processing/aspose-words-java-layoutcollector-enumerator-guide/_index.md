---
date: '2026-01-14'
description: Aprenda como reiniciar a numeração de páginas com Aspose.Words Java e
  usar o LayoutCollector para extrair dados de paginação, atualizar o layout da página
  e renderizar páginas como imagens.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Reiniciar a numeração de páginas com Aspose.Words Java – LayoutCollector e
  LayoutEnumerator
url: /pt/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reiniciar a Numeração de Páginas com Aspose.Words Java – LayoutCollector & LayoutEnumerator

## Introdução

Você está tendo dificuldades para **reiniciar a numeração de páginas** em documentos Java extensos e ainda precisa analisar a paginação ou renderizar páginas como imagens? Com **Aspose.Words for Java**, você pode usar `LayoutCollector` e `LayoutEnumerator` não apenas para reiniciar a numeração de páginas, mas também para **extrair dados de paginação**, **atualizar o layout da página** e **renderizar páginas como imagens** para visualizações ou PDFs. Este guia orienta você passo a passo, desde a configuração da biblioteca até a implementação de callbacks que dão controle total sobre a renderização do documento.

**O que você aprenderá**
- Como usar `LayoutCollector` para extrair dados de paginação e determinar intervalos de páginas.
- Percorrer o layout do documento com `LayoutEnumerator`.
- Implementar callbacks de layout de página para **renderizar páginas como imagens**.
- **Reiniciar a numeração de páginas** em seções contínuas usando opções de layout.
- Dicas para **atualizar o layout da página** de forma eficiente.

## Respostas Rápidas
- **Como reinicio a numeração de páginas em um documento Java?** Use `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` e chame `doc.updatePageLayout()`.
- **Qual classe extrai dados de paginação?** `LayoutCollector` fornece índices de página inicial/final para qualquer nó.
- **Posso renderizar cada página como imagem?** Sim—implemente `IPageLayoutCallback` e use `ImageSaveOptions`.
- **Preciso chamar update page layout manualmente?** Após alterar as opções de layout, sempre chame `doc.updatePageLayout()`.
- **Qual versão do Aspose.Words é necessária?** Os exemplos funcionam com Aspose.Words for Java 25.3 (ou posterior).

## O que é reiniciar a numeração de páginas?

Reiniciar a numeração de páginas permite iniciar uma nova sequência de numeração em uma seção específica do documento, o que é essencial para relatórios, livros ou contratos que exigem numeração separada para capítulos ou apêndices. O Aspose.Words oferece uma opção de layout que permite controlar esse comportamento sem truques manuais de quebra de página.

## Por que usar LayoutCollector e LayoutEnumerator?

- **LayoutCollector** fornece acesso programático aos detalhes de paginação, permitindo que você **extraia dados de paginação** como a primeira e a última página de qualquer nó.
- **LayoutEnumerator** permite percorrer a árvore de layout visual, facilitando a localização de páginas, parágrafos ou linhas para renderização ou análise personalizada.
- Juntos, simplificam tarefas complexas de layout que, de outra forma, exigiriam conversões caras para PDF ou cálculos manuais.

## Pré‑requisitos

### Bibliotecas Necessárias e Versões
Certifique‑se de que o Aspose.Words for Java versão 25.3 (ou mais recente) esteja instalado.

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Requisitos de Configuração do Ambiente
- JDK (Java Development Kit) instalado.
- IntelliJ IDEA, Eclipse ou qualquer IDE Java de sua preferência.
- Uma licença válida do Aspose.Words (a avaliação gratuita funciona para testes).

### Pré‑requisitos de Conhecimento
Conhecimento básico de programação Java é suficiente.

## Configurando Aspose.Words
Primeiro, integre a biblioteca Aspose.Words ao seu projeto. Você pode obter uma licença de avaliação gratuita [aqui](https://releases.aspose.com/words/java/) ou usar uma licença temporária para testes.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

Com a biblioteca pronta, podemos mergulhar nas funcionalidades principais.

## Guia de Implementação

### Recurso 1: Usando LayoutCollector para Análise de Intervalo de Páginas
O recurso `LayoutCollector` permite determinar como os nós se estendem por páginas, o que é a base para **extrair dados de paginação**.

#### Visão Geral
Ao aproveitar o `LayoutCollector`, você pode recuperar os índices de página inicial e final de qualquer nó e calcular o total de páginas que ele ocupa.

#### Etapas de Implementação

**1. Inicializar Document e LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Popular o Documento**
Aqui, adicionaremos conteúdo que se estende por várias páginas:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Atualizar Layout e Recuperar Métricas**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### Explicação
- **`DocumentBuilder`** insere texto e quebras de página/seção.
- **`updatePageLayout()`** recalcula as informações de layout para que os dados de paginação estejam corretos.

### Recurso 2: Percorrendo com LayoutEnumerator
`LayoutEnumerator` permite navegação eficiente pela árvore de layout visual.

#### Visão Geral
Você pode percorrer páginas, parágrafos, linhas e outras entidades de layout, o que é útil para renderização personalizada ou diagnósticos.

#### Etapas de Implementação

**1. Inicializar Document e LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. Percorrer para Frente e para Trás**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Explicação
- **`moveParent()`** move o enumerador para a entidade pai (neste caso, o nível da página).
- Os métodos de travessia recursiva permitem explorar toda a hierarquia de layout.

### Recurso 3: Callbacks de Layout de Página
Implemente callbacks para monitorar eventos de layout e **renderizar páginas como imagens** quando necessário.

#### Visão Geral
A interface `IPageLayoutCallback` notifica quando uma parte do documento termina de ser reflowed ou quando a conversão é concluída.

#### Etapas de Implementação

**1. Definir Callback**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Implementar Métodos de Callback**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### Explicação
- **`notify()`** reage a eventos de layout.
- **`ImageSaveOptions`** junto com `PageSet` permite **renderizar páginas como imagens** (PNG neste exemplo).

### Recurso 4: Reiniciar a Numeração de Páginas em Seções Contínuas
Controle a numeração de páginas quando você tem várias seções que fluem continuamente.

#### Visão Geral
Ao definir a opção `ContinuousSectionRestart`, você decide se os números de página reiniciam em uma nova página ou continuam de forma contínua.

#### Etapas de Implementação

**1. Carregar Documento**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Configurar Opções de Numeração de Páginas**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### Explicação
- **`setContinuousSectionPageNumberingRestart()`** indica ao Aspose.Words como lidar com a numeração em seções contínuas.
- Após alterar a opção, **atualize o layout da página** para aplicar as mudanças.

## Aplicações Práticas
1. **Análise de Paginação de Documentos** – Use `LayoutCollector` para auditar como o conteúdo se distribui pelas páginas e ajuste margens ou quebras conforme necessário.
2. **Renderização de PDF** – Combine `LayoutEnumerator` com o callback para gerar imagens de página de alta fidelidade antes da conversão para PDF.
3. **Atualizações Dinâmicas de Documentos** – Reaja a eventos de layout (por exemplo, após a expansão de uma tabela) e re‑renderize automaticamente as páginas afetadas.
4. **Relatórios Multi‑Seção** – Aplique **reinício da numeração de páginas** para dar a cada capítulo seu próprio esquema de numeração mantendo o fluxo contínuo.

## Considerações de Desempenho
- Remova seções não usadas ou conteúdo oculto antes de chamar `updatePageLayout()` para manter o processamento rápido.
- Use APIs de streaming para documentos grandes a fim de evitar carregar o arquivo inteiro na memória.
- Limite a profundidade da travessia recursiva em `LayoutEnumerator` se precisar apenas de informações ao nível da página.

## Problemas Comuns e Soluções
| Problema | Causa | Correção |
|----------|-------|----------|
| `layoutCollector.getNumPagesSpanned()` retorna 0 | Layout não atualizado | Chame `doc.updatePageLayout()` antes de consultar |
| Imagens não são geradas no callback | Configuração ausente de `ImageSaveOptions` | Certifique‑se de definir `saveOptions.setPageSet(new PageSet(pageIndex))` |
| Números de página não reiniciam | Valor incorreto de `ContinuousSectionRestart` | Use `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` para reinício verdadeiro |

## Perguntas Frequentes

**P: Posso extrair o número exato da página de um parágrafo específico?**  
R: Sim—use `LayoutCollector` para obter a página inicial do nó do parágrafo e então chame `doc.updatePageLayout()` para garantir que os dados estejam atualizados.

**P: O `update page layout` afeta o conteúdo do documento?**  
R: Não. Ele apenas recalcula as informações de layout; o texto e a formatação permanecem inalterados.

**P: Como renderizo todas as páginas de um documento grande como imagens de forma eficiente?**  
R: Implemente `IPageLayoutCallback` e processe cada página sequencialmente, opcionalmente usando multithreading para gravação I/O‑bound.

**P: É possível reiniciar a numeração apenas para certas seções?**  
R: Sim—aplique `setContinuousSectionPageNumberingRestart` às opções de layout da seção específica antes de chamar `updatePageLayout()`.

**P: Em qual versão do Aspose.Words o `LayoutCollector` foi introduzido?**  
R: `LayoutCollector` está disponível desde as versões iniciais de 2020; os exemplos utilizam a versão 25.3.

## Conclusão
Ao dominar **reinício da numeração de páginas**, `LayoutCollector` e `LayoutEnumerator`, você agora possui um conjunto poderoso de ferramentas para processamento avançado de texto no Aspose.Words for Java. Seja para **extrair dados de paginação**, **renderizar páginas como imagens** ou simplesmente controlar a numeração de páginas entre seções, essas APIs oferecem controle preciso e programático mantendo alto desempenho.

---

**Última atualização:** 2026-01-14  
**Testado com:** Aspose.Words for Java 25.3  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}