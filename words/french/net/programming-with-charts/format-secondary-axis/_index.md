---
title: Formater l'axe Y secondaire en devise dans un graphique Word avec Aspose.Words for .NET
weight: 710
limit:
description: Apprenez à ajouter et formater un axe Y secondaire en devise dans un graphique en courbes Word avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à ajouter et formater un axe Y secondaire en devise dans un
    graphique en courbes Word avec Aspose.Words for .NET.
  headline: Formater l'axe Y secondaire en devise dans un graphique Word avec Aspose.Words
    for .NET
  type: TechArticle
- description: Apprenez à ajouter et formater un axe Y secondaire en devise dans un
    graphique en courbes Word avec Aspose.Words for .NET.
  name: Formater l'axe Y secondaire en devise dans un graphique Word avec Aspose.Words
    for .NET
  steps:
  - name: Créez un nouveau document Word vide et un DocumentBuilder pour le modifier.
    text: Créez un nouveau document Word vide et un DocumentBuilder pour le modifier.
  - name: Insérez un graphique en courbes de taille 450×250 points dans le document
      et récupérez son objet Chart.
    text: Insérez un graphique en courbes de taille 450×250 points dans le document
      et récupérez son objet Chart.
  - name: Supprimez la série de remplacement par défaut qu’Aspose ajoute à un nouveau
      graphique.
    text: Supprimez la série de remplacement par défaut qu’Aspose ajoute à un nouveau
      graphique.
  - name: Définissez les libellés des trimestres et ajoutez une série de données principale
      avec des valeurs d'exemple au graphique.
    text: Définissez les libellés des trimestres et ajoutez une série de données principale
      avec des valeurs d'exemple au graphique.
  - name: Créez un groupe de séries secondaire de type Line et affectez-le au groupe
      d'axes secondaire.
    text: Créez un groupe de séries secondaire de type Line et affectez-le au groupe
      d'axes secondaire.
  - name: Masquez l'axe X secondaire afin que seul l'axe Y secondaire soit visible.
    text: Masquez l'axe X secondaire afin que seul l'axe Y secondaire soit visible.
  - name: Affichez le titre de l'axe Y secondaire et définissez son texte sur \"Sales
      (USD)\".
    text: Affichez le titre de l'axe Y secondaire et définissez son texte sur \"Sales
      (USD)\".
  - name: Définissez le format numérique de l'axe Y secondaire sur un modèle de devise
      avec deux décimales et dissociez-le du formatage source.
    text: Définissez le format numérique de l'axe Y secondaire sur un modèle de devise
      avec deux décimales et dissociez-le du formatage source.
  - name: Ajoutez une série auxiliaire au groupe secondaire, en fournissant des données
      qui seront tracées par rapport à l'axe Y secondaire.
    text: Ajoutez une série auxiliaire au groupe secondaire, en fournissant des données
      qui seront tracées par rapport à l'axe Y secondaire.
  - name: Enregistrez le document final dans un fichier nommé ProfitChart.docx dans
      le répertoire actuel.
    text: Enregistrez le document final dans un fichier nommé ProfitChart.docx dans
      le répertoire actuel.
  type: HowTo
- questions:
  - answer: Le graphique conservera la série de remplacement par défaut qu’Aspose.Words
      insère, de sorte que votre « Main Series » personnalisée apparaîtra aux côtés
      de points de données indésirables.
    question: Que se passe-t-il si j'omets l'appel `lineChart.Series.Clear()` ?
  - answer: Définissez `secondarySeriesGroup.AxisX.Hidden = false;` (ou omettez simplement
      la ligne qui le définit à `true`).
    question: Comment afficher l'axe X secondaire au lieu de le masquer ?
  - answer: Oui – changez la chaîne de format, par ex. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` pour les euros ou adaptez le modèle à votre locale.
    question: Puis-je utiliser un symbole monétaire ou un format différent pour l'axe
      Y secondaire ?
  - answer: Lorsque `IsLinkedToSource` est vrai, l'axe hérite du format numérique
      de la source de données sous‑jacente, ce qui écrase tout `FormatCode` personnalisé ;
      le définir à false oblige le graphique à utiliser le format que vous spécifiez.
    question: Pourquoi faut‑il définir `IsLinkedToSource = false` lors de l'application
      d'un format numérique personnalisé ?
  - answer: Oui, affectez `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (ou `Right` pour la valeur par défaut) pour contrôler le côté sur lequel l'axe
      est dessiné.
    question: Est‑il possible de déplacer l'axe Y secondaire du côté gauche du graphique ?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formater l'axe secondaire d'un graphique en devise
og_description: Apprenez à ajouter un axe Y secondaire à un graphique en courbes Word et à le styliser en devise avec deux décimales.
og_image_alt: Capture d'écran montrant un graphique en courbes Word avec un axe Y secondaire formaté en devise utilisant Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formater l'axe Y secondaire en devise dans un graphique Word avec Aspose.Words
Dans ce tutoriel, vous verrez comment créer un document Word, insérer un graphique en courbes, ajouter un axe Y secondaire, formater cet axe en devise avec deux décimales, et y lier une série de données secondaire en utilisant Aspose.Words for .NET. Formater l'axe secondaire en devise vous permet de présenter clairement les données financières aux côtés de la série principale. Suivez le code étape par étape pour voir le graphique rendu directement dans le document généré.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Que se passe-t-il si j'omets l'appel `lineChart.Series.Clear()` ?**  
A: Le graphique conservera la série de remplacement par défaut qu’Aspose.Words insère, de sorte que votre « Main Series » personnalisée apparaîtra aux côtés de points de données indésirables.

**Q: Comment afficher l'axe X secondaire au lieu de le masquer ?**  
A: Définissez `secondarySeriesGroup.AxisX.Hidden = false;` (ou omettez simplement la ligne qui le définit à `true`).

**Q: Puis-je utiliser un symbole monétaire ou un format différent pour l'axe Y secondaire ?**  
A: Oui – changez la chaîne de format, par ex. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` pour les euros ou adaptez le modèle à votre locale.

**Q: Pourquoi faut‑il définir `IsLinkedToSource = false` lors de l'application d'un format numérique personnalisé ?**  
A: Lorsque `IsLinkedToSource` est vrai, l'axe hérite du format numérique de la source de données sous‑jacente, ce qui écrase tout `FormatCode` personnalisé ; le définir à false oblige le graphique à utiliser le format que vous spécifiez.

**Q: Est‑il possible de déplacer l'axe Y secondaire du côté gauche du graphique ?**  
A: Oui, affectez `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (ou `Right` pour la valeur par défaut) pour contrôler le côté sur lequel l'axe est dessiné.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}