---
category: general
date: 2026-09-05
description: Apprenez à créer un groupe de formes dans un fichier docx, à insérer
  un bouton de commande ActiveX et à charger du Markdown dans un document Word avec
  un exemple complet en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: fr
lastmod: 2026-09-05
og_description: Créer un groupe de formes docx, insérer un bouton de commande ActiveX
  et charger du Markdown dans un document Word avec C#. Suivez ce tutoriel étape par
  étape.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Créer un groupe de formes docx et intégrer des contrôles ActiveX – guide
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Comment créer un groupe de formes docx et ajouter des contrôles interactifs
  en C#
url: /fr/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un groupe de formes docx et ajouter des contrôles interactifs en C#

Si vous devez **create group shape docx** des fichiers de manière programmatique, ce guide vous montre exactement comment procéder. Vous verrez également comment **insert ActiveX command button** des contrôles et **load Markdown into a Word document** sans perdre le format de soulignement. À la fin du tutoriel, vous disposerez d’un `.docx` pleinement fonctionnel combinant des graphiques vectoriels, des éléments d’interface utilisateur interactifs et du contenu basé sur le markdown.

Ce tutoriel suppose que vous disposez d’un environnement de développement C# de base et de la bibliothèque Aspose.Words pour .NET installée. Aucun outil externe n’est requis — tout s’exécute dans une application console ou de bureau .NET standard.

## Prérequis

- .NET 6.0 SDK ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
- Aspose.Words pour .NET (package NuGet `Aspose.Words`)
- Un certificat X.509 valide (`.pfx`) si vous souhaitez tester l’étape de signature
- Un fichier image (par ex., `logo.png`) et un fichier markdown (`sample.md`) placés dans un dossier connu

> **Astuce :** Conservez tous les fichiers d’entrée dans un seul dossier *resources* pour simplifier les chemins relatifs.

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez un nouveau projet console et ajoutez les directives `using` requises. Ce bloc montre également comment référencer les classes Aspose.Words que vous utiliserez plus tard.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Les instructions `using` vous donnent un accès direct à `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` et d’autres types utilisés tout au long du tutoriel.

## Étape 2 : **Create group shape docx** – ajouter une forme groupée avec des éléments enfants

Une *group shape* vous permet de traiter plusieurs objets de dessin comme une seule unité. Cela est utile pour déplacer ou redimensionner des graphiques liés ensemble.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Pourquoi une group shape ?**  
Le regroupement maintient le rectangle et l’ellipse alignés lorsque l’utilisateur les déplace dans Word. Il simplifie également les opérations ultérieures comme l’application d’une bordure commune ou le déplacement du graphique complet de façon programmatique.

## Étape 3 : Insérer un contrôle de contenu texte brut (espace réservé pour l’entrée utilisateur)

Les contrôles de contenu offrent aux utilisateurs finaux une zone structurée pour saisir du texte. Le texte d’espace réservé disparaît dès que l’utilisateur commence à taper.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

La propriété `PlaceholderName` correspond à l’indication que Word affiche en gris clair. Les utilisateurs peuvent la remplacer par leur propre texte, et le XML sous‑jacent reste bien formé.

## Étape 4 : **Insert ActiveX command button** – ajouter une interface utilisateur interactive au document

Les contrôles ActiveX sont toujours pris en charge dans les fichiers Word modernes et peuvent déclencher des macros ou une automatisation externe. Ci-dessous, nous ajoutons un *command button* et définissons son libellé.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Quand utiliser un bouton ActiveX ?**  
Si vous distribuez le document dans un environnement d’entreprise qui repose sur des macros VBA, un bouton ActiveX peut lancer une macro ou une application externe. Pour une interactivité purement basée sur HTML, envisagez d’utiliser des *contrôles de contenu* avec *Office.js* à la place.

## Étape 5 : Insérer une image cachée (par ex., un logo) pour le branding ou un accès ultérieur par script

