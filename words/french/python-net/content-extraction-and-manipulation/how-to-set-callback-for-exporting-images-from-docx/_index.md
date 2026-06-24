---
category: general
date: 2026-06-24
description: Comment définir un rappel pour exporter les images d’un DOCX lors de
  l’enregistrement en Markdown. Apprenez à extraire les images, à extraire les SVG
  depuis Word et à enregistrer un DOCX en Markdown avec une gestion personnalisée.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: fr
og_description: Comment définir un rappel pour exporter les images d’un DOCX lors
  de la conversion en Markdown. Ce guide vous montre comment extraire les images et
  les SVG efficacement.
og_title: Comment définir un rappel pour l'exportation d'images depuis un DOCX
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
title: Comment définir un rappel pour l'exportation d'images depuis un DOCX
url: /fr/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir un rappel pour l'exportation d'images depuis DOCX

Vous vous êtes déjà demandé **comment définir un rappel** afin de **exporter des images depuis DOCX** lors de la conversion en Markdown ? Vous n'êtes pas le seul. De nombreux développeurs se heurtent à un mur lorsque la conversion par défaut place toutes les images dans un dossier générique ou, pire, perd complètement les graphiques SVG.

Dans ce tutoriel, nous parcourrons une solution complète, prête à l’emploi, qui répond à la question « comment définir un rappel », montre **comment extraire des images**, et couvre même **l'extraction de SVG depuis Word**. À la fin, vous pourrez **enregistrer un DOCX en Markdown** avec un schéma de nommage personnalisé pour chaque ressource image — sans aucune manipulation manuelle.

## Ce que vous apprendrez

- Pourquoi un rappel est la façon la plus propre de contrôler les noms de fichiers d’image pendant la conversion.  
- Comment se brancher sur `MarkdownSaveOptions.resource_saving_callback` d’Aspose.Words.  
- Code étape par étape qui extrait les **PNG**, **JPG**, **SVG**, et toute autre ressource incorporée.  
- Astuces pour gérer les collisions de noms, les gros fichiers et les particularités de chemins multiplateformes.  

> **Conseil pro :** Si vous utilisez déjà Aspose.Words dans un pipeline plus large, vous pouvez insérer ce rappel sans toucher au reste de votre code.

