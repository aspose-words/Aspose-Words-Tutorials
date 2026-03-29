---
category: general
date: 2026-03-28
description: Comment définir une ombre sur une forme en C# avec Aspose.Words – ajouter
  une ombre à la forme, appliquer l'ombre et personnaliser l'apparence.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- apply shadow to shape
- how to add shadow
language: fr
og_description: Comment définir rapidement une ombre sur une forme en C#. Apprenez
  à ajouter une ombre à une forme, à l’appliquer et à ajuster le flou, la distance
  et l’angle.
og_title: Comment définir une ombre sur une forme en C# – Guide complet
tags:
- Aspose.Words
- C#
- Document Automation
- Graphics
title: Comment ajouter une ombre à une forme en C# – Guide étape par étape
url: /fr/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment appliquer une ombre à une forme en C# – Guide complet de programmation

Vous vous êtes déjà demandé **comment appliquer une ombre** à une forme lorsque vous créez des documents Word de façon programmatique ? Vous n'êtes pas le seul. Dans de nombreux rapports, présentations ou dépliants, une ombre portée subtile peut faire ressortir un graphique sans paraître de mauvais goût. La bonne nouvelle ? Avec Aspose.Words for .NET, vous pouvez ajouter une ombre à une forme en quelques lignes de code.

Dans ce tutoriel, nous parcourrons l’ensemble du processus : charger un DOCX, récupérer la première forme, puis **appliquer une ombre à la forme** — en incluant la couleur, le flou, la distance et l’angle. À la fin, vous disposerez d’un extrait prêt à l’emploi que vous pourrez insérer dans n’importe quel projet C#. Aucun bibliothèque supplémentaire, aucune magie cachée.

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (version 23.9 ou plus récente) – la bibliothèque qui rend la manipulation de Word indolore.  
- Un environnement de développement .NET (Visual Studio 2022, Rider ou la CLI).  
- Un fichier DOCX d’exemple contenant déjà au moins une forme (un rectangle, une image ou un SmartArt suffit).  

Si l’un de ces éléments vous manque, récupérez le package NuGet avec `Install-Package Aspose.Words` et créez un fichier Word simple avec une forme insérée manuellement — uniquement pour la démonstration.

## Étape 1 : Charger le document (préparer l’ajout d’ombre)

La première chose est d’ouvrir le fichier source. C’est ici que l’opération **add shadow to shape** commencera.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the DOCX that holds the shape you want to enhance
        Document doc = new Document("input.docx");
```

> **Pourquoi c’est important :** Charger le document vous fournit un objet `Document` qui possède tous les nœuds, y compris les formes. Sans cela, il n’y a rien à modifier.

## Étape 2 : Récupérer la forme cible (choisir la bonne)

Ensuite, nous localisons la forme que nous souhaitons styliser. Dans cet exemple, nous récupérons la première forme du premier paragraphe, mais vous pouvez adapter la requête à n’importe quelle collection de nœuds.

```csharp
        // Grab the first shape inside the first paragraph of the first section
        Shape targetShape = doc.FirstSection.Body.FirstParagraph
            .GetChildNodes(NodeType.Shape, true)[0] as Shape;

        if (targetShape == null)
        {
            Console.WriteLine("No shape found – check your input file.");
            return;
        }
```

> **Astuce :** `GetChildNodes(NodeType.Shape, true)` parcourt l’arbre de manière récursive, garantissant que vous ne manquiez pas les formes imbriquées comme le WordArt.

## Étape 3 : Accéder à l’objet de formatage d’ombre (là où la magie opère)

Chaque `Shape` expose une propriété `ShadowFormat`. Cet objet contrôle la visibilité, la couleur, le flou, la distance et l’angle—tous les paramètres dont vous avez besoin pour **apply shadow to shape**.

```csharp
        // The ShadowFormat object holds all shadow‑related settings
        ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Pourquoi nous utilisons `ShadowFormat` :** Il abstrait la représentation XML sous‑jacente, vous permettant d’ajuster les ombres sans manipuler le OpenXML brut.

## Étape 4 : Rendre l’ombre visible et choisir une couleur (ajouter une ombre à la forme)

Une ombre n’apparaîtra pas tant que vous n’avez pas défini `Visible` sur `true`. Ensuite, vous pouvez choisir n’importe quelle `System.Drawing.Color`. Ici nous utilisons un gris moyen, mais n’hésitez pas à expérimenter.

```csharp
        // Turn the shadow on and give it a subtle gray tone
        shadow.Visible = true;
        shadow.Color = Color.FromArgb(80, 80, 80);   // dark gray
```

> **Erreur courante :** Oublier d’activer `Visible` entraîne des échecs silencieux—votre forme reste inchangée même si vous avez défini d’autres propriétés.

