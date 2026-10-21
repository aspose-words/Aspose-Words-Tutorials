---
category: general
date: 2026-08-17
description: Insérez un exemple OleControlType.CommandButton dans Word en utilisant
  Aspose.Words. Apprenez comment ajouter des contrôles de formulaire à un document
  Word de manière programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: fr
lastmod: 2026-08-17
og_description: Insérez un exemple OleControlType.CommandButton dans Word avec Aspose.Words.
  Suivez ce guide pour ajouter des contrôles de formulaire à un document Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Insérer un exemple OleControlType.CommandButton dans Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Insérer un exemple OleControlType.CommandButton dans Word
url: /fr/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un exemple OleControlType.CommandButton dans Word

Si vous devez **insérer un exemple OleControlType.CommandButton** dans un fichier Word, ce guide vous montre comment faire. Vous apprendrez **comment ajouter des contrôles de formulaire à un document Word** en utilisant Aspose.Words, avec un programme C# complet et exécutable.

Les contrôles de formulaire tels que les boutons ActiveX vous permettent de créer des modèles Word interactifs — utiles pour les contrats, les questionnaires ou les outils internes. Les étapes ci‑dessous couvrent tout, de la configuration du projet à la vérification que le bouton apparaît correctement dans le fichier `.docx` enregistré.

## Prérequis

- .NET 6.0 SDK ou version ultérieure installé  
- Visual Studio 2022 (ou tout IDE C#)  
- Une licence Aspose.Words pour .NET ou une licence temporaire gratuite  
- Familiarité de base avec C# et les concepts de fichiers Word  

> **Astuce :** Si vous utilisez la version d’essai gratuite, placez le fichier de licence dans le même dossier que l’exécutable et chargez‑le au début de `Main`.

## Étape 1 : Créer un nouveau projet console et ajouter Aspose.Words

Ouvrez un terminal et exécutez :

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Cela crée un projet propre et récupère le dernier package Aspose.Words, qui fournit les API `Document`, `DocumentBuilder` et `InsertForms2OleControl` nécessaires pour le **exemple d’insertion OleControlType.CommandButton**.

## Étape 2 : Écrire le programme complet

Créez ou remplacez `Program.cs` avec le code suivant. Il contient toutes les directives `using` requises, le chargement de la licence, et le flux de travail en quatre étapes présenté dans l’extrait original.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Pourquoi chaque ligne est importante

* **License loading** – garantit que vous n’êtes pas limité par les restrictions d’évaluation.  
* **`Document doc = new Document();`** – crée le conteneur pour tout le contenu Word ; c’est la base de l’**exemple d’insertion OleControlType.CommandButton**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – fournit une API fluide pour ajouter du texte, des images et des contrôles.  
* **`InsertForms2OleControl`** – la méthode principale qui implémente **comment ajouter des contrôles de formulaire à un document Word**. La valeur d’énumération `OleControlType.CommandButton` indique à Aspose.Words de créer un bouton ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – positionne le bouton à 100 pts du bord gauche et du haut, avec une largeur de 80 pts et une hauteur de 30 pts. Ajustez ces valeurs pour correspondre à votre mise en page.  
* **`doc.Save`** – écrit le fichier .docx sur le disque ; le fichier contient maintenant le bouton intégré.

## Étape 3 : Compiler et exécuter le programme

Depuis le dossier du projet, exécutez :

```bash
dotnet run
```

Vous devriez voir le message de la console :

```
Document saved to ActiveXButton.docx
```

Ouvrez `ActiveXButton.docx` dans Microsoft Word. Vous verrez un bouton intitulé **ClickMe** positionné approximativement au centre de la page. Cliquer sur le bouton déclenche le comportement ActiveX par défaut (qui est généralement une opération nulle à moins d’y associer une macro).

![exemple insert olecontroltype.commandbutton](/images/activex-button.png "Bouton ActiveX CommandButton inséré dans un document Word")

*Texte alternatif de l’image :* exemple insert olecontroltype.commandbutton – un bouton ActiveX CommandButton affiché dans un document Word.

## Étape 4 : Personnaliser le bouton (optionnel)

L’**exemple d’insertion OleControlType.CommandButton** de base crée un bouton par défaut. Vous pouvez modifier son texte, sa police, ou même y attacher une macro en éditant l’objet OLE sous‑jacent. Voici une façon concise de changer le texte du bouton après insertion :

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Remarque :** La manipulation directe des propriétés OLE nécessite une compréhension de l’interface COM sous‑jacente. Dans la plupart des cas, le texte par défaut suffit.

## Étape 5 : Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Le bouton n’apparaît pas dans Word | Le document a été enregistré au format `.docx` mais ouvert dans un visualiseur qui supprime les contrôles OLE (par ex., Google Docs). | Ouvrez le fichier dans Microsoft Word ou Word Online avec les droits d’édition. |
| Erreur d’exécution `ArgumentOutOfRangeException` | Les coordonnées du `Rectangle` sont en dehors des marges de la page. | Utilisez des valeurs à l’intérieur de la taille de la page (par ex., 0‑500 pour A4). |
| Exception de licence | Une licence d’essai expire après 30 jours. | Chargez un fichier de licence valide ou demandez une version d’essai prolongée auprès d’Aspose. |

## Étape 6 : Comment cet exemple s’intègre dans des projets d’automatisation plus vastes

Lorsque vous devez **ajouter des contrôles de formulaire à un document Word** à grande échelle — par exemple générer des centaines de modèles de contrat — encapsulez la logique d’insertion dans une méthode réutilisable :

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Vous pouvez alors appeler `AddCommandButton` à l’intérieur de boucles qui traitent les lignes de données, en veillant à ce que chaque document généré contienne un bouton nommé de façon unique (par ex., `Approve_001`, `Approve_002`).

## Conclusion

Vous disposez maintenant d’un **exemple d’insertion OleControlType.CommandButton** complet qui montre **comment ajouter des contrôles de formulaire à un document Word** en utilisant Aspose.Words pour .NET. Le tutoriel a couvert la configuration du projet, le code source complet, des astuces de personnalisation et les étapes de dépannage courantes.

À partir d’ici, vous pourriez explorer :

- Ajouter d’autres types de contrôles tels que **CheckBox** ou **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Lier le bouton à une macro VBA pour une interactivité plus riche.  
- Générer des PDF à partir du même document tout en conservant les champs de formulaire.

Expérimentez avec différentes tailles, positions et noms de contrôles pour répondre à votre cas d’utilisation spécifique. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code fonctionnels complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insérer un champ de formulaire Combo Box dans un document Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insérer un champ de formulaire Check Box dans un document Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insérer un champ de formulaire de saisie de texte dans un document Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}