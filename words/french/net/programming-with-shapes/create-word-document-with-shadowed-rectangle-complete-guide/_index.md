---
category: general
date: 2026-04-21
description: Créer un document Word avec un rectangle stylisé et une ombre. Apprenez
  comment ajouter une ombre, insérer une forme de rectangle, définir la couleur de
  l'ombre, et bien plus encore en C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: fr
og_description: Créez un document Word et ajoutez une forme de rectangle ombrée en
  C#. Suivez ce guide pour définir facilement la couleur de l’ombre, le flou et les
  décalages.
og_title: Créer un document Word avec un rectangle ombré – Étape par étape
tags:
- Aspose.Words
- C#
- Document Automation
title: Créer un document Word avec un rectangle ombré – Guide complet
url: /fr/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec un rectangle ombré – Guide complet

Vous avez déjà eu besoin de **créer un document Word** qui ait un aspect un peu plus soigné qu’une simple page de texte ? Peut‑être que vous construisez un modèle de rapport ou un flyer et qu’un simple rectangle avec une ombre subtile ferait l’affaire. Dans ce tutoriel, nous allons passer en revue exactement cela — comment insérer une forme rectangle, activer l’ombre, et personnaliser sa couleur, son flou et ses décalages — le tout avec C# et Aspose.Words.

Nous couvrirons également **comment ajouter une ombre** d’une manière qui fonctionne que vous cibliez Word 2016, 2019 ou la dernière version d’Office 365. À la fin, vous disposerez d’un fichier *.docx* prêt à être enregistré montrant un rectangle joliment ombré, et vous comprendrez le « pourquoi » de chaque propriété que vous définissez.

## Prérequis

- .NET 6 (ou toute version récente du .NET Framework)  
- Aspose.Words pour .NET package NuGet (`Install-Package Aspose.Words`)  
- Familiarité de base avec la syntaxe C#  
- Un IDE tel que Visual Studio (mais tout éditeur convient)

Aucune bibliothèque supplémentaire n’est requise ; tout le reste vit à l’intérieur d’Aspose.Words.

## Étape 1 – Initialiser le Document et le Builder (Créer un document Word)

Pour **créer un document Word** de façon programmatique, vous commencez avec la classe `Document`. Le `DocumentBuilder` est votre pinceau ; il vous permet d’ajouter du texte, des formes et d’autres éléments.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Pourquoi c’est important :* L’objet `Document` représente l’ensemble du fichier .docx. Sans lui, vous n’avez nulle part où attacher le rectangle ou son ombre.

## Étape 2 – Insérer une forme rectangle (Insert Rectangle Shape)

Nous allons maintenant **insérer une forme rectangle**. La méthode `InsertShape` accepte une énumération `ShapeType`, ainsi que la largeur et la hauteur en points.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Astuce :* 1 point ≈ 1/72 pouce, donc 200 pts correspondent à environ 2,78 pouces de largeur. Ajustez ces valeurs pour convenir à votre mise en page.

## Étape 3 – Activer l’ombre (How to Add Shadow)

Les ombres sont désactivées par défaut. Basculez le drapeau `Visible` pour l’activer.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Que se passe‑t‑il ?* Lorsque `Visible` est vrai, Word rendra une ombre portée basée sur les autres propriétés que vous définirez ensuite.

## Étape 4 – Personnaliser l’apparence de l’ombre (Set Shadow Color, Blur, Offsets)

C’est ici que vous **définissez la couleur de l’ombre**, le rayon de flou, et les décalages X/Y. N’hésitez pas à expérimenter — différentes valeurs donnent un éclat doux, une ombre profonde, ou même un effet « flottant ».

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Pourquoi ces chiffres ?* Un flou de 5 pts donne un bord légèrement plumeux, tandis qu’un décalage de 4 pts déplace l’ombre vers le bas‑droite, imitant une source de lumière venant du haut‑gauche. Changez `Color` en `Color.Black` pour un contraste plus fort, ou utilisez `Color.FromArgb(128, 0, 0, 0)` pour un noir semi‑transparent.

### Cas limites et variations

