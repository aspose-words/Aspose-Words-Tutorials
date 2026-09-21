---
category: general
date: 2026-09-21
description: Aprenda a criar um PDF acessível, converter DOCX para PDF e adicionar
  acessibilidade ao PDF com Aspose.Words para Python em um único guia passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create accessible pdf
- convert docx to pdf
- save word as pdf
- accessible pdf from word
- add accessibility to pdf
language: pt
lastmod: 2026-09-21
og_description: Crie um PDF acessível a partir de um arquivo DOCX usando Python. Este
  tutorial mostra como converter docx para pdf, salvar Word como pdf e adicionar acessibilidade
  ao pdf com Aspose.Words.
og_image_alt: Screenshot of a Python script converting a DOCX file into an accessible
  PDF
og_title: Crie um PDF acessível a partir do Word com Python – guia completo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create an accessible PDF, convert docx to PDF, and add
    accessibility to PDF with Aspose.Words for Python in a single step-by-step guide.
  headline: How to create an accessible PDF from a Word document using Python
  type: TechArticle
- description: Learn how to create an accessible PDF, convert docx to PDF, and add
    accessibility to PDF with Aspose.Words for Python in a single step-by-step guide.
  name: How to create an accessible PDF from a Word document using Python
  steps:
  - name: 1. Load the source DOCX file
    text: '```python import aspose.words as aw'
  - name: 2. Configure PDF save options for accessibility
    text: '```python # Step 2: Create PDF save options pdf_options = aw.saving.PdfSaveOptions()
      ```'
  - name: 3. Enable PDF/UA compliance (PDF/UA‑1.2)
    text: '```python # Step 3: Enable PDF/UA compliance for accessibility pdf_options.compliance
      = aw.saving.PdfCompliance.PDF_UA_1_2 ```'
  - name: 4. Save the document as an accessible PDF
    text: '```python # Step 4: Save the document as an accessible PDF doc.save("YOUR_DIRECTORY/accessible.pdf",
      pdf_options) print("Accessible PDF created at YOUR_DIRECTORY/accessible.pdf")
      ```'
  - name: 5. Verify PDF/UA compliance (optional)
    text: 'If you want to confirm that the PDF meets PDF/UA criteria, you can run
      an open‑source validator such as **veraPDF**:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF/UA
- Document conversion
title: Como criar um PDF acessível a partir de um documento Word usando Python
url: /pt/python/document-conversion/how-to-create-an-accessible-pdf-from-a-word-document-using-p/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um PDF acessível a partir de um documento Word usando Python

Se você precisa **criar PDFs acessíveis** a partir do Microsoft Word, este guia mostra os passos exatos. Você aprenderá como **converter docx para pdf**, **salvar word como pdf**, e **adicionar acessibilidade ao pdf** com uma única chamada de biblioteca.

A solução funciona com Aspose.Words for Python via .NET, que implementa a conformidade PDF/UA‑1.2 automaticamente. Nenhuma ferramenta externa ou pós‑processamento manual é necessário, permitindo integrar o fluxo de trabalho em qualquer pipeline de automação.

## Pré-requisitos

* Python 3.8 ou superior instalado
* Uma licença válida do Aspose.Words for Python via .NET (ou uma chave de avaliação gratuita)
* O documento Word de entrada (`input.docx`) localizado em um diretório conhecido
* Acesso à internet para instalar o pacote `aspose-words` via `pip`

## Instalar Aspose.Words para Python

Execute o comando a seguir no seu terminal ou ambiente virtual:

```bash
pip install aspose-words
```

O pacote inclui tanto o wrapper Python quanto as bibliotecas .NET subjacentes, portanto nenhum binário adicional é necessário.

## Implementação passo a passo

### 1. Carregar o arquivo DOCX fonte

```python
import aspose.words as aw

# Step 1: Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

A classe `Document` analisa o arquivo DOCX e constrói uma representação em memória que preserva estilos, títulos, imagens e tags de acessibilidade (como texto alternativo para imagens).

### 2. Configurar opções de salvamento PDF para acessibilidade

```python
# Step 2: Create PDF save options
pdf_options = aw.saving.PdfSaveOptions()
```

`PdfSaveOptions` permite controlar como o PDF é gerado. Por padrão, a saída é uma réplica visual do arquivo Word; você pode habilitar a conformidade PDF/UA no próximo passo.

### 3. Habilitar conformidade PDF/UA (PDF/UA‑1.2)

```python
# Step 3: Enable PDF/UA compliance for accessibility
pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1_2
```

Definir `PdfCompliance.PDF_UA_1_2` marca o arquivo resultante como PDF/UA‑1.2, o que atende à maioria dos padrões de acessibilidade (navegação por leitor de tela, conteúdo marcado, ordem de leitura correta). Essa única linha substitui toda uma série de ferramentas de marcação manual.