## Étape 5 : Configurer l’apparence – flou, distance et angle (affiner le rendu)

Nous façonnons maintenant l’impact visuel. `BlurRadius` adoucit les bords, `Distance` éloigne l’ombre de la forme, et `Angle` détermine la direction de la source lumineuse.

```csharp
        // Adjust how the shadow looks
        shadow.BlurRadius = 5.0;   // in points – higher = softer
        shadow.Distance   = 3.0;   // how far the shadow is offset
        shadow.Angle      = 45.0;  // degrees clockwise from the horizontal
```

> **Cas particulier :** Si vous définissez une distance négative, l’ombre apparaîtra *à l’intérieur* de la forme, ce qui peut être utile pour des effets en relief.

## Étape 6 : Enregistrer le document mis à jour (voir le résultat)

Enfin, écrivez les modifications sur le disque. Vous pouvez écraser le fichier original ou en créer un nouveau.

```csharp
        // Persist the changes – you’ll see the shadow in Word or any viewer
        doc.Save("output-with-shadow.docx");
        Console.WriteLine("Shadow applied successfully! Check output-with-shadow.docx");
    }
}
```

L’exécution du programme produit `output-with-shadow.docx`. Ouvrez-le dans Microsoft Word, et vous remarquerez que la forme sélectionnée possède maintenant une ombre gris clair inclinée à 45°, floutée de 5 pts et décalée de 3 pts.

![Diagram showing shadow applied to a shape](https://example.com/images/shadow-diagram.png "Diagram showing shadow applied to a shape")

*Texte alternatif : Diagramme montrant l’ombre appliquée à une forme* – cette image illustre l’effet avant/après.

## Comment ajouter une ombre – variantes courantes et cas limites

Même si les étapes de base sont simples, les scénarios réels nécessitent souvent des ajustements. Voici quelques situations « et si » que vous pourriez rencontrer.

### 1. Plusieurs formes, différentes ombres

Si votre document contient plusieurs graphiques, parcourez la collection de formes et attribuez des paramètres d’ombre uniques à chaque forme.

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            ShadowFormat sf = shp.ShadowFormat;
            sf.Visible = true;
            sf.Color = Color.FromArgb(100, 100, 150); // bluish tint
            sf.BlurRadius = 3.0;
            sf.Distance = 2.0;
            sf.Angle = 30.0;
        }
```

### 2. Ombres transparentes

Aspose.Words vous permet de définir un canal alpha via `Color.FromArgb(alpha, r, g, b)`. Utilisez un alpha faible (par ex., 50) pour un effet subtil semi‑transparent.

```csharp
        shadow.Color = Color.FromArgb(50, 0, 0, 0); // 20% opacity black
```

### 3. Supprimer une ombre

Parfois, vous devez désactiver une ombre après l’avoir appliquée. Il suffit de définir `Visible` sur `false`.

```csharp
        shadow.Visible = false;
```

### 4. Problèmes de compatibilité

Les fonctionnalités d’ombre utilisées ici sont prises en charge dans Word 2007 + (format DOCX). Si vous ciblez le format binaire plus ancien `.doc`, l’ombre peut être ignorée car le format ne possède pas les éléments XML nécessaires. Dans ce cas, envisagez d’enregistrer au format DOCX ou d’utiliser un indicateur visuel de secours.

## Récapitulatif : Ce que nous avons accompli

- **Chargé** un DOCX avec Aspose.Words.  
- **Récupéré** la première forme du document.  
- **Accédé** à son objet `ShadowFormat`.  
- **Activé** l’ombre, défini une couleur, un rayon de flou, une distance et un angle.  
- **Enregistré** un nouveau fichier qui montre visiblement l’effet.  

Tous ces étapes ensemble répondent à **how to set shadow** sur une forme, tout en vous montrant comment **add shadow to shape**, **apply shadow to shape**, et même **how to add shadow** dans des scénarios plus complexes.

## Prochaines étapes et sujets associés

Maintenant que vous avez maîtrisé le style des ombres, vous pourriez vouloir explorer :

- **Remplissages en dégradé** pour les formes (`Shape.FillFormat.GradientFill`).  
- **Effets de texte** tels que la lueur ou le reflet (`TextEffect`).  
- **Insertion programmatique de nouvelles formes** (`doc.FirstSection.Body.AppendChild(new Shape(...))`).  
- **Exportation en PDF** tout en conservant les ombres (`doc.Save("output.pdf")`).  

Chacun de ces sujets s’appuie sur les mêmes principes du modèle d’objets que nous avons utilisés ici, vous vous sentirez donc à l’aise.

---

*Bon codage ! Si vous rencontrez un problème, laissez un commentaire ci‑dessous ou consultez la documentation de l’API Aspose.Words pour des informations plus approfondies.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}