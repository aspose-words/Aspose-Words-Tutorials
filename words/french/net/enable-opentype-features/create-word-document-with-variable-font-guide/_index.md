---
category: general
date: 2026-03-19
description: Créer un document Word avec Aspose.Words et une police variable. Apprenez
  à modifier le poids de la police, à définir la largeur de la police et à spécifier
  la variation de la police en C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: fr
og_description: Créer un document Word avec une police variable en utilisant Aspose.Words.
  Ce tutoriel vous montre comment charger la police, modifier le poids de la police,
  définir la largeur de la police et spécifier la variation de la police.
og_title: Créer un document Word avec une police variable – Guide complet
tags:
- Aspose.Words
- C#
- Variable Font
title: Créer un document Word avec une police variable – Guide
url: /fr/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec une police variable – Guide

Vous avez déjà eu besoin de **créer un document Word** utilisant une police variable moderne, mais vous ne saviez pas par où commencer ? Vous n'êtes pas seul. Dans de nombreux projets—pensez aux rapports dynamiques ou aux brochures cohérentes avec la marque—pouvoir **modifier le poids de la police** à la volée est un véritable atout.  

Dans ce tutoriel, nous parcourrons l’ensemble du processus : du chargement d’une police variable dans Aspose.Words, à la définition de son poids et de sa largeur, jusqu’à l’enregistrement d’un DOCX qui ressemble exactement à votre conception. Pas de références vagues, seulement du code concret que vous pouvez intégrer immédiatement dans votre projet C#.

## Ce que vous allez apprendre

- Comment **charger des fichiers de police variable** dans Aspose.Words à l’aide de `FontSettings`.
- La syntaxe pour **définir les axes de variation de police** tels que `wght` (poids) et `wdth` (largeur).
- Comment **définir la largeur de la police** et **modifier le poids de la police** sur un seul `Run`.
- Conseils pour dépanner les problèmes courants (glyphes manquants, chemins de dossiers incorrects, etc.).
- Un exemple complet et exécutable que vous pouvez copier‑coller et tester immédiatement.

> **Prérequis** : .NET 6+ (ou .NET Framework 4.6+), Aspose.Words pour .NET installé via NuGet, et un fichier de police variable comme *RobotoFlex.ttf* placé dans un dossier local *Fonts*.

## Étape 1 – Charger la police variable dans Aspose.Words

Tout d'abord, nous devons indiquer à Aspose.Words où chercher nos polices personnalisées. La classe `FontSettings` effectue le travail lourd.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Pourquoi c’est important** : Sans enregistrer le dossier, Aspose.Words revient aux polices système et ignorera toute donnée de variation OpenType que vous essayez d’appliquer plus tard. En le pointant vers un répertoire spécifique, vous garantissez que *RobotoFlex* (ou toute autre police variable) est trouvé à chaque exécution du code.

> **Astuce pro** : Définissez le deuxième paramètre de `SetFontsFolder` sur `true` si vous souhaitez qu’Aspose recherche également les sous‑dossiers. Cela aide lorsque vous organisez les polices par style ou poids.

## Étape 2 – Créer un nouveau document et ajouter du texte d’exemple

