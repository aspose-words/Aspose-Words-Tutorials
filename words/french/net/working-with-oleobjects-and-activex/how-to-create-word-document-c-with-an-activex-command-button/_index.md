---
category: general
date: 2026-10-26
description: Apprenez à créer un document Word en C# et à ajouter un bouton ActiveX
  de façon programmatique. Ce guide étape par étape couvre l’insertion d’un bouton
  de commande, son masquage en mode conception et l’enregistrement du fichier.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: fr
lastmod: 2026-10-26
og_description: Créer un document Word en C# et ajouter un bouton ActiveX par programmation.
  Suivez ce tutoriel complet pour intégrer un bouton de commande qui n'apparaît qu'à
  l'exécution.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Créer un document Word en C# avec un bouton de commande ActiveX – guide
  complet
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Comment créer un document Word en C# avec un bouton de commande ActiveX
url: /fr/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word C# avec un bouton de commande ActiveX

Si vous devez **créer un document Word C#** contenant un bouton interactif, ce guide vous montre exactement comment faire. À la fin des deux premières phrases, vous connaîtrez l'approche globale, et les étapes suivantes vous guideront à travers chaque ligne de code que vous devez écrire.

Vous apprendrez comment ajouter un bouton ActiveX, le masquer pendant la conception, et le rendre visible uniquement lorsque l'utilisateur ouvre le fichier. Le tutoriel couvre également les pièges courants tels que les avertissements de sécurité et la compatibilité des versions, afin que vous puissiez livrer des documents fiables.

## Prérequis

* .NET 6.0 ou version ultérieure installé  
* Une copie sous licence de **Aspose.Words for .NET** (l'essai gratuit fonctionne pour l'expérimentation)  
* Une connaissance de base de C# et de Visual Studio (tout IDE supportant .NET convient)  

Aucun package NuGet supplémentaire n'est requis au-delà de `Aspose.Words`.

## Étape 1 : Créer un document Word C# et initialiser le DocumentBuilder

La première étape consiste à instancier un objet `Document` et un `DocumentBuilder`. Le `Document` représente le fichier .docx complet, tandis que le `DocumentBuilder` fournit des méthodes fluides pour ajouter du contenu.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Pourquoi c'est important :** Sans `DocumentBuilder`, vous devriez manipuler le DOM OpenXML manuellement, ce qui est sujet aux erreurs et plus difficile à lire. Le builder abstrait ces détails et garantit un fichier Word bien formé.

## Étape 2 : Comment ajouter un bouton ActiveX – insérer un contrôle CommandButton

Nous insérons maintenant un **contrôle ActiveX CommandButton** à un emplacement spécifique. Le rectangle définit la position du bouton (X, Y) et sa taille (largeur, hauteur) en points.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Pourquoi c'est important :** `InsertForms2OleControl` est la seule méthode d'Aspose.Words qui crée un véritable objet OLE ActiveX. La valeur d'énumération `Forms2OleControlType.CommandButton` indique à Word d'intégrer un bouton cliquable plutôt qu'un conteneur OLE générique.

## Étape 3 : Ajouter le bouton de commande programmatique – le masquer jusqu'à l'exécution

Word considère toute forme insérée comme visible par défaut. Pour garder le bouton invisible pendant la conception du modèle, définissez la propriété `Hidden` sur la forme que le builder vient de créer.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Pourquoi c'est important :** Définir `Hidden = true` empêche le bouton d'encombrer la vue de conception. Lorsque le document est ouvert dans Word, l'environnement d'exécution révèle automatiquement le contrôle, préservant l'expérience utilisateur prévue.

## Étape 4 : Enregistrer le fichier – créer un document Word avec bouton de commande

Enfin, écrivez le document sur le disque. Choisissez un chemin que votre application peut écrire, et utilisez l'extension `.docx` pour garantir une compatibilité moderne.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Pourquoi c'est important :** Enregistrer au format `.docx` garantit que le contrôle ActiveX intégré respecte la norme Office Open XML, prise en charge par Word 2007 et versions ultérieures. Si vous avez besoin du support legacy `.doc`, remplacez l'extension et utilisez `SaveFormat.Doc`.

## Exemple complet fonctionnel

