---
date: 2025-12-24
description: Aprenda como criar arquivos de texto simples a partir de documentos Word
  usando Aspose.Words para Java. Este guia mostra como converter Word para txt, usar
  indentação com tabulação e salvar Word como txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Como criar um arquivo de texto simples com Aspose.Words para Java
url: /pt/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um arquivo de texto simples com Aspose.Words para Java

## Introdução ao Salvamento de Documentos como Arquivos de Texto no Aspose.Words para Java

Neste tutorial, você aprenderá **como criar um arquivo de texto simples** a partir de um documento Word usando a biblioteca Aspose.Words para Java. Seja para **converter word para txt**, automatizar a geração de relatórios ou simplesmente extrair texto bruto para processamento adicional, este guia o conduzirá por todo o fluxo de trabalho — desde a criação do documento até o ajuste fino das opções de salvamento, como **usar indentação com tabulação** ou adicionar marcas bidi. Vamos começar!

## Respostas Rápidas
- **Qual é a classe principal para criar um documento?** `Document` do Aspose.Words.
- **Qual opção adiciona marcas bidi para idiomas da direita para a esquerda?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Como posso indentar itens de lista com tabulações?** Defina `ListIndentation.Character` para `'\t'`.
- **Preciso de uma licença para desenvolvimento?** Um teste gratuito funciona para testes; uma licença é necessária para produção.
- **Posso salvar o arquivo com um nome e caminho personalizados?** Sim — passe o caminho completo para `doc.save()`.

## Pré-requisitos

Antes de começarmos, certifique-se de que você tem os seguintes pré-requisitos:

- Java Development Kit (JDK) instalado em seu sistema.  
- Biblioteca Aspose.Words para Java integrada ao seu projeto. Você pode baixá‑la [aqui](https://releases.aspose.com/words/java/).  
- Conhecimento básico de programação Java.

## Etapa 1: Criar um Documento

Para **salvar word como txt**, primeiro precisamos de uma instância `Document`. Abaixo está um trecho simples em Java que cria um documento e escreve algumas linhas de texto multilíngue:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Neste código criamos um novo documento, adicionamos texto em inglês, hebraico e árabe, e habilitamos a formatação da direita para a esquerda para o parágrafo em hebraico.

## Etapa 2: Definir Opções de Salvamento de Texto

Em seguida, configuramos como o documento será salvo como um arquivo de texto simples. Aspose.Words fornece a classe `TxtSaveOptions`, que permite controlar tudo, desde marcas bidi até a indentação de listas.

### Exemplo 1: Adicionando Marcas Bidi (como salvar txt com suporte RTL adequado)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Definir `AddBidiMarks` como `true` garante que os caracteres da direita para a esquerda sejam representados corretamente no **arquivo de texto simples** resultante.

### Exemplo 2: Usando Caractere de Tabulação para Indentação de Lista (usar indentação com tabulação)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Aqui instruímos o Aspose.Words a prefixar um caractere de tabulação (`'\t'`) antes de cada nível de lista, tornando a saída de texto mais fácil de ler.

## Etapa 3: Salvar o Documento como Texto

Agora que as opções de salvamento estão prontas, você pode persistir o documento como um **arquivo de texto simples**:

```java
doc.save("output.txt", saveOptions);
```

Substitua `"output.txt"` pelo caminho completo onde deseja armazenar o arquivo.

## Código Fonte Completo para Salvar Documentos como Arquivos de Texto no Aspose.Words para Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Problemas Comuns e Soluções

| Problema | Solução |
|----------|---------|
| **Caracteres bidi aparecem como texto corrompido** | Certifique‑se de que `setAddBidiMarks(true)` está habilitado e o arquivo de saída é aberto com codificação UTF‑8. |
| **Indentação da lista parece errada** | Verifique se `ListIndentation.Count` e `Character` estão definidos para os valores desejados (tab `'\t'` ou espaço `' '` ). |
| **Arquivo não criado** | Verifique se o caminho do diretório existe e se a aplicação tem permissões de gravação. |

## Perguntas Frequentes

### Como adiciono marcas bidi à saída de texto?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Posso personalizar o caractere de indentação da lista?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### O Aspose.Words para Java é adequado para lidar com texto multilíngue?

Sim, o Aspose.Words para Java suporta uma ampla variedade de idiomas e codificações de caracteres, tornando‑o ideal para extrair e salvar conteúdo multilíngue como texto simples.

### Como posso acessar mais documentação e recursos para Aspose.Words para Java?

Você pode encontrar documentação abrangente e recursos na página de Documentação do Aspose.Words para Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Onde posso baixar o Aspose.Words para Java?

Você pode baixar a biblioteca no site oficial: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### E se eu precisar **converter word para txt** em um processo em lote?

Envolva o código mostrado acima em um loop que carrega cada arquivo `.docx`, aplica as mesmas `TxtSaveOptions` e salva cada um como `.txt`. Certifique‑se de gerenciar os recursos descartando os objetos `Document` após cada iteração.

### A API suporta salvar diretamente em um stream em vez de um arquivo?

Sim, você pode passar um `OutputStream` para `doc.save(outputStream, saveOptions)` para processamento em memória ou ao integrar com serviços web.

---

**Última atualização:** 2025-12-24  
**Testado com:** Aspose.Words para Java 24.12 (mais recente)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}