### 4. Salvar o documento como um PDF acessível

```python
# Step 4: Save the document as an accessible PDF
doc.save("YOUR_DIRECTORY/accessible.pdf", pdf_options)
print("Accessible PDF created at YOUR_DIRECTORY/accessible.pdf")
```

O método `save` grava o PDF no disco usando as opções definidas anteriormente. O arquivo de saída contém:

* Conteúdo marcado que corresponde à estrutura do Word
* Informação de idioma do documento
* Texto alternativo para imagens (se presente no DOCX)
* Hierarquia de títulos adequada para tecnologias assistivas

### 5. Verificar conformidade PDF/UA (opcional)

Se você deseja confirmar que o PDF atende aos critérios PDF/UA, pode executar um validador de código aberto como o **veraPDF**:

```bash
verapdf --format text YOUR_DIRECTORY/accessible.pdf
```

Um relatório limpo indica que o **pdf acessível a partir do word** está pronto para distribuição.

## Script completo para copiar e colar rapidamente

```python
# ------------------------------------------------------------
# Create an accessible PDF from a Word document (Python)
# ------------------------------------------------------------
# Prerequisites:
#   pip install aspose-words
#   Valid Aspose.Words license (optional for evaluation)
# ------------------------------------------------------------
import aspose.words as aw

def create_accessible_pdf(input_path: str, output_path: str) -> None:
    """
    Converts a DOCX file to a PDF/UA‑1.2 compliant PDF.
    
    Args:
        input_path: Path to the source .docx file.
        output_path: Destination path for the accessible PDF.
    """
    # Load the source document
    doc = aw.Document(input_path)

    # Configure PDF save options for accessibility
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1_2

    # Save the document as an accessible PDF
    doc.save(output_path, pdf_options)
    print(f"Accessible PDF created at {output_path}")

if __name__ == "__main__":
    create_accessible_pdf(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/accessible.pdf"
    )
```

Executar este script produz um PDF que satisfaz os requisitos de **adicionar acessibilidade ao pdf** ao mesmo tempo que demonstra como **salvar word como pdf** em um formato acessível.

## Perguntas comuns e casos extremos

| Pergunta | Resposta |
|----------|----------|
| **E se o DOCX contiver imagens sem texto alternativo?** | Aspose.Words copia qualquer texto alternativo existente. Se não houver, o PDF conterá um atributo `Alt` vazio. Adicione texto alternativo no Word antes da conversão para total conformidade. |
| **Posso personalizar os metadados do PDF (autor, título)?** | Sim. Use `pdf_options.metadata` para definir `Author`, `Title` e outros campos antes de chamar `doc.save`. |
| **O suporte a PDF/UA está disponível em versões mais antigas do Aspose.Words?** | A conformidade PDF/UA foi introduzida na versão 22.9. Atualize se encontrar a enumeração `PdfCompliance` ausente. |
| **A conversão preservará tabelas complexas?** | O motor de layout reproduz as estruturas de tabelas fielmente, e as tags resultantes preservam a ordem lógica, o que é essencial para casos de uso de **converter docx para pdf**. |
| **Como lidar com arquivos DOCX protegidos por senha?** | Carregue o documento com um objeto `LoadOptions` que inclua a senha, então prossiga com os mesmos passos. |

## Dicas profissionais

* **Processamento em lote** – Envolva a chamada `create_accessible_pdf` em um loop para converter uma pasta inteira de arquivos DOCX.
* **Desempenho** – Reutilize uma única instância de `PdfSaveOptions` ao processar muitos arquivos para reduzir a sobrecarga de alocação de objetos.
* **Testes** – Inclua um teste automatizado que execute `verapdf` na saída e falhe a compilação se aparecerem erros de conformidade.

## Conclusão

Agora você sabe como **criar PDFs acessíveis** diretamente do Word usando Python. A solução completa cobre **converter docx para pdf**, **salvar word como pdf**, e **adicionar acessibilidade ao pdf** em apenas quatro linhas de código, garantindo conformidade PDF/UA‑1.2 sem ferramentas adicionais.

Em seguida, explore tópicos relacionados como **extrair texto de PDFs acessíveis**, **adicionar tags personalizadas**, ou **integrar a conversão em uma API web**. Essas extensões permitem construir fluxos de trabalho de documentos totalmente automatizados e focados em acessibilidade.

---

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar PDF Acessível a partir de DOCX – Guia Completo da Aspose](/words/english/net/basic-conversions/create-accessible-pdf-from-docx-complete-aspose-guide/)
- [Criar PDF Acessível a partir de DOCX – Guia Completo](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-complete-guide/)
- [Criar PDF Acessível – Guia Passo a Passo para Conformidade PDF/UA](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-step-by-step-guide-for-pdf-ua-complian/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}