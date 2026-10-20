---
category: general
date: 2026-06-02
description: Apprenez à utiliser les polices à poids variable en C# et à définir le
  poids de la police par programme tout en modifiant le code d’étirement de la police
  pour une typographie dynamique.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: fr
og_description: Utilisez une police à poids variable en C# pour définir le poids de
  la police de manière programmatique et modifier le code d’étirement de la police,
  permettant une typographie dynamique dans vos documents.
og_title: Utiliser une police à poids variable en C# – Guide complet
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Utiliser une police à poids variable en C# – Guide complet de programmation
url: /fr/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utiliser les polices à poids variable en C# – Guide complet de programmation

Vous avez déjà eu besoin d'**utiliser une police à poids variable** dans un projet .NET mais vous ne saviez pas comment faire en sorte que le poids et l'étirement répondent aux entrées de l'utilisateur ? Vous n'êtes pas seul. Dans de nombreux scénarios d'interface ou de reporting, vous voulez que le texte s'adapte—peut‑être un titre léger qui devient gras au survol, ou un paragraphe qui élargit sa largeur pour mettre en avant. La bonne nouvelle, c'est qu'avec Aspose.Words vous pouvez **définir le poids de la police par programme** et même **modifier le code d'étirement de la police** à la volée.

Dans ce tutoriel, nous parcourrons un exemple pratique qui montre exactement comment charger une police à poids variable, appliquer un poids personnalisé et ajuster le paramètre d'étirement—le tout avec du code C# clair que vous pouvez copier‑coller. À la fin, vous disposerez d’une application console exécutable qui produit un PDF illustrant l’effet.

---

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (v23.12 ou ultérieur). La bibliothèque inclut une prise en charge complète des polices à poids variable.
- Un dossier contenant au moins un fichier de police à poids variable, par ex., *RobotoFlex‑Variable.ttf*. Vous pouvez le télécharger depuis Google Fonts.
- SDK .NET 6 (ou toute version récente de .NET) et un IDE de votre choix.
- Connaissances de base en C#—rien de compliqué, juste quelques lignes de code.

C'est tout. Aucun package NuGet supplémentaire au-delà d'Aspose.Words, et aucun fichier de configuration obscur.