Maintenant que le moteur de polices sait où chercher, nous créons un `Document` vierge et insérons un paragraphe contenant un `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Ce qui se passe** : `Run` représente une portion contiguë de texte avec un formatage uniforme. En le créant d’abord, nous isolons la logique de formatage—parfait pour appliquer ultérieurement différents axes de variation à des runs séparés si besoin.

## Étape 3 – Définir les axes de variation souhaités (Poids & Largeur)

Les polices variables exposent des *axes* que vous pouvez ajuster à l’exécution. Les deux plus courants sont `wght` (poids de la police) et `wdth` (largeur de la police). Aspose.Words modélise cela avec la collection `OpenTypeFontVariation`.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Pourquoi ces valeurs** : Selon la spécification OpenType, `wght` varie du poids minimum au poids maximum de la police (souvent 100–900). Une valeur de **700** correspond à un aspect gras. `wdth` fonctionne de façon similaire ; **100** représente la largeur par défaut (normale), tandis que des valeurs inférieures à 100 condensent les glyphes.

> **Cas particulier** : Certaines polices variables ne supportent pas un axe donné. Si vous fournissez une balise non prise en charge, Aspose l’ignorera silencieusement. Vérifiez toujours la spécification de la police (généralement trouvée dans les métadonnées du fichier `.ttf` ou `.otf`).

## Étape 4 – Appliquer la variation au Run en utilisant le nom de la police

Nous associons maintenant les données de variation au texte réel. La classe `FontInfo` contient le nom de la famille de police et la collection d’axes.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explication** : En définissant `FontInfo`, nous contournons la propriété habituelle `Font.Name` et fournissons au moteur une configuration de police entièrement qualifiée. C’est la seule façon d’indiquer à Aspose.Words d’utiliser une police variable avec des axes personnalisés.

> **Erreur fréquente** : Oublier de faire correspondre exactement le nom de famille présent dans le fichier de police (`RobotoFlex` dans cet exemple). Une faute de frappe fera revenir Aspose à une police par défaut, et votre variation sera perdue.

## Étape 5 – Enregistrer le document et vérifier le résultat

Enfin, écrivez le document sur le disque. Le DOCX généré contiendra les instructions de police variable, que Microsoft Word (2016+) peut rendre correctement.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Ouvrez le fichier résultant dans Word, sélectionnez le texte et consultez la boîte de dialogue **Police**. Vous devriez voir *Roboto Flex* répertorié, et le texte apparaîtra plus gras que le contenu environnant—exactement ce que notre réglage `wght = 700` demandait.

> **Astuce de vérification** : Si le texte semble inchangé, revérifiez que le fichier de police supporte réellement l’axe `wght`. Certaines polices « variables » n’exposent que `ital` (italique) ou `opsz` (taille optique).

## Optionnel : Ajouter plus de variation – Modifier la largeur dynamiquement

Si vous souhaitez *définir la largeur de la police* différemment pour un autre paragraphe, répétez simplement les étapes 3‑4 avec une nouvelle collection `OpenTypeFontVariation`.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Vous avez maintenant deux runs—l’un gras, l’autre légèrement plus large—démontrant à la fois **modifier le poids de la police** et **définir la largeur de la police** dans le même document.

## Exemple complet fonctionnel

Copiez le fragment ci‑dessous dans une nouvelle application console (`Program.cs`) et exécutez‑le. Assurez‑vous que le dossier `Fonts` contient `RobotoFlex.ttf` (ou toute police variable de votre choix).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Résultat attendu** : Un fichier `VariableFont.docx` où la phrase « Variable‑weight text » apparaît en gras, grâce à l’axe `wght = 700`, tout en conservant la largeur par défaut.

## Questions fréquentes & cas particuliers

| Question | Réponse |
|----------|--------|
| *Et si la police n’est pas trouvée ?* | Vérifiez le chemin du dossier, assurez‑vous que le nom du fichier correspond, et que le processus dispose des permissions de lecture. Vous pouvez également appeler `fontSettings.GetFonts()` pour lister les polices détectées. |
| *Puis‑je combiner plusieurs runs avec des variations différentes ?* | Absolument. Chaque `Run` peut contenir son propre `FontInfo`. Répétez simplement les étapes 3‑4 pour chaque run. |
| *Les versions plus anciennes de Word prennent‑elles en charge les polices variables ?* | Word 2016 (Build 16.0.8001) a introduit un support de base. Si vous ciblez des versions antérieures, le document reviendra à l’instance statique la plus proche de la police. |
| *Y a‑t‑il une limite au nombre d’axes que je peux définir ?* | Vous pouvez définir autant d’axes que la police le permet. Les balises courantes sont `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Fournir une balise non prise en charge n’a simplement aucun effet. |
| *Comment déboguer les glyphes manquants ?* | Utilisez `FontSettings.GetFontSources()` pour inspecter les polices chargées, et `FontInfo.HasGlyph(char)` pour tester des caractères individuels. |

## Conclusion

En quelques étapes, nous avons montré **comment créer des fichiers Word** qui exploitent la puissance des polices variables, vous permettant de **modifier le poids de la police**, **définir la largeur de la police**, **charger des fichiers de police variable**, et **définir les axes de variation de police**—tout cela avec Aspose.Words pour .NET.  

L’idée principale est simple : enregistrer le dossier de polices, décrire les axes souhaités, les attacher à un `Run`, puis enregistrer. À partir de là, vous pouvez étendre la technique à des sections entières, des tableaux, ou même générer de façon programmatique des rapports spécifiques à une marque.

**Prochaines étapes** : essayez de remplacer `RobotoFlex` par une autre police variable, expérimentez avec l’axe `ital` (italique), ou générez une version PDF du même document en utilisant Aspose.PDF. Le même schéma s’applique—charger, définir, appliquer, enregistrer.

Bon codage, et profitez de la flexibilité que les polices variables apportent à vos projets d’automatisation Word !  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}