En rassemblant tous les éléments, voici le programme complet que vous pouvez copier, coller et exécuter :

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Sortie attendue :** Après avoir exécuté le programme, ouvrez `C:\Temp\ActiveX.docx` dans Microsoft Word. Vous verrez un document vierge ; le bouton n'est pas visible en mode conception. Appuyez sur **Alt + F9** pour basculer les codes de champ, puis cliquez sur la zone du bouton — Word affichera le contrôle ActiveX, et vous pourrez interagir avec lui (par ex., double‑cliquer pour voir ses propriétés).

## Cas limites et conseils de bonnes pratiques

| Situation | Ce qu'il faut surveiller | Solution recommandée |
|-----------|--------------------------|----------------------|
| **L'utilisateur désactive ActiveX** | Word peut afficher un avertissement de sécurité ou bloquer le contrôle. | Demandez aux utilisateurs finaux d'activer les « contrôles ActiveX » dans le Centre de confiance, ou fournissez une alternative signée par macro. |
| **Document ouvert dans Word Online** | Word Online ne prend pas en charge ActiveX ; le bouton sera omis. | Utilisez un hyperlien de secours ou un contrôle de contenu si vous avez besoin de compatibilité cloud. |
| **Paramètres DPI différents** | La taille du rectangle peut apparaître plus grande ou plus petite sur des écrans à haute résolution DPI. | Utilisez `GraphicsUnit.Point` (la valeur par défaut) et testez sur les réglages DPI courants (96 dpi, 120 dpi). |
| **Boutons multiples** | L'appel `GetChildNodes(NodeType.Shape, true)[0]` ne récupère que la première forme. | Parcourez `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` et définissez `Hidden` pour chaque forme que vous ajoutez. |
| **Format .doc hérité** | Certaines propriétés ActiveX sont perdues lors de l'enregistrement au format `.doc`. | Privilégiez le `.docx` sauf si vous avez une exigence stricte de compatibilité héritée. |

**Astuce :** Après avoir inséré le bouton, vous pouvez assigner une macro à sa propriété `OnAction` via l'interface Word. Cela vous permet de définir un comportement de clic personnalisé sans écrire de code C# supplémentaire.

## Questions fréquentes

* **Cela fonctionne-t-il avec .NET Core ?**  
  Oui. Aspose.Words for .NET est entièrement compatible avec .NET 5, .NET 6 et les versions ultérieures. Il suffit de référencer le même package NuGet.

* **Puis-je changer la légende du bouton après la génération du document ?**  
  La légende définie dans `InsertForms2OleControl` devient le texte par défaut en mode conception. Les utilisateurs peuvent la modifier dans Word, mais vous pouvez également mettre à jour la légende programmatique en accédant aux propriétés de l'objet OLE via l'API `Shape.OleFormat`.

* **Et si j'ai besoin d'une taille différente pour le bouton ?**  
  Ajustez les valeurs de `RectangleF`. Les deux premiers paramètres sont les coordonnées X et Y ; les deux derniers sont la largeur et la hauteur en points (1 pt = 1/72 pouce).

## Conclusion

Vous savez maintenant comment **créer un document Word C#** et **ajouter programmatique un bouton de commande** en utilisant Aspose.Words. Le tutoriel a couvert l'initialisation du document, l'insertion d'un bouton ActiveX, son masquage jusqu'à l'exécution, et l'enregistrement du fichier final. Avec ces blocs de construction, vous pouvez intégrer des contrôles interactifs dans n'importe quel modèle Word que vous générez.

Ensuite, explorez les sujets connexes tels que la gestion des événements **how to add ActiveX button**, le style **create command button word** avec VBA, et **programmatically add command button** aux documents existants. Étendre ce modèle aux cases à cocher, aux listes déroulantes ou aux objets OLE personnalisés suit les mêmes étapes — il suffit de changer la valeur d'énumération `Forms2OleControlType`.

Commencez à expérimenter : remplacez la légende, ajustez la position, ou enchaînez plusieurs contrôles. Plus vous pratiquerez, plus vous deviendrez à l'aise pour fournir des documents Word riches et interactifs depuis C#. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment ajouter un bouton de commande programmatique dans un document Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Comment ajouter un bouton ActiveX dans un document Word avec Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Créer un document Word avec bouton ActiveX – Guide C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}