![Exemple d'utilisation d'une police à poids variable](https://example.com/variable-weight-sample.png "Démonstration de l'utilisation d'une police à poids variable")

*Texte alternatif : capture d'écran montrant l'utilisation d'une police à poids variable dans un document PDF généré.*

---

## Étape 1 : Configurer FontSettings et pointer vers votre dossier de polices  

Tout d'abord—Aspose.Words doit savoir où se trouvent vos polices à poids variable. Vous le faites en créant un objet `FontSettings` et en y attachant un `FolderFontSource`. Le drapeau `true` indique au moteur de rechercher également dans les sous‑dossiers, ce qui est pratique si vous regroupez plusieurs familles de polices.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Pourquoi c’est important :** Sans l’enregistrement du dossier, Aspose.Words revient aux polices système et ignorera les données de poids variable intégrées dans votre fichier de police personnalisé. Cette étape constitue la base de tout ce qui suit.

---

## Étape 2 : Attacher FontSettings au Document  

Nous créons maintenant un nouveau `Document` (ou chargeons un existant) et lui indiquons d’utiliser les `FontSettings` que nous venons de préparer. Cette liaison rend les données de poids variable disponibles pour chaque `Run` que nous ajouterons plus tard.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Si vous avez déjà un modèle—par exemple, un fichier Word avec des espaces réservés—vous pouvez remplacer `new Document()` par `new Document("Template.docx")`. Les mêmes `FontSettings` s’appliqueront.

---

## Étape 3 : Ajouter un Run de texte qui utilisera la police à poids variable  

Un **Run** est la plus petite unité de mise en forme de texte dans Aspose.Words. Nous en créerons un, l’insérerons dans un nouveau paragraphe, puis modifierons plus tard ses attributs de police.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

À ce stade, le texte sera rendu avec la police par défaut (généralement Times New Roman). La magie opère une fois que nous assignons la famille à poids variable.

---

## Étape 4 : Choisir la famille de police à poids variable  

Voici où nous **utilisons réellement une police à poids variable**. Définissez `Font.Name` sur le nom exact de la famille tel qu’il est défini dans le fichier de police variable. Pour Roboto Flex, le nom est `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Si vous n’êtes pas sûr du nom de la famille, ouvrez le fichier `.ttf` dans un visualiseur de polices ou utilisez la méthode `fontSettings.GetFonts()` pour énumérer les familles disponibles.

---

## Étape 5 : Définir le poids et l'étirement de la police par programme  

Passons maintenant au cœur du tutoriel : nous **définissons le poids de la police par programme** et **modifions le code d'étirement de la police**. Les deux propriétés acceptent des valeurs entières qui correspondent à la spécification OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight** : 100 (Thin) → 900 (Black). Choisissez n’importe quelle valeur prise en charge par la police variable.
- **FontStretch** : 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). La valeur par défaut est 100 (Normal).

> **Astuce :** Toutes les polices variables n’exposent pas toute la gamme. Si vous définissez une valeur non prise en charge, le moteur la limitera à la valeur de poids ou d’étirement la plus proche disponible.

---

## Étape 6 : Enregistrer le document et vérifier le résultat  

Enfin, écrivez le document en PDF (ou DOCX) et ouvrez‑le pour voir l’effet. Le PDF est un excellent format pour la vérification visuelle car le rendu est cohérent sur toutes les plateformes.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Lorsque vous ouvrez *VariableWeightDemo.pdf*, vous devriez voir la phrase « Variable‑weight text demo » rendue dans une version légère et légèrement étendue de Roboto Flex. Changez `FontWeight` à `700` et `FontStretch` à `80` puis relancez—observez le texte devenir gras et plus condensé.

---

## Questions fréquentes & cas particuliers  

### Que faire si la police n'apparaît pas du tout ?

- **Missing FontSettings** : Vérifiez que `doc.FontSettings = fontSettings;` est exécuté **avant** l’ajout de tout texte.
- **Incorrect family name** : Utilisez `fontSettings.GetFonts()` pour lister toutes les familles découvertes ; copiez la chaîne exacte.
- **Unsupported weight/stretch** : Certaines polices variables ne prennent en charge qu’une sous‑plage de la gamme 100‑900. Utilisez `run.Font.FontWeight = 400;` comme solution de secours sûre.

### Puis‑je modifier le poids après l'enregistrement du document ?

Oui. L’objet `Run` est mutable, vous pouvez donc ajuster `FontWeight` ou `FontStretch` à tout moment avant le `Save` final. Si vous devez basculer les poids dynamiquement (par ex., selon l’interaction de l’utilisateur), envisagez de générer des runs séparés pour chaque état.

### Cela fonctionne‑t‑il avec la sortie DOCX ?

Absolument. Les métadonnées de poids variable sont stockées dans l’OpenXML sous‑jacent, et les versions récentes de Word peuvent les interpréter. Cependant, les versions plus anciennes de Word peuvent ignorer le paramètre d’étirement.

---

## Exemple complet fonctionnel  

Voici un programme console complet que vous pouvez compiler et exécuter immédiatement. Il comprend toutes les directives `using` nécessaires, la gestion des erreurs et des commentaires.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Sortie attendue :** La console affiche le chemin de sauvegarde, et le PDF généré montre le texte dans un style léger et étendu—exactement ce que nous avons configuré.

---

## Récapitulatif  

Nous avons vu comment **utiliser une police à poids variable** en C# avec Aspose.Words, démontré comment **définir le poids de la police par programme**, et montré le **code de changement d'étirement de la police** nécessaire pour élargir ou condenser les glyphes. Les étapes sont simples : configurer `FontSettings`, les attacher à un `Document`, créer un `Run`, choisir la famille à poids variable, puis ajuster `FontWeight` et `FontStretch`.

---

## Et après ?

- **Intégration UI dynamique** : Branchez la même logique dans une application WinForms ou WPF pour permettre aux utilisateurs de choisir le poids/étirement via des curseurs.
- **Runs multiples** : Combinez plusieurs runs avec des poids différents dans le même paragraphe pour des hiérarchies typographiques riches.
- **Axes avancés** : Certaines polices variables exposent des axes supplémentaires (ex. inclinaison, taille optique). Utilisez `run.Font.FontStyle` ou explorez `FontVariationSettings` pour un contrôle encore plus fin.
- **Conseils de performance** : Mettez en cache l’instance `FontSettings` lors du traitement de nombreux documents afin d’éviter des analyses de dossiers répétées.

N’hésitez pas à expérimenter—remplacez *Roboto Flex* par *Inter Variable* ou toute autre police OpenType variable, et observez vos documents gagner en flexibilité visuelle. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Utiliser la police depuis la machine cible](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Utiliser la police depuis la machine cible](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Utiliser la police depuis la machine cible](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}