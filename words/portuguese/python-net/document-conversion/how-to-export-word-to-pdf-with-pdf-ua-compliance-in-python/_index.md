---
category: general
date: 2026-10-16
description: Exporte Word para PDF com conformidade PDF/UA usando Aspose.Words para
  Python. Aprenda como definir a conformidade, tornar o PDF/UA compatível e criar
  arquivos PDF/UA em minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- export word to pdf
- how to set compliance
- make pdf/ua compliant
- create pdf/ua
language: pt
lastmod: 2026-10-16
og_description: Exporte Word para PDF com conformidade PDF/UA usando Aspose.Words
  para Python. Este tutorial mostra passo a passo como definir a conformidade, tornar
  o PDF/UA compatível e criar arquivos PDF/UA rapidamente.
og_image_alt: Screenshot of Python code exporting a Word document to a PDF/UA‑compliant
  file
og_title: Exportar Word para PDF com conformidade PDF/UA – Guia Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Export Word to PDF with PDF/UA compliance using Aspose.Words for Python.
    Learn how to set compliance, make PDF/UA compliant, and create PDF/UA files in
    minutes.
  headline: How to export Word to PDF with PDF/UA compliance in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF/UA
title: Como exportar Word para PDF com conformidade PDF/UA em Python
url: /pt/python/document-conversion/how-to-export-word-to-pdf-with-pdf-ua-compliance-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportar Word para PDF com conformidade PDF/UA em Python

Se você precisa **exportar Word para PDF** garantindo que o arquivo atenda aos padrões PDF/UA, este guia mostra exatamente como fazer. Vamos percorrer **como definir a conformidade**, como **tornar PDF/UA compatível**, e como **criar documentos PDF/UA** com Aspose.Words for Python.

Você aprenderá um script completo e executável que carrega um `.docx`, configura as opções de salvamento PDF para PDF/UA 1.2 e grava o PDF compatível no disco. Nenhuma referência externa é necessária — apenas o código abaixo e uma cópia licenciada do Aspose.Words.

## Pré-requisitos

* Python 3.8 ou mais recente instalado.
* Uma licença válida do Aspose.Words for Python (a versão de avaliação funciona, mas adiciona uma marca d'água).
* O pacote `aspose-words` instalado via `pip install aspose-words`.
* Um documento Word (`.docx`) que você deseja converter, por exemplo, `doc_with_rules.docx`.

## Instalar Aspose.Words for Python

```bash
pip install aspose-words
```

O pacote fornece o namespace `aspose.words` usado nos exemplos de código.

## Carregar o documento Word

```python
import aspose.words as aw

# Step 1: Load the source document
doc_path = "YOUR_DIRECTORY/doc_with_rules.docx"
doc = aw.Document(doc_path)
```

*Por que esta etapa importa*: O objeto `Document` representa todo o arquivo Word na memória, proporcionando acesso a todo o conteúdo, estilos e metadados necessários para a conversão.

## Como definir a conformidade para PDF/UA

```python
# Step 2: Create PDF save options and enable PDF/UA compliance
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.compliance = aw.saving.PdfCompliance.PDF_UA_1_2
```

Definir a propriedade `compliance` indica ao Aspose.Words que ele deve gerar um PDF que esteja em conformidade com a especificação PDF/UA 1.2, que é necessária para documentos PDF acessíveis.

## Tornar PDF/UA compatível e salvar o arquivo

```python
# Step 3: Save the document as a PDF/UA‑compatible file
output_path = "YOUR_DIRECTORY/ua_compliant.pdf"
doc.save(output_path, pdf_opts)
print(f"PDF/UA file saved to: {output_path}")
```

Quando `doc.save` recebe o `PdfSaveOptions` com a flag de conformidade, o arquivo resultante é **compatível com PDF/UA**. Você pode verificar a conformidade com ferramentas como Adobe Acrobat Pro (File → Properties → Description → PDF/A and PDF/UA).

## Script completo

Juntando tudo, aqui está o script completo, pronto‑para‑executar:

```python
import aspose.words as aw

# Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/doc_with_rules.docx")

# Configure PDF/UA compliance
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.compliance = aw.saving.PdfCompliance.PDF_UA_1_2

# Save as PDF/UA
doc.save("YOUR_DIRECTORY/ua_compliant.pdf", pdf_opts)

print("Export complete: PDF/UA file created successfully.")
```

**Saída esperada**: Um arquivo chamado `ua_compliant.pdf` localizado em `YOUR_DIRECTORY`. Ao abri‑lo em um visualizador de PDF, não haverá avisos de acessibilidade, confirmando que ele atende ao PDF/UA 1.2.

## Casos de borda e dicas práticas

| Situação | Recomendação |
|-----------|----------------|
| **Versão antiga do Aspose.Words** | A propriedade `compliance` foi introduzida na versão 22.5. Atualize com `pip install --upgrade aspose-words`. |
| **Documentos grandes** | Use `doc.save` com um `MemoryStream` primeiro, depois grave no disco para evitar picos de memória. |
| **Caminhos multiplataforma** | Prefira `pathlib.Path` para manipulação de caminhos: `from pathlib import Path; doc_path = Path("YOUR_DIRECTORY") / "doc_with_rules.docx"` |
| **Licença ausente** | A versão de avaliação adiciona uma marca d'água; obtenha uma licença para produzir arquivos PDF/UA limpos. |

## Verificar conformidade PDF/UA

Você pode verificar programaticamente a conformidade usando Aspose.PDF (opcional) ou manualmente:

```python
import aspose.pdf as ap

pdf_doc = ap.Document("YOUR_DIRECTORY/ua_compliant.pdf")
print("Is PDF/UA compliant?", pdf_doc.is_compliant(ap.pdf.PdfCompliance.PDF_UA_1_2))
```

Se o script imprimir `True`, o arquivo está em conformidade com PDF/UA 1.2.

## Conclusão

Agora você sabe como **exportar Word para PDF** enquanto **torna PDF/UA compatível** e **cria arquivos PDF/UA** usando Aspose.Words for Python. A solução completa carrega um documento Word, define a flag de conformidade PDF/UA e salva o PDF acessível em três etapas concisas.

### Próximos passos

* Explore a adição de **document tags** (`doc.tags`) para melhorar os metadados de acessibilidade.
* Aprenda a gerar arquivos **PDF/A‑2b** para fins de arquivamento (`PdfCompliance.PDF_A_2B`).
* Combine este fluxo de trabalho com **processamento em lote** para converter vários arquivos Word em uma única execução.

Sinta-se à vontade para experimentar diferentes opções de salvamento — como incorporar fontes ou compactar imagens — para ajustar a saída PDF aos requisitos do seu projeto. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar PDF a partir do Word – Guia Python completo com Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Criar PDF acessível a partir do Word com Python – Guia passo a passo](/words/english/python-net/document-conversion/create-accessible-pdf-from-word-with-python-step-by-step-gui/)
- [Criar PDF acessível a partir do Word – Guia completo do Aspose.Words](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}