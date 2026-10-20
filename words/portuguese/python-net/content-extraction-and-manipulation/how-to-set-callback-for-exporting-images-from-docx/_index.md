---
category: general
date: 2026-06-24
description: Como definir um callback para exportar imagens de DOCX ao salvar como
  Markdown. Aprenda a extrair imagens, extrair SVG do Word e salvar DOCX como Markdown
  com tratamento personalizado.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: pt
og_description: Como definir um callback para exportar imagens de DOCX ao converter
  para Markdown. Este guia mostra como extrair imagens e SVGs de forma eficiente.
og_title: Como definir um callback para exportar imagens de DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Como Configurar um Callback para Exportar Imagens de DOCX
url: /pt/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Definir Callback para Exportar Imagens de DOCX

Já se perguntou **como definir callback** para **exportar imagens de DOCX** ao convertê-lo para Markdown? Você não está sozinho. Muitos desenvolvedores se deparam com um obstáculo quando a conversão padrão despeja todas as imagens em uma pasta genérica ou, pior, perde completamente os gráficos SVG.  

Neste tutorial, percorreremos uma solução completa, pronta‑para‑executar, que responde à pergunta “como definir callback”, mostra **como extrair imagens** e ainda aborda **extrair SVG do Word**. Ao final, você será capaz de **salvar DOCX como Markdown** com um esquema de nomenclatura personalizado para cada recurso de imagem — sem necessidade de ajustes manuais.

## O que Você Vai Aprender

- Por que um callback é a maneira mais limpa de controlar os nomes de arquivos de imagem durante a conversão.  
- Como conectar ao `MarkdownSaveOptions.resource_saving_callback` do Aspose.Words.  
- Código passo a passo que extrai **PNG**, **JPG**, **SVG** e qualquer outro recurso incorporado.  
- Dicas para lidar com colisões de nomes, arquivos grandes e peculiaridades de caminhos entre plataformas.  

> **Dica profissional:** Se você já está usando Aspose.Words em um pipeline maior, pode inserir este callback sem tocar no restante do seu código.

