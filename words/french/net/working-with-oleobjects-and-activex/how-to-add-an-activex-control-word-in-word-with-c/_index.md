---
category: general
date: 2026-09-30
description: Ajoutez un contrôle ActiveX à un document Word en C#. Apprenez à insérer
  un bouton ActiveX, à ajouter un bouton de commande et à le rendre cliquable.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: fr
lastmod: 2026-09-30
og_description: Ajoutez un contrôle ActiveX à un document Word avec C#. Suivez ce
  guide complet pour insérer un bouton ActiveX, ajouter un bouton de commande et le
  rendre cliquable.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Ajouter un contrôle ActiveX aux documents Word – guide C# étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Comment ajouter un contrôle ActiveX dans Word avec C#
url: /fr/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter un contrôle ActiveX dans Word avec C#

Si vous devez intégrer un **contrôle ActiveX** dans un fichier Microsoft Word, ce guide vous montre exactement comment le faire. Vous verrez un exemple complet et exécutable qui insère un bouton cliquable, enregistre le document et fonctionne avec la dernière version d’Aspose.Words pour .NET.

Ajouter un contrôle ActiveX vous permet de créer des formulaires interactifs, des boîtes de dialogue personnalisées ou des éléments d’interface simples qui se comportent comme des contrôles natifs de Word. Que vous construisiez un modèle de contrat nécessitant une interaction utilisateur ou un rapport qui a besoin d’un bouton « Exécuter », les étapes ci‑dessous couvrent tout ce dont vous avez besoin.

## Prérequis

