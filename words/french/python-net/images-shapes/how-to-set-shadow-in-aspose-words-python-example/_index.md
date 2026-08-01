---
category: general
date: 2026-08-01
description: Comment définir l’ombre sur une forme Word à l’aide d’Aspose.Words pour
  Python. Apprenez à modifier l’opacité, ajuster le flou et changer rapidement la
  distance de l’ombre.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: fr
lastmod: 2026-08-01
og_description: Comment définir une ombre sur une forme avec Aspose.Words pour Python.
  Suivez ce tutoriel étape par étape pour modifier l’opacité, ajuster le flou et changer
  la distance de l’ombre.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Comment définir l’ombre dans Aspose.Words – Guide rapide Python
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Comment définir l’ombre dans Aspose.Words – Exemple Python
url: /fr/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir une ombre dans Aspose.Words – Exemple Python

Vous vous êtes déjà demandé **comment définir une ombre** sur une forme Word sans ouvrir le document manuellement ? Vous n'êtes pas le seul—de nombreux développeurs rencontrent ce problème lorsqu'ils automatisent des rapports ou créent des modèles cohérents avec la charte graphique. Bonne nouvelle ? Avec Aspose.Words pour Python, vous pouvez ajuster l'ombre d'une forme, son opacité, son flou et sa distance en quelques lignes de code seulement.

Dans ce tutoriel, nous parcourrons un exemple complet et exécutable qui montre **comment définir une ombre**, **comment changer l'opacité**, **comment ajuster le flou**, et même **comment modifier la distance de l'ombre**. À la fin, vous maîtriserez **comment utiliser Aspose.Words** pour styliser les formes de manière programmatique.

---

![Comment définir une ombre sur une forme avec Aspose.Words](image-placeholder.png){alt="Comment définir une ombre sur une forme avec Aspose.Words"}

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

| Exigence | Raison |
|----------|--------|
| Python 3.8+ | Syntaxe moderne, annotations de type |
| `aspose-words` package (pip install aspose-words) | Bibliothèque principale pour la manipulation de Word |
| Un fichier `input.docx` d'exemple contenant au moins une forme | La forme que nous ombrerons |
| Permission d'écriture sur le dossier où vous enregistrerez `output.docx` | Pour conserver les modifications |

Aucun DLL supplémentaire ou interop COM—Aspose.Words est pure‑Python, vous pouvez donc l’exécuter sous Windows, macOS ou Linux.

---

## Comment définir une ombre sur une forme avec Aspose.Words

Ci‑dessous se trouve le script **complet**. Il charge un document, trouve la première forme (récursivement), configure l'ombre et enregistre le résultat. Chaque ligne est commentée afin que vous compreniez **pourquoi** elle est là, pas seulement **ce que** elle fait.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Pourquoi cela fonctionne

* **`doc.get_child(..., True)`** – Le drapeau `True` indique à Aspose.Words de rechercher **récursivement**, de sorte que même les formes situées dans les en‑têtes, pieds de page ou objets groupés soient trouvées. C’est crucial quand vous ne savez pas exactement où se trouve la forme.
* **`shadow_format`** – Cette propriété regroupe tous les paramètres liés à l'ombre. En définissant `distance`, `blur` et `opacity`, vous contrôlez la profondeur visuelle de la forme. Modifier l’une de ces valeurs montre **comment changer l'opacité**, **comment ajuster le flou**, et **modifier la distance de l'ombre** en un seul appel cohérent.
* **Enregistrement** – `doc.save` écrit un nouveau fichier `.docx`. L'original reste intact, ce qui constitue une pratique sûre pour le traitement par lots.

---

## Comment changer l'opacité de l'ombre d'une forme

L'opacité détermine à quel point l'ombre est transparente. La plage va de 0,0 (complètement invisible) à 1,0 (pleinement opaque). Dans le code ci‑dessus, il suffit de modifier l’argument `opacity` :

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Astuce :** Lors de la génération de PDF ultérieure, une opacité plus élevée se traduit souvent par une ombre plus profonde et plus imprimable. Expérimentez avec des valeurs entre 0,4 et 0,9 pour trouver le juste milieu selon vos directives de marque.

---

## Comment ajuster le flou pour un rendu plus doux

Le flou correspond au rayon du flou gaussien appliqué aux bords de l'ombre. Un nombre plus grand produit un effet plume :

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

Si vous avez besoin d’un rendu d’ombre nette (style « Microsoft PowerPoint »), définissez `blur` à une valeur basse comme `1.0`.

---

## Modifier la distance de l'ombre pour créer de la profondeur

La distance est mesurée en points (1 pt = 1/72 in). Éloigner davantage l'ombre fait apparaître la forme comme flottant plus haut :

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Combinez une `distance` plus grande avec un `blur` modéré pour un effet dramatique, « levé ».

---

## Mettre le tout ensemble – Un mini‑projet

Imaginez que vous construisez un générateur de rapports automatisé qui insère le logo de l’entreprise dans une zone de texte. Vous souhaitez que chaque logo possède une ombre subtile correspondant au style corporate. En utilisant la fonction `apply_shadow`, vous pouvez :

1. **Créer le document** (ou charger un modèle).
2. **Insérer la forme du logo** (via `DocumentBuilder.insert_image` ou `Shape`).
3. **Appeler `apply_shadow`** avec les spécifications d'ombre de votre marque.
4. **Exporter** en DOCX, PDF ou HTML avec une seule ligne de code.

Comme la fonction accepte des paramètres, vous pouvez stocker vos réglages d'ombre dans un fichier JSON et les appliquer à des dizaines de documents—sans aucune manipulation manuelle.

---

## Questions fréquentes & cas limites

| Question | Réponse |
|----------|--------|
| **Et si le document contient plusieurs formes ?** | L’exemple cible la *première* forme. Pour affecter toutes les formes, parcourez avec `doc.get_child_nodes(aw.NodeType.SHAPE, True)` et appliquez les mêmes paramètres `shadow_format` à chaque nœud. |
| **Puis‑je définir une couleur d'ombre différente ?** | Absolument. Utilisez `shape.shadow_format.color = aw.Color(255, 0, 0)` pour une ombre rouge, ou toute autre `aw.Color` de votre choix. |
| **Ces paramètres survivent‑ils à une conversion en PDF ?** | Oui. Aspose.Words conserve les propriétés d’ombre lors du rendu en PDF, bien que des valeurs de flou très élevées puissent être approximées. |
| **Y a‑t‑il un impact sur les performances pour de gros documents ?** | L’API d’ombre n’intervient que sur les objets forme, ainsi même un rapport de 500 pages se traite en millisecondes. Le goulot d’étranglement est généralement l’I/O, pas la configuration de l’ombre. |
| **Puis‑je supprimer l'ombre plus tard ?** | Réglez `shape.shadow_format.is_visible = False` ou réinitialisez simplement les propriétés à leurs valeurs par défaut. |

---

## Récapitulatif de l’exemple complet

Voici le script entier, dépouillé des commentaires pour un copier‑coller rapide :

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Exécutez le script, ouvrez `output.docx`, et vous verrez la forme affichant une ombre nette correspondant aux paramètres que vous avez définis.

---

## Conclusion

Nous avons couvert **

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants abordent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Implement Comments and Replies in Word Documents using Aspose.Words for Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [How to Manage Document Variables with Aspose.Words in Python: A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}