---
category: general
date: 2026-09-21
description: Apprenez à créer un bouton de commande ActiveX dans un document Word
  avec Aspose.Words et C#. Ce guide étape par étape couvre l’insertion, le positionnement
  et l’enregistrement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: fr
lastmod: 2026-09-21
og_description: Créer un bouton de commande ActiveX dans un document Word en utilisant
  C# et Aspose.Words. Suivez ce tutoriel complet pour insérer, positionner et enregistrer
  le bouton de façon programmatique.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Créer un bouton de commande ActiveX dans Word avec C# – guide complet
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Comment créer un bouton de commande ActiveX dans Word avec C#
url: /fr/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un bouton de commande ActiveX dans Word avec C#

Si vous devez **créer un bouton de commande ActiveX** dans un fichier Word, ce guide vous montre les étapes exactes. En utilisant Aspose.Words for .NET, vous pouvez ajouter, positionner et configurer le bouton entièrement depuis du code C#.

L’insertion programmatique d’un bouton ActiveX élimine le travail manuel d’interface utilisateur et permet la génération automatisée de documents pour des formulaires, des rapports ou des modèles interactifs. Dans ce tutoriel, vous apprendrez à utiliser **DocumentBuilder**, la méthode **InsertForms2OleControl** et les propriétés associées pour obtenir un bouton pleinement fonctionnel.

## Ce dont vous avez besoin

Avant de commencer, assurez-vous d’avoir :

* .NET 6.0 SDK ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
* Aspose.Words for .NET (package NuGet `Aspose.Words`)
* Un IDE tel que Visual Studio 2022 ou VS Code
* Des connaissances de base en C# et en concepts de documents Word

Aucune installation supplémentaire d’Office n’est requise car Aspose.Words fonctionne indépendamment de Microsoft Word.

## Étape 1 : Configurer le projet C#

Créez un nouveau projet console et ajoutez le package Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

La bibliothèque `Aspose.Words` fournit la classe **DocumentBuilder** que nous utiliserons pour manipuler le document.

## Étape 2 : Initialiser le document et le builder

Le premier bloc de code crée un document vierge et une instance de `DocumentBuilder`. Cet objet est le point d’entrée pour toutes les opérations de traitement Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :** `DocumentBuilder` maintient la position actuelle du curseur, de sorte que toute insertion qui suit apparaîtra exactement à l’endroit où vous placez le curseur.

## Étape 3 : Insérer le bouton de commande ActiveX

La méthode **InsertForms2OleControl** crée un contrôle ActiveX du type demandé. Ici, nous demandons un `CommandButton` et spécifions sa taille en points (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Explication :**  
* `OleControlType.CommandButton` indique à Aspose.Words de créer un bouton plutôt qu’un autre type de contrôle.  
* La méthode renvoie un objet `Forms2OleControl`, qui expose les champs de positionnement et de propriétés.

## Étape 4 : Positionner le bouton et définir ses propriétés

Après l’insertion, vous pouvez déplacer le bouton à n’importe quel emplacement de la page et lui attribuer un nom programmatique ainsi qu’une légende visible.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Astuce :** Le système de coordonnées commence au coin supérieur gauche de la page. Ajustez `Left` et `Top` pour aligner le bouton avec les autres champs du formulaire.

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le fichier contiendra le bouton ActiveX, prêt à être ouvert dans Microsoft Word où le bouton devient interactif.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Lorsque vous ouvrez `ActiveXCommandButton.docx` dans Word, vous verrez un bouton libellé **Submit** à l’emplacement spécifié. Cliquer dessus dans Word déclenchera le comportement par défaut du bouton de commande (que vous pourrez personnaliser ultérieurement avec VBA ou des compléments Word).

## Exemple complet, exécutable

Assembler toutes les pièces donne un programme autonome que vous pouvez copier, coller et exécuter.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Résultat attendu :** La console affiche *« Document created successfully. »* et le dossier contient maintenant `ActiveXCommandButton.docx`. L’ouverture du fichier dans Microsoft Word montre un bouton **Submit** cliquable positionné à 100 pt du bord gauche et à 150 pt du haut de la page.

## Problèmes courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Le bouton apparaît hors de la page | Les valeurs `Left`/`Top` dépassent les dimensions de la page | Utilisez `doc.FirstSection.PageSetup.PageWidth` et `PageHeight` pour calculer des coordonnées sûres |
| Le bouton n’est pas visible dans Word | Le document a été enregistré dans un format qui supprime les contrôles ActiveX (par ex., `.txt`) | Enregistrez toujours en `.docx` ou `.doc` |
| Erreur d’exécution `ArgumentOutOfRangeException` | La largeur ou la hauteur est définie à zéro ou à une valeur négative | Assurez‑vous que les arguments de taille passés à `InsertForms2OleControl` sont des nombres positifs |

## Étendre la solution

Vous pouvez personnaliser davantage le bouton en définissant des propriétés supplémentaires telles que `Enabled`, `Visible`, ou en attachant une macro via VBA. La classe **Forms2OleControl** vous permet également d’insérer d’autres contrôles ActiveX comme des cases à cocher (`OleControlType.CheckBox`) ou des listes déroulantes (`OleControlType.ComboBox`).

Si vous devez générer plusieurs boutons dans une boucle, encapsulez la logique d’insertion dans une méthode d’assistance :

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Conclusion

Vous savez maintenant comment **créer un bouton de commande ActiveX** dans un document Word en utilisant C# et Aspose.Words. Le tutoriel a couvert la configuration du projet, l’insertion du bouton avec `InsertForms2OleControl`, son positionnement et l’enregistrement du fichier final. Avec cette base, vous pouvez automatiser des formulaires complexes, intégrer des contrôles interactifs et intégrer des documents Word dans des solutions .NET plus larges.

Ensuite, explorez des sujets connexes tels que les champs de formulaire **Aspose.Words ActiveX**, le **C# DocumentBuilder** avancé, ou l’ajout programmatique de **contrôles ActiveX dans Word** pour des cases à cocher et des listes déroulantes. Expérimentez avec différentes coordonnées et tailles pour répondre à vos exigences de mise en page spécifiques. Bon codage !

## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}