- **Pas de flou :** définissez `Blur = 0` pour une ombre nette, à bord dur.  
- **Décalages négatifs :** utilisez `OffsetX = -4` pour pousser l’ombre vers la gauche.  
- **Formes différentes :** les mêmes propriétés d’ombre fonctionnent pour les cercles, triangles ou formes libres—il suffit de changer `ShapeType` à l’étape 2.  
- **Compatibilité :** Aspose.Words écrit les données d’ombre au format Office Open XML, qui fonctionne avec Word 2010‑2021 et Office 365.

## Étape 5 – Enregistrer le document (Create Word Document)

Enfin, persistez le fichier sur le disque. Vous pouvez choisir n’importe quel format supporté (`.docx`, `.pdf`, `.odt`, …) mais pour ce guide nous resterons sur le format Word classique.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Lorsque vous ouvrez **ShadowRectangle.docx** dans Microsoft Word, vous verrez un rectangle gris avec une ombre subtile et floue décalée vers le bas‑droite—exactement ce que nous avons scripté.

### Résultat attendu

- Un fichier *.docx* d’une seule page.  
- Un rectangle de 200 pt × 100 pt centré à l’endroit où le curseur était lors de l’appel à `InsertShape`.  
- Une ombre grise qui apparaît 4 pts à droite et 4 pts en bas, avec un flou de 5 pts.

Si la forme semble mal centrée, vous pouvez déplacer le curseur avec `builder.MoveTo` avant l’insertion, ou ajuster les propriétés `Left` et `Top` de la forme après insertion.

## Questions fréquentes & Dépannage

**Q : L’ombre n’apparaît pas dans Word.**  
A : Assurez‑vous que `ShadowFormat.Visible` est `true`. Vérifiez également que vous utilisez une version récente d’Aspose.Words (la fonctionnalité d’ombre a été ajoutée dans la version 20.3).

**Q : Puis‑je appliquer un dégradé à l’ombre ?**  
A : Pas directement via `ShadowFormat`. L’interface de Word supporte les ombres dégradées, mais le schéma Open XML (que suit Aspose.Words) n’expose que des ombres de couleur unie. Vous devriez modifier le XML sous‑jacent manuellement—un scénario plus avancé.

**Q : Et si j’ai besoin d’un rectangle transparent avec seulement une ombre ?**  
A : Définissez `rectangle.FillColor = Color.Transparent;` après l’insertion. L’ombre sera toujours rendue car elle est indépendante du remplissage.

## Astuces pro pour le code en production

- **Réutiliser le builder :** si vous ajoutez plusieurs formes, conservez la même instance de `DocumentBuilder`—créer une nouvelle pour chaque forme ajoute une surcharge inutile.  
- **Enregistrements en lot :** enregistrez une fois après toutes les modifications ; les I/O fréquents ralentissent la génération de gros documents.  
- **Gestion des erreurs :** encapsulez tout le bloc dans un `try / catch` et journalisez les exceptions `Aspose.Words` ; elles contiennent souvent des numéros de ligne utiles si le modèle de document est corrompu.

## Prochaines étapes (Sujets associés)

- **Comment ajouter une ombre** aux images ou zones de texte (utilisation similaire de `ShadowFormat`).  
- **Insérer une forme rectangle** dans une cellule de tableau pour un style de cellule personnalisé.  
- **Créer un rectangle dans Word** en utilisant le XML natif de Word (pour ceux qui préfèrent le Open XML brut).  
- **Définir la couleur de l’ombre** dynamiquement selon l’entrée utilisateur ou les couleurs du thème.

Expérimentez avec différentes couleurs, rayons de flou et décalages—peut‑être un éclat bleu doux pour un rapport d’entreprise, ou une ombre noire profonde pour un flyer dramatique. Les possibilités sont infinies, et les changements de code sont minimes.

---

### Récapitulatif rapide

- Nous **avons créé un document Word** à partir de zéro.  
- Nous **avons inséré une forme rectangle** et activé son ombre.  
- Nous **avons défini la couleur de l’ombre**, le flou et les décalages pour obtenir un rendu professionnel.  
- Nous avons enregistré le fichier, prêt à être distribué.

Vous avez maintenant une base solide pour ajouter du style visuel à tout projet d’automatisation Word. D’autres idées ? Laissez un commentaire, et continuons la conversation. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}