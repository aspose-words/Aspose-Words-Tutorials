---
category: general
date: 2026-08-23
description: Créer un bouton de soumission dans l’automatisation Word en C#. Apprenez
  à ajouter un bouton ActiveX, à définir le nom du bouton, la légende et le texte
  par programmation.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: fr
lastmod: 2026-08-23
og_description: Créer un bouton de soumission en automatisation Word avec C#. Ce guide
  montre comment ajouter un bouton ActiveX, définir son nom, sa légende et son texte
  à l'aide d'Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Créer un bouton de soumission dans l'automatisation Word en C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Comment créer un bouton de soumission dans l’automatisation Word en C#
url: /fr/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un bouton de soumission en C# pour l'automatisation Word

Si vous devez **créer un bouton de soumission** à l'intérieur d'un document Word en utilisant C#, ce guide vous accompagne tout au long du processus. Vous verrez comment ajouter un bouton ActiveX, attribuer un nom programmatique et définir la légende du bouton afin qu'il ressemble à un contrôle *Submit* standard.

L'automatisation des contrôles de formulaire dans Word peut remplacer le travail manuel de mise en page et garantir la cohérence sur des centaines de documents. Dans les étapes ci‑dessous, vous apprendrez également comment **définir le texte du bouton**, **définir le nom du bouton** et **définir la légende du bouton** — tous essentiels lorsque le bouton participe à un flux de travail piloté par des macros.

## Prérequis

* .NET 6.0 (ou version ultérieure) installé.  
* Une référence à **Aspose.Words for .NET** (la bibliothèque qui fournit `DocumentBuilder.InsertForms2OleControl`).  
* Une connaissance de base de C# et des contrôles de formulaire ActiveX de Word.

Vous pouvez installer Aspose.Words via NuGet :

```bash
dotnet add package Aspose.Words
```

> **Astuce :** Utilisez la dernière version stable d'Aspose.Words pour bénéficier des corrections de bugs et des nouvelles fonctionnalités liées aux contrôles ActiveX.

## Vue d'ensemble de la solution

Le tutoriel est organisé en trois étapes claires :

