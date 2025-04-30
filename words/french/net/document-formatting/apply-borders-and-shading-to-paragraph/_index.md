---
"description": "Appliquez des bordures et des trames de fond aux paragraphes de vos documents Word avec Aspose.Words pour .NET. Suivez notre guide étape par étape pour améliorer la mise en forme de vos documents."
"linktitle": "Appliquer des bordures et un ombrage à un paragraphe dans un document Word"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Appliquer des bordures et un ombrage à un paragraphe dans un document Word"
"url": "/fr/net/document-formatting/apply-borders-and-shading-to-paragraph/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Appliquer des bordures et un ombrage à un paragraphe dans un document Word

## Introduction

Salut ! Vous êtes-vous déjà demandé comment sublimer vos documents Word avec des bordures et des ombres originales ? Vous êtes au bon endroit ! Aujourd'hui, nous plongeons dans l'univers d'Aspose.Words pour .NET pour dynamiser vos paragraphes. Imaginez un document aussi élégant qu'un designer professionnel, avec seulement quelques lignes de code. Prêt à commencer ? C'est parti !

## Prérequis

Avant de retrousser nos manches et de nous lancer dans le codage, assurons-nous d'avoir tout ce dont nous avons besoin. Voici une liste de contrôle rapide :

- Aspose.Words pour .NET : cette bibliothèque doit être installée. Vous pouvez la télécharger depuis le [Site Web d'Aspose](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre IDE prenant en charge .NET.
- Connaissances de base de C# : juste assez pour comprendre et peaufiner les extraits de code.
- Une licence valide : soit une [permis temporaire](https://purchase.aspose.com/temporary-license/) ou un acheté chez [Aspose](https://purchase.aspose.com/buy).

## Importer des espaces de noms

Avant de nous lancer dans le code, nous devons nous assurer que les espaces de noms nécessaires sont importés dans notre projet. Cela nous permettra d'accéder à toutes les fonctionnalités intéressantes d'Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

Décomposons maintenant le processus en petites étapes. Chaque étape aura un titre et une explication détaillée. Prêt ? C'est parti !

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, nous avons besoin d'un emplacement pour enregistrer notre document parfaitement formaté. Définissons le chemin d'accès à votre répertoire de documents.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ce répertoire est l'endroit où votre document final sera enregistré. Remplacer `"YOUR DOCUMENT DIRECTORY"` avec le chemin réel sur votre machine.

## Étape 2 : Créer un nouveau document et DocumentBuilder

Ensuite, nous devons créer un nouveau document et un `DocumentBuilder` objet. Le `DocumentBuilder` est notre baguette magique qui nous permet de manipuler le document.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le `Document` l'objet représente l'intégralité de notre document Word, et le `DocumentBuilder` nous aide à ajouter et à formater du contenu.

## Étape 3 : Définir les bordures des paragraphes

Ajoutons maintenant des bordures élégantes à notre paragraphe. Nous allons définir la distance par rapport au texte et définir différents styles de bordure.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

Ici, nous définissons une distance de 20 points entre le texte et les bordures. Les bordures de tous les côtés (gauche, droite, haut, bas) sont doublées. Élégant, non ?

## Étape 4 : Appliquer l'ombrage au paragraphe

Les bordures sont un atout, mais passons à la vitesse supérieure avec un peu d'ombrage. Nous utiliserons un motif croisé en diagonale avec un mélange de couleurs pour faire ressortir notre paragraphe.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

Dans cette étape, nous avons appliqué une texture croisée diagonale avec du corail clair en arrière-plan et du saumon clair en premier plan. C'est comme habiller votre paragraphe de vêtements de créateurs !

## Étape 5 : ajouter du texte au paragraphe

Qu'est-ce qu'un paragraphe sans texte ? Ajoutons une phrase d'exemple pour voir notre mise en forme en action.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

Cette ligne insère notre texte dans le document. Simple, il est désormais encadré avec élégance et doté d'un arrière-plan ombré.

## Étape 6 : Enregistrer le document

Enfin, il est temps de sauvegarder notre travail. Enregistrons le document dans le répertoire spécifié, sous un nom explicite.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

Cela enregistre notre document avec le nom `DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` dans le répertoire que nous avons spécifié précédemment.

## Conclusion

Et voilà ! En quelques lignes de code, nous avons transformé un simple paragraphe en un contenu visuellement attrayant. Aspose.Words pour .NET simplifie considérablement la mise en forme professionnelle de vos documents. Que vous prépariez un rapport, une lettre ou tout autre document, ces astuces vous aideront à faire bonne impression. Alors, n'hésitez plus, essayez et voyez vos documents prendre vie !

## FAQ

### Puis-je utiliser différents styles de ligne pour chaque bordure ?  
Absolument ! Aspose.Words pour .NET vous permet de personnaliser chaque bordure individuellement. Il vous suffit de définir `LineStyle` pour chaque type de bordure comme indiqué dans le guide.

### Quelles autres textures d'ombrage sont disponibles ?  
Plusieurs textures sont disponibles, comme l'uni, les rayures horizontales, les rayures verticales, etc. Consultez la section [Documentation Aspose](https://reference.aspose.com/words/net/) pour une liste complète.

### Comment puis-je changer la couleur de la bordure ?  
Vous pouvez définir la couleur de la bordure à l'aide du `Color` propriété pour chaque bordure. Par exemple, `borders[BorderType.Left].Color = Color.Red;`.

### Est-il possible d'appliquer des bordures et des ombrages à une partie spécifique du texte ?  
Oui, vous pouvez appliquer des bordures et des ombrages à des passages de texte spécifiques à l'aide de l' `Run` objet dans le `DocumentBuilder`.

### Puis-je automatiser ce processus pour plusieurs paragraphes ?  
Absolument ! Vous pouvez parcourir vos paragraphes et appliquer les mêmes bordures et paramètres d'ombrage par programmation.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}