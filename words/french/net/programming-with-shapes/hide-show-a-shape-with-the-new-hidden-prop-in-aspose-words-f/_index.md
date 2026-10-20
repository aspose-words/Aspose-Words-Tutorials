---
category: general
date: 2026-10-20
description: Masquer/Afficher une forme avec la nouvelle propriété `Hidden` en utilisant
  Aspose.Words pour C#. Apprenez comment basculer la visibilité d’une forme, gérer
  les cas limites et enregistrer le résultat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: fr
lastmod: 2026-10-20
og_description: Masquez/Affichez une forme avec la nouvelle propriété `Hidden` en
  utilisant Aspose.Words pour C#. Maîtrisez le basculement de la visibilité des formes
  et évitez les pièges courants.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Masquer/Afficher une forme avec la nouvelle propriété `Hidden` dans Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Masquer/Afficher une forme avec la nouvelle propriété `Hidden` dans Aspose.Words
  pour C#
url: /fr/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Masquer/Afficher une forme avec la nouvelle propriété `Hidden` dans Aspose.Words pour C#

Si vous devez **Masquer/Afficher une forme avec la nouvelle propriété `Hidden`** dans un document Word, ce guide vous montre exactement comment le faire avec Aspose.Words pour .NET. Que vous génériez des rapports, créiez des modèles ou nettoyiez des documents importés, contrôler la visibilité des formes par programme vous évite les modifications manuelles.

Dans ce tutoriel, vous apprendrez comment charger un document, localiser une forme, basculer la propriété `Hidden` et enregistrer le fichier modifié. Les étapes couvrent également des variantes courantes telles que la gestion de plusieurs formes et le traitement des graphiques en ligne ou flottants.

## Prérequis

* .NET 6.0 (ou version ultérieure) installé – Aspose.Words prend en charge .NET Standard 2.0 et .NET Core.
* Une copie sous licence de **Aspose.Words for .NET** (l’essai gratuit fonctionne pour l’exploration).
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code.
* Un document Word (`input.docx`) contenant au moins une forme (par ex., une image, SmartArt ou une toile de dessin).

## Étape 1 : Charger le document Word

La première opération consiste à créer un objet `Document` qui représente le fichier .docx sur le disque.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Pourquoi cette étape est importante* : `Document` est le point d’entrée pour toutes les opérations Aspose.Words. Charger le fichier en mémoire vous donne un accès complet à son arbre de nœuds, y compris les formes.

## Étape 2 : Récupérer la forme cible

Pour basculer la visibilité, vous devez obtenir une référence au nœud de forme. L’exemple ci‑dessous récupère la première forme du document, mais vous pouvez adapter la logique pour localiser les formes par nom, type ou indice.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Pourquoi cette étape est importante* : `GetChild` avec `true` effectue une recherche approfondie, garantissant que vous trouvez les formes même lorsqu’elles sont imbriquées dans des tableaux ou des en‑têtes. Vérifier la valeur `null` évite une `NullReferenceException` lorsque le document ne contient aucune forme.

## Étape 3 : Masquer la forme avec la propriété `Hidden`

Aspose.Words a introduit la propriété `Hidden` pour contrôler si une forme est rendue ou imprimée. La définir sur `true` masque la forme ; la définir sur `false` rend la forme à nouveau visible.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Si vous devez **afficher** une forme précédemment masquée, attribuez simplement `false` :

```csharp
// Show the shape again
shape.Hidden = false;
```

*Pourquoi cette étape est importante* : La propriété `Hidden` fonctionne pour les formes flottantes et en ligne, et elle s’intègre au formatage natif « Hidden » de Word. Cette approche est plus fiable que la suppression de la forme car le nœud reste dans l’arbre du document, préservant la mise en page et les références.

## Étape 4 : Enregistrer le document modifié

