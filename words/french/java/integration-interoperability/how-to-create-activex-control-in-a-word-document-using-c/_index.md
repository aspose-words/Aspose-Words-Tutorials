---
category: general
date: 2026-08-20
description: Apprenez à créer un contrôle ActiveX, à définir la taille du bouton et
  à ajouter le bouton à Word avec un exemple complet en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: fr
lastmod: 2026-08-20
og_description: Créer un contrôle ActiveX dans un fichier Word avec C#. Ce tutoriel
  montre comment définir la taille du bouton, ajouter le bouton à Word et créer un
  bouton cliquable.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Créer un contrôle ActiveX dans Word – guide C# étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Comment créer un contrôle ActiveX dans un document Word en C#
url: /fr/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un contrôle ActiveX dans un document Word avec C#

Si vous devez **create ActiveX control** à l'intérieur d'un fichier Microsoft Word, ce guide vous montre exactement comment le faire. Vous verrez comment **add button to Word**, définir les dimensions du bouton et rendre le contrôle cliquable — le tout avec un petit programme C# autonome.

Dans ce tutoriel vous allez :

* Comprendre pourquoi un contrôle ActiveX est utile pour les documents Word interactifs.  
* Apprendre le code exact nécessaire pour **set button size** et attribuer une légende.  
* Voir comment **create clickable button** qui peut ensuite être relié à une macro ou à une logique externe.  

Les étapes fonctionnent avec Aspose.Words .NET 23.12 ou version ultérieure et nécessitent uniquement un environnement de développement .NET.

> **Prerequisite** – Vous avez une licence valide Aspose.Words (ou vous utilisez la version d'évaluation) et Visual Studio 2022 ou tout IDE C#.

---

## Comment créer un contrôle ActiveX dans un document Word

La première étape consiste à instancier un `Document` vierge et un `DocumentBuilder`. Le builder fournit l'API de haut niveau pour insérer des objets tels que les contrôles ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

La méthode `InsertActiveXButton` (définie ci‑après) contient la logique pour **how to insert button** et la configurer.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

L'exécution du programme crée **ActiveXButton.docx**. L'ouverture du fichier dans Word affiche un bouton intitulé **Submit**. Le contrôle est pleinement fonctionnel — le cliquer déclenchera l'événement standard `CommandButton_Click`, que vous pourrez ensuite lier à une macro VBA.

### Pourquoi cela fonctionne

* `InsertForms2OleControl` indique à Word d'intégrer un objet OLE de type **CommandButton**, qui est la classe de bouton ActiveX classique.  
* Les arguments de largeur et de hauteur définissent directement **set button size** ; Word traduit les valeurs depuis les points (1 pt ≈ 1/72 in).  
* Nommer le contrôle (`Name = "btnSubmit"`) facilite son localisation depuis VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Définir la taille et la légende du bouton

Si vous avez besoin d'une apparence différente, ajustez les arguments numériques dans l'appel `InsertForms2OleControl`. La signature de la méthode est :

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – L'identifiant programmatique de la classe ActiveX (`"CommandButton"` pour un bouton standard).  
* **width / height** – Taille en points. Pour un bouton de 2 cm de large, utilisez `width = 56.7` (2 cm ≈ 56.7 pt).  

Vous pouvez également modifier la légende après l'insertion :

```csharp
commandButton.Caption = "Send Request";
```

Modifier la légende n'affecte pas la taille, mais influence le retour visuel pour l'utilisateur.

### Astuce

Si vous souhaitez un bouton carré, définissez les deux dimensions à la même valeur :

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Ajouter un bouton à Word et le rendre cliquable

Le code ci‑dessus **add button to Word** déjà. Pour que le bouton exécute une action, vous devez écrire une macro VBA qui gère l'événement `Click`. Voici une macro minimale que vous pouvez coller dans l'éditeur VBA de Word (`Alt+F11` → Insert → Module) :

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Comme le contrôle porte le nom `btnSubmit`, Word associe automatiquement l'événement `Click` à `btnSubmit_Click`. C'est la méthode standard pour **create clickable button** sans bibliothèques externes.

> **Note :** Les paramètres de sécurité des macros dans Word peuvent bloquer les contrôles ActiveX. Assurez‑vous que « Enable all macros » ou « Enable VBA macros » est sélectionné pour le document, ou signez numériquement la macro pour une utilisation en production.

---

## Questions fréquentes : comment insérer un bouton et dépannage

### 1. Que faire si le bouton n'apparaît pas après l'enregistrement ?

* Vérifiez que la version d'Aspose.Words prend en charge `InsertForms2OleControl`. Les versions antérieures à 22.5 ne disposent pas de cette fonctionnalité.  
* Assurez‑vous que le format de fichier cible est `.docx` ou `.doc`. Les formats plus anciens comme `.rtf` ne peuvent pas stocker d'objets ActiveX.  

### 2. Puis‑je insérer le bouton à un signet spécifique ?

Oui. Déplacez le builder vers le signet avant d'appeler `InsertForms2OleControl` :

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Comment **set button size** dynamiquement en fonction de la longueur du texte ?

Calculez la largeur requise en utilisant la méthode `Graphics.MeasureString` (de `System.Drawing`) et convertissez les pixels en points (`points = pixels * 72 / DPI`). Ensuite, transmettez la largeur calculée à `InsertForms2OleControl`.

### 4. Existe‑t‑il un moyen d'ajouter plusieurs boutons dans une boucle ?

Absolument. Encapsulez la logique d'insertion dans une boucle `for` et ajustez les propriétés `Left` et `Top` à chaque itération :

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Résultat attendu

Lorsque vous exécutez le programme et ouvrez **ActiveXButton.docx** :

* Un seul bouton **Submit** apparaît près du coin supérieur gauche de la première page.  
* La taille du bouton correspond aux dimensions que vous avez fournies (`100 pt × 30 pt`).  
* Si vous avez ajouté la macro VBA, cliquer sur le bouton affiche une boîte de dialogue : « You clicked the Submit button! ».

Vous avez maintenant créé avec succès **create ActiveX control**, **set button size**, et **add button to Word** tout en apprenant **how to insert button** et **create clickable button** pour de futures tâches d'automatisation.

---

## Conclusion

Dans ce tutoriel, vous avez appris comment **create ActiveX control** dans un document Word avec C#. En suivant les étapes, vous pouvez **set button size**, donner au contrôle un nom significatif, et **add button to Word** afin qu'il devienne un **clickable button** lié à une macro VBA.

À partir d'ici, vous pourriez explorer :

* Lier le bouton à un add‑in COM .NET au lieu de VBA.  
* Utiliser d'autres classes ActiveX telles que `CheckBox` ou `ComboBox`.  
* Automatiser la création de formulaires complets avec plusieurs contrôles.

N'hésitez pas à expérimenter avec différentes tailles

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}