![Diagramme de mise en place du rappel](https://example.com/images/how-to-set-callback.png "comment définir un rappel")

## Prérequis

- Python 3.8+ (l’exemple utilise des f‑strings, donc 3.6+ suffit).  
- Package `aspose-words` installé (`pip install aspose-words`).  
- Un fichier DOCX contenant des images raster **et** des graphiques vectoriels (SVG).  
- Familiarité de base avec les fonctions Python et les entrées‑sorties de fichiers.

Si vous avez tout cela, plongeons‑y.

## Comment définir un rappel pour l'exportation d'images depuis DOCX

Le cœur de la solution réside dans un **rappel d’enregistrement de ressource**. Aspose.Words appelle ce délégué pour chaque image ou SVG qu’il souhaite écrire lorsque vous invoquez `document.save`. En renvoyant un tuple `(new_name, data)`, vous définissez à la fois le nom de fichier et le contenu binaire.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Pourquoi un rappel ?

Sans rappel, Aspose.Words crée des fichiers nommés `image1.png`, `image2.svg`, etc., et les place dans un dossier à côté du fichier Markdown. Cela suffit pour des démonstrations rapides, mais en production vous avez souvent besoin de :

1. **Noms déterministes** – utiles pour le contrôle de version ou la publication sur CDN.  
2. **Évitement des collisions** – deux images avec le même nom d’origine ne s’écraseront pas.  
3. **Structures de dossiers personnalisées** – peut‑être souhaitez‑vous que tous les actifs soient sous `/assets/docs/`.

Le rappel vous donne un contrôle total sur ces trois exigences.

---

## Exporter des images depuis DOCX à l’aide d’un rappel de ressource

Voici l’implémentation du rappel. Il calcule le hachage des données binaires pour produire un suffixe unique, conserve l’extension de fichier d’origine, et renvoie le nouveau nom de fichier ainsi que les octets bruts.

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

#### Gestion des cas limites

- **Fichiers volumineux :** SHA‑256 fonctionne bien pour n’importe quelle taille ; le hachage est calculé en mémoire, donc soyez conscient des contraintes de mémoire si vous traitez d’énormes PDF.  
- **Extensions manquantes :** Certains anciens fichiers Word peuvent stocker des images sans extension explicite. Dans ce cas, `extension` sera vide ; vous pouvez par défaut utiliser `.bin` ou inspecter les premiers octets pour deviner le format.  
- **Ressources non‑image :** Le rappel est invoqué pour chaque ressource externe (par ex., objets OLE). Si vous ne vous intéressez qu’aux images/SVG, filtrez par `resource.type` avant de poursuivre.

---

## Comment extraire des images et des SVG depuis Word

Nous allons maintenant connecter le rappel au pipeline d’enregistrement Markdown. L’objet `MarkdownSaveOptions` expose la propriété `resource_saving_callback` exactement à cette fin.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Définir `resource_folder` est optionnel mais souvent pratique. Si vous l’omettez, les images se retrouvent à côté du fichier Markdown, ce qui peut encombrer la racine de votre projet.

### Enregistrement du document

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

Lorsque vous exécutez le script, vous verrez une série de fichiers tels que :

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

Et le `output.md` généré contiendra des liens d’image pointant vers ces noms de fichiers exacts :

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

C’est la partie **extraction d’images** en action — chaque image, raster ou vecteur, est maintenant une ressource distincte, nommée de façon unique.

---

## Enregistrer DOCX en Markdown avec une gestion d’image personnalisée

En rassemblant le tout, voici le script complet que vous pouvez copier‑coller dans un fichier nommé `convert_docx_to_md.py` :

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

**Pourquoi cela fonctionne :**  
- Le `resource_callback` garantit que chaque image obtient un nom unique et reproductible.  
- `resource_folder` maintient le Markdown propre en séparant les actifs.  
- Les appels `os.makedirs` vous protègent des erreurs « dossier introuvable » lorsque le script s’exécute sur une machine vierge.

## Extraire les SVG depuis Word – Qu’en est‑il des graphiques vectoriels ?

Les SVG sont traités de la même façon que les PNG par le rappel car ils ne sont qu’une autre `resource`. La seule nuance est que certaines versions plus anciennes de Word intègrent les SVG comme des objets *OfficeArt*, que Aspose.Words convertit automatiquement en PNG raster à moins que vous n’activiez explicitement le drapeau **preserve SVG** :

```python
md_options.export_svg = True  # Keep original SVG markup
```

Ajoutez cette ligne avant l’enregistrement, et le rappel recevra des ressources avec une extension `.svg`, préservant les données vectorielles nettes — parfait pour les documents web responsives.

## Questions fréquentes & pièges

| Question | Réponse |
|----------|--------|
| **Et si deux images sont identiques ?** | Le hachage SHA‑256 sera identique, donc les noms de fichiers entreront en collision. Si vous avez besoin des deux copies, incluez le `resource.name` original dans le calcul du hachage (par ex., `hash(resource.name + resource.data)`). |
| **Puis-je changer le dossier selon le type de fichier ?** | Oui. À l’intérieur de `resource_callback` vous pouvez inspecter `extension` et renvoyer un chemin comme `f"png/{new_name}"` pour les images raster et `f"svg/{new_name}"` pour les vecteurs. |
| **Cela fonctionne‑t‑il sur Linux/macOS ?** | Absolument. Le code utilise `os.path` qui abstrait les séparateurs de chemin. Assurez‑vous simplement que le fichier de licence Aspose.Words (`aspose.words.lic`) est accessible si vous utilisez une version payante. |
| **Qu’en est‑il de l’utilisation de la mémoire pour les documents volumineux ?** | Le rappel reçoit le **tableau d’octets complet** pour chaque ressource, ce qui signifie que l’image entière réside temporairement en mémoire. Pour des fichiers de plusieurs gigaoctets, vous pourriez vouloir diffuser les données vers le disque à l’intérieur du rappel plutôt que de les renvoyer. |

## Conclusion

Vous savez maintenant **comment définir un rappel** pour contrôler l’extraction d’images lorsque vous **enregistrez un DOCX en Markdown**. Cette approche vous permet **d’exporter des images depuis DOCX**, **d’extraire des SVG depuis Word**, et de garder votre Markdown propre et déterministe.

Dans un script unique et autonome, nous avons couvert le chargement d’un document, la définition d’un rappel d’enregistrement de ressource, la configuration de `MarkdownSaveOptions`, et la gestion des cas limites comme les collisions de noms et les graphiques vectoriels. Le résultat est un ensemble d’actifs nommés de façon unique à côté d’un fichier Markdown parfaitement lié — prêt pour les générateurs de sites statiques, les pipelines de documentation, ou tout flux de travail nécessitant des actifs propres et réutilisables.

**Prochaines étapes ?**  
- Essayez d’enchaîner cela avec un générateur de site statique comme MkDocs pour publier automatiquement des docs basés sur Word.  
- Expérimentez avec `markdown_options.export_images_as_base64 = True` si vous préférez les images en ligne plutôt que des fichiers externes.  
- Approfondissez les autres rappels d’Aspose.Words (par ex., `document_saving_callback`) pour contrôler directement la sortie Markdown.

Vous avez d’autres questions sur **comment extraire des images** d’autres formats Office, ou besoin d’aide pour ajuster le rappel selon une convention de nommage spécifique ? Laissez un commentaire ci‑dessous, et bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment renommer les images lors de la conversion de DOCX en Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Comment enregistrer le Markdown depuis DOCX – Guide étape par étape](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}