Après avoir ajusté la visibilité, écrivez les modifications dans un nouveau fichier (ou écrasez l’original si vous le souhaitez).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Pourquoi cette étape est importante* : `Save` sérialise l’arbre de nœuds en mémoire dans un package .docx que Word peut ouvrir. Le drapeau masqué est conservé, de sorte qu’en ouvrant le fichier dans Microsoft Word, la forme s’affichera selon le paramètre `Hidden`.

## Exemple complet et exécutable

Assembler toutes les étapes vous fournit un programme autonome que vous pouvez copier, compiler et exécuter.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Sortie attendue** lorsque vous exécutez le programme :

```
Document saved. Shape hidden = True
```

L’ouverture de `ShapeHidden.docx` dans Microsoft Word affiche le document sans la forme ciblée. Si vous définissez `shape.Hidden = false;` avant l’enregistrement, la forme réapparaît.

## Gestion de plusieurs formes

L’exemple ci‑dessus fonctionne pour une seule forme. Les documents du monde réel contiennent souvent de nombreux graphiques. Utilisez une boucle pour masquer ou afficher toutes les formes qui répondent à une condition (par ex., un nom ou un type spécifique).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Astuce* : filtrer par `ShapeType` évite de masquer involontairement des éléments décoratifs tels que des zones de texte ou SmartArt.

## Cas limites et bonnes pratiques

| Situation | Recommandation |
|-----------|----------------------|
| **La forme est dans un en‑tête/pied de page** | Récupérez d’abord le nœud d’en‑tête/pied de page, puis appelez `GetChild(NodeType.Shape, …)` sur ce sous‑document. |
| **Le document ne contient aucune forme** | Vérifiez toujours la valeur `null` après `GetChild` ou vérifiez `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Vous devez conserver le drapeau masqué entre différentes versions de Word** | La propriété `Hidden` est stockée dans le XML de la forme sous la forme `<w:hidden/>`, qui est prise en charge par Word 2007 et versions ultérieures. |
| **Performance avec de gros documents** | Utilisez `doc.GetChildNodes(NodeType.Shape, true)` une fois et réutilisez la collection au lieu d’appeler `GetChild` à plusieurs reprises. |

## Astuce pro : Combiner `Hidden` avec `WrapType`

Lorsqu’une forme est masquée, Word réserve toujours l’espace qu’elle occuperait à moins que vous ne modifiiez également son comportement d’enveloppe. Définir `WrapType = WrapType.None` supprime la zone de l’espace réservé.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Cela garantit que la mise en page se contracte comme si la forme n’avait jamais existé, ce qui est utile pour générer des rapports propres.

## Conclusion

Vous savez maintenant comment **Masquer/Afficher une forme avec la nouvelle propriété `Hidden`** en utilisant Aspose.Words pour C#. La solution couvre le chargement d’un document, la localisation d’une forme, le basculement de la propriété `Hidden` et la persistance du changement. En suivant les conseils de bonnes pratiques — vérification du null, gestion de plusieurs formes et ajustement des paramètres d’enveloppe—vous pouvez contrôler de manière fiable la visibilité des formes dans n’importe quel scénario d’automatisation Word.

Prêt à explorer davantage ? Envisagez les étapes suivantes :

* **Masquer/Afficher plusieurs formes** en fonction de métadonnées personnalisées (utilise la technique « masquer la forme par programme »).
* **Combiner `Hidden` avec du contenu conditionnel** en utilisant les champs Aspose.Words pour la génération dynamique de rapports.
* **Explorer d’autres propriétés de nœud**, comme `Visible` pour les objets de graphique ou `IsDeleted` pour le contrôle au niveau du paragraphe.

Bon codage, et profitez du contrôle granulaire qu’Aspose.Words offre pour la visibilité des formes dans les documents Word !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [comment masquer une forme dans Word avec C# – guide étape par étape](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [Comment masquer une forme dans Word avec C# – guide étape par étape](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Créer un document Word vierge avec une forme ellipse masquée – guide complet C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}