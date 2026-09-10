---
date: 2025-12-20
description: Aprenda como carregar HTML e converter HTML para DOCX com Aspose.Words
  for Java. Guia passo a passo mostra como salvar arquivos DOCX e usar tags de documento
  estruturado.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Como carregar HTML e salvar como DOCX usando Aspose.Words para Java
url: /pt/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como Carregar HTML e Salvar como DOCX usando Aspose.Words para Java

## Introdução ao Carregamento e Salvamento de Documentos HTML com Aspose.Words para Java

Neste artigo, exploraremos **como carregar html** e salvá-lo como um arquivo DOCX usando a biblioteca Aspose.Words para Java. Aspose.Words é uma API poderosa que permite manipular documentos Word programaticamente, e inclui suporte robusto para importação/exportação de HTML. Percorreremos todo o processo, desde a configuração das opções de carregamento até a persistência do resultado como um documento Word.

## Respostas Rápidas
- **Qual é a classe principal para carregar HTML?** `Document` junto com `HtmlLoadOptions`.
- **Qual opção habilita Structured Document Tags?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Posso converter HTML para DOCX em um único passo?** Sim – carregue o HTML e chame `doc.save(...".docx")`.
- **Preciso de uma licença para desenvolvimento?** Uma avaliação gratuita funciona para testes; uma licença comercial é necessária para produção.
- **Qual versão do Java é necessária?** Java 8 ou superior é suportado.

## O que é “como carregar html” no contexto do Aspose.Words?

Carregar HTML significa ler uma string ou arquivo HTML e convertê-lo em um objeto `Document` do Aspose.Words. Esse objeto pode então ser editado, formatado ou salvo em qualquer formato suportado pela API, como DOCX, PDF ou RTF.

## Por que usar Aspose.Words para conversão de HTML‑para‑DOCX?

- **Preserva o layout** – tabelas, listas e imagens são mantidas intactas.
- **Suporta Structured Document Tags** – ideal para criar controles de conteúdo no Word.
- **Não requer Microsoft Office** – funciona em qualquer servidor ou ambiente de nuvem.
- **Alto desempenho** – processa arquivos HTML grandes rapidamente.

## Pré-requisitos

1. **Biblioteca Aspose.Words para Java** – faça o download em [here](https://releases.aspose.com/words/java/).
2. **Ambiente de Desenvolvimento Java** – JDK 8+ instalado e configurado.
3. **Familiaridade básica com Java I/O** – usaremos `ByteArrayInputStream` para fornecer a string HTML.

## Como Carregar Documentos HTML

Abaixo está um exemplo conciso que demonstra o carregamento de um trecho HTML enquanto habilita o recurso de **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Explicação**

- Criamos uma string `HTML` que contém um controle `<select>` simples.
- `HtmlLoadOptions` permite especificar como o HTML deve ser interpretado. Definir o tipo de controle preferido para `STRUCTURED_DOCUMENT_TAG` indica ao Aspose.Words que converta os controles de formulário HTML em controles de conteúdo do Word.
- O construtor `Document` lê o HTML de um `ByteArrayInputStream` usando codificação UTF‑8.

## Como Salvar como DOCX (Converter HTML para DOCX)

Depois que o HTML é carregado em um `Document`, salvá-lo como um arquivo DOCX é simples:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Substitua `"Your Directory Path"` pela pasta real onde você deseja que o arquivo de saída seja criado.

## Código Fonte Completo para Carregar e Salvar Documentos HTML

Abaixo está o exemplo completo, pronto‑para‑executar, que combina as etapas de carregamento e salvamento. Sinta‑se à vontade para copiar‑colar no seu IDE.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Armadilhas Comuns & Dicas

| Problema | Por que acontece | Como corrigir |
|----------|------------------|---------------|
| **Fontes ausentes** | HTML referencia fontes que não estão instaladas no servidor. | Incorpore fontes no DOCX usando `FontSettings` ou garanta que as fontes necessárias estejam disponíveis. |
| **Imagens não exibidas** | Caminhos de imagem relativos não podem ser resolvidos. | Use URLs absolutas ou carregue imagens em um `MemoryStream` e defina `HtmlLoadOptions.setImageSavingCallback`. |
| **Tipo de controle não convertido** | `setPreferredControlType` não definido ou definido com o enum errado. | Verifique se está usando `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Problemas de codificação** | String HTML codificada com um charset diferente. | Sempre use `StandardCharsets.UTF_8` ao converter a string em bytes. |

## Perguntas Frequentes

### Como instalo o Aspose.Words para Java?

Aspose.Words para Java pode ser baixado em [here](https://releases.aspose.com/words/java/). Siga o guia de instalação na página de download para adicionar os arquivos JAR ao classpath do seu projeto.

### Posso carregar documentos HTML complexos usando Aspose.Words?

Sim, Aspose.Words para Java pode lidar com HTML complexo, incluindo tabelas aninhadas, estilos CSS e elementos interativos sem JavaScript. Ajuste `HtmlLoadOptions` (por exemplo, `setLoadImages` ou `setCssStyleSheetFileName`) para refinar a importação.

### Quais outros formatos de documento o Aspose.Words suporta?

Aspose.Words suporta DOC, DOCX, RTF, HTML, PDF, EPUB, XPS e muitos outros. A API fornece salvamento em uma linha para qualquer um desses formatos.

### O Aspose.Words é adequado para automação de documentos em nível empresarial?

Absolutamente. É usado por grandes empresas para geração automática de relatórios, conversão em massa de documentos e processamento de documentos no servidor sem dependências do Microsoft Office.

### Onde posso encontrar mais documentação e exemplos para Aspose.Words para Java?

Você pode explorar a referência completa da API e tutoriais adicionais no site de documentação do Aspose.Words para Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Última atualização:** 2025-12-20  
**Testado com:** Aspose.Words for Java 24.12 (mais recente no momento da escrita)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}