* SDK .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.8)
* Visual Studio 2022 (ou tout IDE supportant C#)
* Aspose.Words pour .NET installé (`dotnet add package Aspose.Words`)
* Une compréhension de base de C# et de la structure des documents Word

> **Astuce :** La méthode `InsertForms2OleControl` ne fonctionne qu’avec les contrôles « Forms 2.0 » hérités, qui sont les contrôles ActiveX que Word utilise pour les champs de formulaire. Si vous ciblez des versions plus récentes d’Office, le contrôle s’affiche toujours correctement dans le client de bureau.

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez un nouveau projet console et ajoutez les instructions `using` requises. Cela garantit que le compilateur peut trouver les classes `Document`, `DocumentBuilder` et `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

L’espace de noms `Aspose.Words` fournit des API de haut niveau pour le traitement de Word, tandis que `Aspose.Words.Drawing` contient l’énumération `OleControlType` nécessaire pour spécifier le type de contrôle ActiveX.

## Étape 2 : Charger le document Word source

Vous devez commencer avec un fichier Word que vous souhaitez modifier. Le code suivant charge `input.docx` depuis le dossier que vous spécifiez.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Si le fichier n’existe pas, Aspose.Words lève une `FileNotFoundException`. Enveloppez l’appel dans un bloc `try/catch` si vous avez besoin d’une gestion d’erreur souple.

## Étape 3 : Créer un DocumentBuilder pour modifier le document

`DocumentBuilder` est le moteur pour insérer du texte, des images et des contrôles. Il maintient un curseur qui pointe vers l’emplacement où le prochain élément sera placé.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Par défaut, le curseur du builder est positionné au début de la première section. Vous pouvez le déplacer avec des méthodes comme `MoveToDocumentEnd()` ou `MoveToParagraph(index)` si vous souhaitez placer le bouton ailleurs.

## Étape 4 : Insérer un contrôle ActiveX CommandButton

Voici le cœur du tutoriel : insérer un **contrôle ActiveX** qui apparaît sous forme de bouton cliquable. La méthode `InsertForms2OleControl` prend deux arguments — le type de contrôle et une légende (ou un nom) pour le contrôle.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Pourquoi utiliser `OleControlType.CommandButton` ?**  
  Cela indique à Word de créer un bouton de commande classique Forms 2.0, qui affiche une légende et peut être relié à une macro ou à un script VBA ultérieurement.

* **À quoi sert la légende ?**  
  La chaîne `"ClickMe"` devient le texte visible du bouton. Vous pouvez la modifier selon vos besoins d’interface.

### Insérer le bouton à un emplacement spécifique

Si vous avez besoin du bouton après un paragraphe particulier, déplacez d’abord le builder :

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Étape 5 : Enregistrer le document modifié

Après avoir inséré le contrôle, persistez les modifications dans un nouveau fichier (ou écrasez l’original).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Lorsque vous ouvrez `output.docx` dans la version de bureau de Word, vous verrez le bouton intitulé **ClickMe** (ou **Submit**, selon la légende que vous avez utilisée). Cliquer sur le bouton en mode conception ne fait rien par défaut ; vous pouvez assigner une macro plus tard via l’onglet « Developer » de Word.

## Exemple complet et exécutable

Voici un programme autonome qui démontre l’ensemble du flux de travail. Copiez‑le dans `Program.cs` d’une nouvelle application console et exécutez‑le.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Résultat attendu

* La console affiche le message de succès avec le chemin du fichier de sortie.
* L’ouverture de `output.docx` montre un bouton **ClickMe** à l’endroit où le builder l’a inséré.
* Le bouton peut être sélectionné, redimensionné ou assigné à une macro via **Developer → Design Mode** de Word.

## Questions fréquentes et gestion des cas limites

| Question | Réponse |
|----------|--------|
| **Comment insérer un bouton ActiveX dans l’en‑tête/pied de page ?** | Déplacez le builder vers l’en‑tête/pied de page avec `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` avant d’appeler `InsertForms2OleControl`. |
| **Et si j’ai besoin d’une case à cocher au lieu d’un bouton ?** | Utilisez `OleControlType.CheckBox` et fournissez une légende comme `"Agree"`. |
| **Le bouton fonctionnera‑t‑il dans Word Online ?** | Non. Word Online ne prend pas en charge les contrôles ActiveX hérités Forms 2.0. Le bouton ne s’affiche que dans le client de bureau. |
| **Puis‑je définir la taille du bouton par programme ?** | Après insertion, récupérez l’objet `Shape` via `builder.CurrentParagraph.Runs[0].GetShape()` et ajustez `Width`/`Height`. |
| **Existe‑t‑il un moyen d’assigner une macro depuis le code ?** | Aspose.Words n’expose pas l’édition de macros. Vous devez ouvrir le document dans Word et y attacher une macro manuellement ou utiliser l’API Office Interop. |

## Conseils pour une utilisation en production

* **Évitez les chemins codés en dur** – utilisez `Path.Combine` et des fichiers de configuration.
* **Libérez `Document`** – encapsulez‑le dans une instruction `using` si vous travaillez avec de gros fichiers afin de libérer rapidement la mémoire.
* **Validez la sortie** – vérifiez programmétiquement que le document contient une forme de type `OleControl` en parcourant `doc.GetChildNodes(NodeType.Shape, true)`.
* **Note de sécurité** – Les contrôles ActiveX peuvent exécuter du code sur la machine cliente. Distribuez les documents uniquement à des utilisateurs de confiance et envisagez des signatures numériques.

## Conclusion

Vous savez maintenant comment ajouter un **contrôle ActiveX** à un document Word en utilisant C#. En chargeant un document, en créant un `DocumentBuilder`, en insérant un bouton de commande avec `InsertForms2OleControl` et en enregistrant le fichier, vous pouvez automatiser la création de formulaires Word interactifs. Expérimentez avec d’autres valeurs `OleControlType`, placez des contrôles dans les en‑têtes ou les tableaux, et combinez‑les avec des macros pour offrir des expériences utilisateur plus riches.

---

*Prochaines étapes* : explorez **comment insérer des contrôles ActiveX** d’autres types, apprenez **comment ajouter des gestionnaires d’événements de bouton de commande** via VBA, et lisez les meilleures pratiques pour **insérer un bouton ActiveX** afin d’assurer la compatibilité multiplateforme.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Intégration d’objets OLE et de contrôles ActiveX dans les documents Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Ajouter un champ de formulaire Combo Box à un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Ajouter un champ de formulaire Check Box à un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}