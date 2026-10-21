---
category: general
date: 2026-09-11
description: Apprenez à créer des forms2olecontrol en code à l'aide d'Aspose.Words
  DocumentBuilder. Ce guide étape par étape couvre l'insertion d'un bouton de commande
  ActiveX, l'utilisation de setOleClassName et le dimensionnement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: fr
lastmod: 2026-09-11
og_description: Créez forms2olecontrol dans le code avec Aspose.Words. Suivez ce guide
  pour insérer un bouton de commande ActiveX, définir son nom de classe et ajuster
  sa taille.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Créer forms2olecontrol dans le code – guide complet d'Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Comment créer forms2olecontrol en code avec Aspose.Words
url: /fr/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer forms2olecontrol en code avec Aspose.Words

Si vous devez **créer forms2olecontrol en code**, ce guide vous montre exactement comment le faire en utilisant l'API Aspose.Words .NET. Que vous automatisiez un modèle nécessitant un bouton de commande ActiveX ou que vous souhaitiez simplement enrichir un document Word de façon programmatique, les étapes ci‑dessous couvrent tout, de l’insertion du contrôle à la configuration de son apparence.

Dans ce tutoriel, vous apprendrez à utiliser le **Aspose.Words DocumentBuilder** pour insérer un **ActiveX command button**, définir sa classe avec la **méthode setOleClassName**, et ajuster sa **taille Forms2OleControl**. Aucun outil externe n’est requis — seulement un environnement de développement .NET et la bibliothèque Aspose.Words.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 ou version ultérieure installé (le code fonctionne également avec .NET Framework 4.7+)
* Une version récente du package NuGet Aspose.Words for .NET
* Une connaissance de base du C# et du concept de contrôles ActiveX dans les documents Word

Si l’un de ces éléments manque, installez le package NuGet avec :

```bash
dotnet add package Aspose.Words
```

## Ce que couvre ce tutoriel

* Création d’une instance `DocumentBuilder`
* Insertion d’un `Forms2OleControl` (l’objet sous‑jacent d’un bouton de commande ActiveX)
* Attribution du nom de classe correct avec `setOleClassName`
* Définition de la largeur et de la hauteur visuelles à l’aide des propriétés **Forms2OleControl size**
* Enregistrement du document et vérification du résultat

À la fin du guide, vous disposerez d’un fichier Word pleinement fonctionnel contenant un bouton cliquable que vous pourrez personnaliser davantage ou lier à des macros VBA.

---

## Comment créer forms2olecontrol en code – étape par étape

### Étape 1 : Initialiser le DocumentBuilder

La classe `DocumentBuilder` est le point d’entrée pour la plupart des tâches de génération de documents dans Aspose.Words. Elle vous fournit des méthodes pour ajouter du texte, des images, des tableaux et, surtout pour ce tutoriel, des contrôles OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :**  
`DocumentBuilder` maintient la position du curseur actuel dans le document. En le créant dès le départ, vous vous assurez que toute insertion ultérieure—comme le **ActiveX command button**—apparaît exactement à l’endroit souhaité.

### Étape 2 : Insérer le Forms2OleControl

La méthode `insertForms2OleControl` renvoie un objet `Forms2OleControl`. Cet objet représente l’espace réservé du contrôle OLE que Word affichera sous forme de bouton ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Pourquoi c’est important :**  
Sans cet appel, vous ne pouvez pas manipuler les propriétés du contrôle. Le `Forms2OleControl` retourné vous donne un accès complet à la **méthode setOleClassName**, aux attributs de taille et aux autres paramètres spécifiques à OLE.

### Étape 3 : Spécifier la classe ActiveX avec setOleClassName

Word doit savoir quel type de contrôle ActiveX rendre. Le nom de classe pour un bouton de commande standard est `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Pourquoi c’est important :**  
La méthode `setOleClassName` fait le lien entre l’espace réservé OLE générique et le **ActiveX command button** concret. Utiliser un mauvais nom de classe entraîne un objet vide ou une erreur d’exécution à l’ouverture du document.

### Étape 4 : Ajuster la taille du Forms2OleControl

Un bouton trop petit ou trop grand paraît non professionnel. Vous pouvez contrôler ses dimensions avec `setWidth` et `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Pourquoi c’est important :**  
Ces propriétés constituent la **taille Forms2OleControl**. Elles influencent l’apparence du bouton dans l’interface Word et garantissent que toute macro associée dispose d’une zone cliquable suffisante.

### Étape 5 : Enregistrer le document et tester

Après avoir configuré le contrôle, enregistrez le document à l’emplacement de votre choix.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Ouvrez `ActiveXButton.docx` dans Microsoft Word. Vous devriez voir un bouton libellé « CommandButton1 » (la légende par défaut). Cliquer dessus ne fera rien tant que vous n’ajoutez pas de macro VBA, mais le contrôle lui‑même est pleinement fonctionnel.