Les formes cachées ne sont pas affichées dans le document imprimé mais restent dans le XML, vous permettant de les récupérer programmatique plus tard.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Étape 6 : **Load markdown into a Word document** tout en conservant le format de soulignement

Aspose.Words peut importer le Markdown directement. Activer `ImportUnderlineFormatting` garantit que les soulignements du markdown (`<u>` ou `__text__`) deviennent des styles de soulignement Word au lieu de texte brut.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Cas particulier :** Si le fichier markdown contient des tableaux, ils sont automatiquement convertis en tableaux Word. Si vous avez besoin d’un style de tableau personnalisé, appliquez un `DocumentBuilder` après l’insertion.

## Étape 7 : Signer le document avec XAdES‑EPES (étape de sécurité optionnelle)

Les signatures numériques garantissent l’intégrité du document. Le code suivant signe le fichier **create group shape docx** en utilisant un profil XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Note de sécurité :** Gardez le mot de passe du certificat hors du contrôle de version. Utilisez des variables d’environnement ou un coffre sécurisé en production.

## Exemple complet exécutable

En combinant toutes les étapes, on obtient un programme unique et autonome. Enregistrez le fichier sous le nom `Program.cs` et exécutez-le depuis la ligne de commande.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

L’exécution du programme génère `CompleteGroupShape.docx` contenant :

- Un rectangle + ellipse groupés (le cœur du **create group shape docx**)
- Un contrôle de contenu texte brut avec texte d’espace réservé
- Un **insert ActiveX command button** libellé « Click Me »
- Une image logo cachée
- Du contenu Markdown avec les soulignements conservés
- Une signature numérique XAdES‑EPES (si le certificat est fourni)

## Questions fréquentes et dépannage

| Question | Réponse |
|---|---|
| **Le bouton ActiveX fonctionnera-t-il sur Word macOS ?** | Word sur macOS ne prend pas en charge les contrôles ActiveX. Le bouton apparaîtra comme une image statique. Utilisez des contrôles de contenu avec Office.js pour une interactivité multiplateforme. |
| **Que se passe-t-il si le fichier markdown contient du CSS personnalisé ?** | Aspose.Words ignore le CSS ; seule la syntaxe markdown standard est traitée. Convertissez manuellement les éléments stylisés en CSS en styles Word après l’importation. |
| **Puis-je ajouter d’autres formes au même groupe plus tard ?** | Oui. Récupérez le `GroupShape` par son nom ou son index, puis appelez `AppendChild(newShape)`. N’oubliez pas de réenregistrer le document après les modifications. |
| **Comment changer l’algorithme de signature ?** | Définissez `signature.SignatureAlgorithm` avant d’appeler `Sign`. La valeur par défaut est SHA‑256, qui satisfait la plupart des exigences de conformité. |
| **L’image cachée est‑elle visible dans l’interface Word ?** | Non, mais elle peut être affichée en activant *Afficher le texte masqué* dans les options de Word. Cela est utile pour stocker des métadonnées sans encombrer la mise en page. |

## Prochaines étapes

Maintenant que vous pouvez **create group shape docx**, **insert ActiveX command button**, et **load markdown into a Word document**, vous pouvez explorer :

- **Intégrer des macros VBA** qui réagissent au clic du bouton ActiveX.
- **Appliquer des styles personnalisés** aux paragraphes générés à partir du markdown.
- **Générer des PDFs** à partir du même document en utilisant `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automatiser le traitement par lots** de plusieurs fichiers markdown en un seul rapport compilé.

Ces extensions vous permettent de créer des pipelines de documents entièrement automatisés combinant graphiques riches, contrôles interactifs et rédaction basée sur le markdown—le tout depuis C#.

---

*Bon codage ! Si vous avez trouvé ce tutoriel

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer une forme rectangle dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer du markdown à partir de Word – Guide complet C#](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}