![Diagrama de como definir callback](https://example.com/images/how-to-set-callback.png "como definir callback")

## Pré-requisitos

- Python 3.8+ (o exemplo usa f‑strings, então 3.6+ funciona).  
- Pacote `aspose-words` instalado (`pip install aspose-words`).  
- Um arquivo DOCX que contém imagens raster **e** gráficos vetoriais (SVG).  
- Familiaridade básica com funções Python e I/O de arquivos.

Se você tem isso, vamos mergulhar.

## Como Definir Callback para Exportar Imagens de DOCX

O núcleo da solução reside em um **callback de salvamento de recurso**. Aspose.Words chama esse delegate para cada imagem ou SVG que deseja gravar quando você invoca `document.save`. Ao retornar uma tupla `(new_name, data)` você determina tanto o nome do arquivo quanto o conteúdo em bytes.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Por que um Callback?

Sem um callback, Aspose.Words cria arquivos nomeados `image1.png`, `image2.svg`, etc., e os coloca em uma pasta ao lado do arquivo Markdown. Isso é aceitável para demonstrações rápidas, mas em produção você costuma precisar:

1. Nomes determinísticos – úteis para controle de versão ou publicação em CDN.  
2. Evitar colisões – duas imagens com o mesmo nome original não sobrescreverão uma à outra.  
3. Estruturas de pastas personalizadas – talvez você queira todos os ativos em `/assets/docs/`.

O callback lhe dá controle total sobre essas três questões.

---

## Exportar Imagens de DOCX Usando um Callback de Recurso

Abaixo está a implementação do callback. Ele gera um hash dos dados binários para produzir um sufixo único, preserva a extensão original do arquivo e retorna o novo nome de arquivo juntamente com os bytes brutos.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Tratamento de Casos Limite

- **Arquivos grandes:** SHA‑256 funciona bem para qualquer tamanho; o hash é calculado na memória, portanto fique atento às restrições de memória se estiver processando PDFs enormes.  
- **Extensões ausentes:** Alguns arquivos Word mais antigos podem armazenar imagens sem extensão explícita. Nesse caso `extension` ficará vazio; você pode usar `.bin` como padrão ou inspecionar os primeiros bytes para adivinhar o formato.  
- **Recursos não‑imagem:** O callback é invocado para cada recurso externo (por exemplo, objetos OLE). Se você se importa apenas com imagens/SVGs, filtre por `resource.type` antes de prosseguir.

## Como Extrair Imagens e SVGs do Word

Agora conectamos o callback ao pipeline de salvamento de Markdown. O objeto `MarkdownSaveOptions` expõe a propriedade `resource_saving_callback` exatamente para esse propósito.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Definir `resource_folder` é opcional, mas costuma ser útil. Se você omiti-lo, as imagens ficarão ao lado do arquivo Markdown, o que pode bagunçar a raiz do seu projeto.

### Salvando o Documento

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

Ao executar o script, você verá uma série de arquivos como:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

E o `output.md` gerado conterá links de imagem que apontam para esses nomes de arquivos exatos:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Essa é a parte **como extrair imagens** em ação — cada imagem, raster ou vetor, agora é um recurso separado, com nome único.

## Salvar DOCX como Markdown com Manipulação Personalizada de Imagens

Juntando tudo, aqui está o script completo que você pode copiar‑colar em um arquivo chamado `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Por que isso funciona:**  
- O `resource_callback` garante que cada imagem receba um nome único e reproduzível.  
- `resource_folder` mantém o Markdown organizado ao separar os ativos.  
- As chamadas `os.makedirs` protegem você de erros de “pasta não encontrada” quando o script é executado em uma máquina nova.

## Extrair SVG do Word – E os Gráficos Vetoriais?

SVGs são tratados da mesma forma que PNGs pelo callback porque são apenas outro `resource`. A única nuance é que algumas versões antigas do Word incorporam SVGs como objetos *OfficeArt*, que o Aspose.Words converte automaticamente para um PNG raster, a menos que você habilite explicitamente a flag **preserve SVG**:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Adicione essa linha antes de salvar, e o callback receberá recursos com extensão `.svg`, preservando dados vetoriais nítidos — perfeito para documentos web responsivos.

## Perguntas Frequentes & Armadilhas

| Pergunta | Resposta |
|----------|----------|
| **E se duas imagens forem idênticas?** | O hash SHA‑256 será idêntico, portanto os nomes de arquivos colidirão. Se você precisar de ambas as cópias, inclua o `resource.name` original no cálculo do hash (por exemplo, `hash(resource.name + resource.data)`). |
| **Posso mudar a pasta por tipo de arquivo?** | Sim. Dentro de `resource_callback` você pode inspecionar `extension` e retornar um caminho como `f"png/{new_name}"` para imagens raster e `f"svg/{new_name}"` para vetores. |
| **Isso funciona no Linux/macOS?** | Absolutamente. O código usa `os.path`, que abstrai os separadores de caminho. Apenas certifique-se de que o arquivo de licença do Aspose.Words (`aspose.words.lic`) esteja acessível se você estiver usando a versão paga. |
| **E quanto ao uso de memória para documentos enormes?** | O callback recebe o **array de bytes completo** para cada recurso, o que significa que a imagem inteira fica na memória temporariamente. Para arquivos de vários gigabytes, talvez você queira transmitir os dados para o disco dentro do callback em vez de retorná‑los. |

## Conclusão

Agora você sabe **como definir callback** para controlar a extração de imagens ao **salvar DOCX como Markdown**. A abordagem permite **exportar imagens de DOCX**, **extrair SVG do Word**, e manter seu Markdown limpo e determinístico.  

Em um único script autônomo, cobrimos o carregamento de um documento, a definição de um callback de salvamento de recurso, a configuração de `MarkdownSaveOptions` e o tratamento de casos limites como colisões de nomes e gráficos vetoriais. O resultado é um conjunto de ativos com nomes únicos ao lado de um arquivo Markdown perfeitamente vinculado — pronto para geradores de sites estáticos, pipelines de documentação ou qualquer fluxo de trabalho que precise de ativos limpos e reutilizáveis.

**Próximos passos?**  
- Tente encadear isso com um gerador de site estático como MkDocs para publicar automaticamente documentos baseados em Word.  
- Experimente `markdown_options.export_images_as_base64 = True` se preferir imagens embutidas em vez de arquivos externos.  
- Aprofunde-se nos outros callbacks do Aspose.Words (por exemplo, `document_saving_callback`) para controlar a própria saída de Markdown.  

Tem mais perguntas sobre **como extrair imagens** de outros formatos Office, ou precisa de ajuda para ajustar o callback para uma convenção de nomenclatura específica? Deixe um comentário abaixo, e feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como Renomear Imagens ao Converter DOCX para Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Como Salvar Markdown a partir de DOCX – Guia Passo a Passo](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}