**Résultat attendu :**  

![Document Word avec un bouton ActiveX command inséré](/images/activeX-button.png "Capture d’écran d’un document Word affichant un nouveau bouton ActiveX command inséré via le code")

*Le texte alternatif de l’image contient le mot‑clé principal pour l’accessibilité et le SEO.*

---

## Comprendre la classe ActiveX Forms2OleControl

La classe `Forms2OleControl` encapsule l’infrastructure OLE de bas niveau que Word utilise pour les éléments ActiveX. Elle hérite de `Shape`, ce qui signifie que vous pouvez également appliquer le formatage typique des formes (bordures, rotation, etc.) si besoin.

* **ActiveX command button** – Le cas d’usage le plus courant ; vous pouvez le lier à une macro via les outils développeur de Word.
* **méthode setOleClassName** – Détermine quelle classe COM Word charge ; d’autres valeurs valides incluent `"Forms.TextBox.1"` et `"Forms.ComboBox.1"`.
* **taille Forms2OleControl** – Contrôlée via `SetWidth`/`SetHeight`. Ces méthodes acceptent des points (1 pt = 1/72 in).

### Quand utiliser Forms2OleControl vs. Content Controls

Si vous avez seulement besoin d’une saisie de données simple (par ex., un champ texte), les contrôles de contenu natifs de Word sont plus légers. Utilisez `Forms2OleControl` lorsque vous avez besoin de la pleine fonctionnalité ActiveX, comme la gestion d’événements ou l’interaction VBA personnalisée.

---

## Définir des propriétés supplémentaires (facultatif)

Bien que les étapes de base suffisent à **créer forms2olecontrol en code**, vous souhaitez souvent affiner l’apparence ou le comportement du bouton.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Pourquoi c’est important :**  
`SetOleData` vous permet d’écrire des valeurs de propriétés arbitraires directement dans le flux OLE. C’est la façon la plus flexible de personnaliser un **ActiveX command button** sans recourir à VBA.

---

## Problèmes courants et dépannage

| Symptom | Likely cause | Fix |
|--------|--------------|-----|
| Le bouton apparaît sous forme de boîte grise | Nom de classe incorrect passé à `setOleClassName` | Vérifiez que la chaîne est exactement `"Forms.CommandButton.1"` (sensible à la casse) |
| La taille ne change pas | Largeur/Hauteur définie avant l’insertion du contrôle | Appelez toujours `SetWidth`/`SetHeight` **après** `InsertForms2OleControl` |
| Le document génère « OLE object not found » à l’ouverture | Licence Aspose.Words manquante (la version d’évaluation peut limiter OLE) | Appliquez une licence valide ou utilisez l’essai gratuit avec prise en charge complète d’OLE |
| La légende du bouton reste « CommandButton1 » | `SetOleData` non utilisé ou macro ne lit pas la propriété | Utilisez une macro VBA pour lire la propriété `"Caption"` ou définissez la légende via l’interface Word |

---

## Exemple complet, exécutable

Voici une application console complète que vous pouvez copier, coller et exécuter. Elle démontre tout ce qui a été couvert dans ce tutoriel.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Explication de chaque section**

* **Using directives** – Importation de l’espace de noms Aspose.Words requis pour `Document`, `DocumentBuilder` et `Forms2OleControl`.
* **Création du document** – Instancie un fichier Word vide.
* **InsertForms2OleControl** – Place le contrôle OLE à la position actuelle du curseur du builder.
* **SetOleClassName** – Indique à Word que le contrôle est un **ActiveX command button**.
* **SetWidth / SetHeight** – Ajuste la **taille Forms2OleControl** pour un rendu professionnel.
* **SetOleData (facultatif)** – Montre comment écrire des propriétés supplémentaires comme une légende.
* **Save** – Enregistre le fichier final `.docx` sur le disque.

Exécutez le programme (`dotnet run`) et ouvrez `ActiveXButton.docx`. Vous verrez un bouton que vous pourrez ensuite lier à une macro.

---

## Conclusion

Vous savez maintenant comment **créer forms2olecontrol en code** avec Aspose.Words, depuis l’initialisation du `DocumentBuilder` jusqu’à la configuration du **ActiveX command button** avec `setOleClassName` et le contrôle de sa **taille Forms2OleControl**. Cette approche vous permet d’automatiser des documents Word complexes, d’intégrer des éléments d’interface interactifs et de garder toute la logique dans votre code.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Créer une forme groupée dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer une forme rectangle dans Word avec Aspose.Words – Guide pas à pas](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}