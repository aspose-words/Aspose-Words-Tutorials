---
category: general
date: 2026-09-21
description: Créer un document Word de façon programmatique et apprendre comment enregistrer
  le bouton du document Word, insérer le bouton de commande Word, et définir la légende
  du bouton de commande à l'aide de DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: fr
lastmod: 2026-09-21
og_description: Créer un document Word de façon programmatique avec Aspose.Words.
  Découvrez comment enregistrer le bouton du document Word, insérer un bouton de commande
  Word, définir la légende du bouton de commande et utiliser DocumentBuilder pour
  des formulaires interactifs.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Créer un document Word par programmation et ajouter un bouton
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Créer un document Word par programmation et insérer un bouton
url: /fr/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word programmatique et insérer un bouton

Si vous devez **créer un document Word programmatique**, Aspose.Words fournit une API fluide qui vous permet d'ajouter des contrôles interactifs tels qu'un CommandButton. Ce tutoriel explique également **comment utiliser DocumentBuilder**, comment **enregistrer le bouton du document Word**, et comment **définir la légende du bouton de commande** afin que le bouton apparaisse exactement comme vous l'attendez dans le fichier .docx.

Vous apprendrez à :

* Initialiser un document vierge avec `Document`.
* Travailler avec `DocumentBuilder` pour modifier le document.
* Insérer un **CommandButton** (`insert command button word`).
* Définir le nom du bouton et sa légende visible (`set command button caption`).
* Persister le résultat sur le disque (`save word document button`).

Les étapes sont rédigées pour les développeurs .NET utilisant C# et la dernière version d'Aspose.Words pour .NET (v24.10). Aucun package NuGet supplémentaire n'est requis au-delà d'Aspose.Words.

---

## Ce dont vous avez besoin avant de commencer

| Pré‑requis | Raison |
|------------|--------|
| Visual Studio 2022 (ou tout IDE C#) | Pour compiler et exécuter le code d'exemple. |
| .NET 6.0 SDK or later | Fournit le runtime pour l'exemple. |
| Aspose.Words for .NET (v24.10 or newer) | La bibliothèque qui vous permet de **créer un document Word programmatique** et de manipuler les contrôles de formulaire. |
| Basic familiarity with C# and OOP concepts | Nécessaire pour comprendre le flux du code. |

Vous pouvez installer Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Créer un document Word programmatique

La première étape consiste à instancier un `Document` vide. Cet objet représente l'intégralité du fichier Word en mémoire.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Créer le document de manière programmatique vous offre une toile vierge sur laquelle vous pouvez ajouter des paragraphes, des tableaux ou des contrôles interactifs.  

---

## Comment utiliser DocumentBuilder

`DocumentBuilder` est la classe principale pour éditer un `Document`. Elle fournit des méthodes pour insérer du texte, des images et des champs de formulaire. Dans ce tutoriel, nous l'utilisons pour placer un CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le builder maintient un curseur interne qui pointe vers l'emplacement d'insertion actuel. Par défaut, il commence au début de la première section, ce qui est idéal pour notre exemple.

---

## Insérer un bouton de commande Word

Aspose.Words considère un CommandButton comme un contrôle ActiveX. La méthode `InsertForms2OleControl` crée un contrôle OLE générique que nous configurons ensuite comme un bouton.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

À ce stade, le contrôle existe dans le document mais n'a aucune représentation visuelle tant que nous ne définissons pas son type.

---

## Définir la légende du bouton de commande

Nous indiquons maintenant au contrôle OLE qu'il doit se comporter comme un CommandButton et lui attribuer une étiquette conviviale.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Définir la **légende du bouton de commande** est essentiel car Word affiche ce texte sur la surface du bouton. Si vous omettez `SetCaption`, le bouton apparaîtra avec une étiquette générique.

---

## Enregistrer le bouton du document Word

Enfin, persistez le document sur le disque. La méthode `Save` écrit l'ensemble du package Word, y compris le bouton nouvellement inséré, dans un fichier .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Le fichier `CommandButton.docx` contient désormais un bouton pleinement fonctionnel portant l'étiquette **Submit**. Lorsque l'utilisateur ouvre le fichier dans Microsoft Word et clique sur le bouton, l'action par défaut (que vous pourrez ensuite lier via VBA) sera déclenchée.

---

## Exemple complet fonctionnel

Ci-dessous le programme complet que vous pouvez copier, coller et exécuter. Il démontre l'ensemble du flux de travail, de la création du document à l'enregistrement du bouton.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Résultat attendu**

* Un fichier nommé `CommandButton.docx` situé au chemin que vous avez spécifié.
* L'ouverture du fichier dans Microsoft Word affiche un seul bouton **Submit** sur la première page.
* Le bouton peut être sélectionné, redimensionné ou lié à une macro depuis l'onglet **Developer** de Word.

---

## Questions fréquentes et gestion des cas limites

| Question | Réponse |
|----------|--------|
| *Et si j'ai besoin de plus d'un bouton ?* | Répétez les étapes 3–6 avec des noms et des légendes différents. Chaque bouton doit avoir une valeur `SetName` unique. |
| *Puis-je définir la taille du bouton ?* | Oui. Après avoir inséré le contrôle, vous pouvez modifier ses propriétés `Width` et `Height` via l'objet `OleFormat`. |
| *Le bouton fonctionnera-t-il sur toutes les versions de Word ?* | Les contrôles ActiveX sont pris en charge dans la version de bureau de Word (Windows). Ils ne sont pas rendus dans Word Online ou sur macOS. |
| *Comment ajouter un gestionnaire de clic ?* | Vous devez écrire du code VBA qui fait référence au nom du bouton (`btnSubmit`). La macro VBA peut être intégrée en utilisant `doc.VbaProject`. |
| *Et si je dois insérer le bouton dans une cellule de tableau ?* | Déplacez le curseur du builder vers la cellule souhaitée (`builder.MoveTo(cell.FirstParagraph)`) avant d'appeler `InsertForms2OleControl`. |

---

## Astuces professionnelles

* **Astuce pro :** Toujours définir un nom significatif avec `SetName`. Cela simplifie l'automatisation VBA et facilite le débogage.
* **Attention à :** Oublier d'appeler `SetControlType`. Sans cet appel, l'objet OLE apparaît comme un espace réservé générique plutôt qu'un bouton cliquable.
* **Astuce de performance :** Si vous générez de nombreux documents dans une boucle, réutilisez une seule instance de `DocumentBuilder` et appelez `builder.MoveToDocumentEnd()` avant chaque insertion afin d'éviter des réinitialisations de curseur inutiles.

---

## Prochaines étapes

Maintenant que vous savez comment **créer un document Word programmatique**, **insérer un bouton de commande Word**, **définir la légende du bouton de commande**, et **enregistrer le bouton du document Word**, vous pouvez explorer des scénarios plus avancés :

* Ajouter des contrôles **TextFormField** pour la saisie utilisateur.
* Combiner les boutons avec des champs **MacroButton** pour exécuter du VBA directement.
* Utiliser **DocumentBuilder.InsertImage** pour placer des icônes sur vos boutons.
* Intégrer avec ASP.NET pour générer des formulaires Word sur

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un nouveau document Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Créer un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}