1. **Ajouter un bouton ActiveX** – utilisez la méthode `InsertForms2OleControl` pour placer un bouton de commande dans le document.  
2. **Définir le nom du bouton** – attribuez un identifiant programmatique unique avec la propriété `Name`.  
3. **Définir la légende du bouton** – définissez le texte visible sur le bouton via la propriété `Caption` (qui contrôle également le **set button text** que vous voyez dans l'interface).

À la fin du guide, vous disposerez d'une routine **create submit button** entièrement fonctionnelle que vous pourrez réutiliser dans n'importe quel projet d'automatisation Word.

## Étape 1 : Ajouter un bouton ActiveX au document

La première tâche consiste à **add activex button** au fichier Word. Aspose.Words expose l'énumération `Forms2OleControlType.CommandButton` à cet effet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Pourquoi cette étape est importante :**  
Les contrôles ActiveX sont les seuls éléments de formulaire Word capables d'exécuter des macros VBA ou d'interagir avec du code externe. Ajouter le contrôle crée un espace réservé que les étapes suivantes pourront configurer.

> **Cas particulier :** Si le document contient déjà un contrôle portant le même nom, Word renomme automatiquement le nouveau (par ex., `CommandButton1`). Définir explicitement le nom à l'étape suivante évite ces collisions.

## Étape 2 : Définir le nom du bouton

Un **set button name** fiable est crucial lorsque vous devez référencer le contrôle depuis VBA ou depuis d'autres parties de votre code C#. La propriété `Name` attribue au bouton un identifiant programmatique.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Pourquoi vous devez définir un nom :**  
Lorsque le document est ouvert, VBA peut récupérer le bouton via `ActiveDocument.InlineShapes("btnSubmit")`. Un nom significatif comme `btnSubmit` clarifie également l'intention lors de l'inspection du XML du document.

> **Astuce :** Gardez les noms courts, alphanumériques et commencez par une lettre pour rester compatible avec les règles de nommage VBA.

## Étape 3 : Définir la légende du bouton (texte visible)

Le texte que les utilisateurs voient sur le bouton est contrôlé par la propriété **set button caption**. Dans l'interface de Word, cela apparaît comme l'étiquette du bouton, qui est également le **set button text** que vous souhaitez afficher.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Pourquoi la légende est importante :**  
La légende est l'étiquette visible par l'utilisateur. La modifier ultérieurement n'affecte pas le nom du bouton, vous pouvez donc localiser l'interface sans casser le code qui dépend de `btnSubmit`.

> **Question fréquente :** *Puis-je définir à la fois Caption et Value ?*  
> Pour un `CommandButton`, `Caption` contrôle l'étiquette, tandis que `Value` n'est pas utilisé. Si vous avez besoin d'une valeur cachée, stockez‑la dans une propriété personnalisée du document.

## Exemple complet fonctionnel

En combinant les trois étapes, vous obtenez une routine complète que vous pouvez intégrer à n'importe quelle application console ou Windows :

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
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Résultat attendu

L'exécution du programme crée `SubmitButton.docx`. Lorsque vous ouvrez le fichier dans Microsoft Word :

* Un bouton **Submit** apparaît à l'emplacement spécifié.  
* Le nom du bouton est `btnSubmit` (vérifiez via *Développeur → Mode création → Propriétés*).  
* Cliquer sur le bouton en mode création affiche la légende *Submit*.

Vous disposez maintenant d'un bloc réutilisable pour toute solution Word basée sur des formulaires.

## Considérations supplémentaires

### Gestion des collisions de noms

Si vous exécutez la routine plusieurs fois sur le même document, Word peut renommer automatiquement les contrôles en double. Pour garantir l'unicité, vous pouvez préfixer d'un GUID :

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Localisation de la légende du bouton

Pour les documents multilingues, stockez les légendes dans un fichier de ressources et attribuez‑les à l'exécution :

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Réagir au clic du bouton

Le bouton lui‑même ne contient pas de logique de clic en C#. Vous associez généralement une macro VBA :

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Comme vous avez **set button name** à `btnSubmit`, le nom de la macro suit automatiquement la convention `<Name>_Click`.

## FAQ de dépannage

| Question | Réponse |
|----------|--------|
| **Pourquoi le bouton apparaît-il vide ?** | Assurez‑vous d'avoir défini la propriété `Caption` ; sans celle‑ci le bouton n'affiche aucun texte. |
| **Puis‑je utiliser un autre contrôle ActiveX ?** | Oui. Remplacez `Forms2OleControlType.CommandButton` par `CheckBox`, `OptionButton`, etc., mais les propriétés diffèrent. |
| **Cette solution est‑elle compatible avec .NET Core ?** | Aspose.Words for .NET prend en charge .NET 6+, donc le même code fonctionne sur .NET Core et .NET Framework. |
| **Et si le document possède déjà un bouton ?** | Utilisez un `Name` unique (par ex., ajoutez un GUID) pour éviter les conflits. |

## Conclusion

Vous savez maintenant comment **create submit button** programmétiquement dans un document Word en utilisant C#. En suivant les trois étapes — **add activex button**, **set button name** et **set button caption** — vous pouvez de façon fiable **set button text**, **set button name** et **set button caption** pour toute solution de formulaire automatisée.

À partir d'ici, vous pourriez explorer :

* Ajouter des macros VBA qui réagissent au clic du **submit button**.  
* Styliser le bouton avec des polices ou couleurs personnalisées via le XML sous‑jacent.  
* Générer plusieurs boutons dans une boucle pour des formulaires dynamiques.

N'hésitez pas à expérimenter différentes légendes, noms et positions pour adapter à votre flux de travail spécifique. Bonne automatisation !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d'API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un graphique en courbes dans Word avec Aspose.Words pour .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Créer un document Word avec en-tête et pied de page avec Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}