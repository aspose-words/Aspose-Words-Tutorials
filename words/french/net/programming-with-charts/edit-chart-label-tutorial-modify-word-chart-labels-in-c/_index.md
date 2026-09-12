---
category: general
date: 2026-09-11
description: Tutoriel de modification des libellés de graphique montrant comment changer
  la position du libellé, personnaliser le libellé de données, masquer le nom de catégorie
  du graphique et afficher la valeur du libellé avec Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: fr
lastmod: 2026-09-11
og_description: Le tutoriel d'édition d'étiquettes de graphique vous guide à travers
  la modification de la position de l'étiquette du graphique, la personnalisation
  de l'étiquette de données du graphique, le masquage du nom de catégorie du graphique
  et l'affichage de la valeur de l'étiquette du graphique en utilisant Aspose.Words
  pour .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Tutoriel de modification d'étiquette de graphique – personnalisez les étiquettes
  de graphique Word en C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Tutoriel de modification d'étiquette de graphique – modifier les étiquettes
  de graphique Word en C#
url: /fr/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutoriel de modification d’étiquette de graphique – modifier les étiquettes de graphique Word en C#

Si vous devez **modifier les étiquettes de graphique** d’un document Word, ce guide vous montre exactement comment changer la position de l’étiquette, personnaliser l’étiquette de données du graphique, masquer le nom de catégorie du graphique et afficher la valeur de l’étiquette du graphique en utilisant Aspose.Words pour .NET. Vous verrez un exemple complet et exécutable que vous pouvez intégrer à n’importe quel projet C#.

Travailler avec les étiquettes de graphique est une exigence courante lors de la génération de rapports, factures ou tableaux de bord de façon programmatique. Ce tutoriel couvre chaque étape – du chargement du document à la persistance des modifications – afin que vous puissiez produire des graphiques soignés sans édition manuelle.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 ou version ultérieure installé  
* Une licence valide d’Aspose.Words pour .NET (ou une clé d’évaluation temporaire)  
* Visual Studio 2022 ou tout IDE compatible C#  
* Un fichier Word (`Chart.docx`) contenant au moins un graphique  

Aucun package NuGet supplémentaire n’est requis au‑delà de `Aspose.Words`.

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez une nouvelle application console et ajoutez le package NuGet Aspose.Words :

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Ouvrez `Program.cs` et importez les espaces de noms requis :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Ces espaces de noms vous donnent accès à la classe `Document` pour manipuler les fichiers Word et aux classes `Chart` pour travailler avec les éléments de graphique.

## Étape 2 : Charger le document Word contenant un graphique

La première ligne exécutable charge le document source. Remplacez `YOUR_DIRECTORY` par le chemin réel où se trouve `Chart.docx`.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Le chargement du document crée une représentation en mémoire que vous pouvez parcourir et modifier.

## Étape 3 : Récupérer le premier graphique du document

Les graphiques sont stockés comme nœuds enfants de type `NodeType.Chart`. La méthode `GetChild` parcourt l’arbre du document et renvoie le graphique que vous souhaitez modifier.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Si le document contient plusieurs graphiques, vous pouvez changer l’index pour cibler un autre graphique.

## Étape 4 : Accéder et personnaliser l’étiquette de données de la première série

Chaque série de graphique possède un objet `DataLabel` qui contrôle l’apparence de l’étiquette. Le code ci‑dessous montre les quatre personnalisations clés requises par les mots‑clés secondaires du tutoriel.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Pourquoi ces paramètres sont importants**

* `DataLabelPosition.Center` déplace l’étiquette de la position par défaut « à l’extérieur du point » vers le centre du point de données, rendant le graphique plus lisible lorsque les points sont très rapprochés.  
* Définir un `Separator` personnalisé vous permet de contrôler la façon dont le nom de la série, la valeur et les autres parties sont concaténés.  
* Masquer le nom de catégorie (`ShowCategoryName = false`) réduit l’encombrement visuel lorsque la catégorie est déjà évidente grâce à l’axe.  
* Activer `ShowValue` garantit que la valeur réelle des données est visible, ce qui est souvent requis pour les rapports financiers ou statistiques.

## Étape 5 : Enregistrer le document modifié

Après avoir ajusté les propriétés de l’étiquette, persistez les modifications dans un nouveau fichier :

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Le nouveau fichier (`CustomLabelChart.docx`) conserve la même disposition du graphique mais avec l’apparence d’étiquette que vous avez définie.

## Code source complet

Voici le programme complet, prêt à être exécuté. Copiez‑le dans `Program.cs`, ajustez les chemins de fichiers, puis lancez le projet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Résultat attendu

Ouvrez `CustomLabelChart.docx` dans Microsoft Word. Vous devriez voir l’étiquette de la première série du graphique centrée sur chaque point de données, affichant uniquement la valeur numérique et utilisant « ; » comme séparateur. Les noms de catégorie n’apparaîtront plus à côté des valeurs.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|---------|
| **Que faire si le document ne contient aucun graphique ?** | L’exemple vérifie la présence d’un graphique `null` et quitte proprement avec un message dans la console. |
| **Puis‑je modifier les étiquettes de plusieurs séries ?** | Oui. Parcourez `chart.Series` et appliquez les mêmes paramètres `DataLabel` à chaque `Series[i].DataLabel`. |
| **Comment changer le style de police de l’étiquette ?** | Utilisez `label.Font` (par ex., `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **`DataLabelPosition.Center` est‑il pris en charge par tous les types de graphiques ?** | La plupart des graphiques 2‑D le supportent. Pour les graphiques 3‑D, certaines positions peuvent être ignorées par Word. |
| **Ai‑je besoin d’une licence pour Aspose.Words ?** | Le mode d’évaluation fonctionne mais ajoute un filigrane. Une licence supprime le filigrane et débloque toutes les fonctionnalités. |

## Astuces professionnelles

* **Traitement par lots :** Encapsulez la logique de chargement et d’enregistrement dans une méthode qui accepte les chemins d’entrée et de sortie. Cela facilite le traitement de dizaines de documents dans une boucle.  
* **Performance :** Réutilisez une seule instance `Document` lorsque vous modifiez plusieurs graphiques dans le même fichier afin d’éviter des opérations d’E/S répétées.  
* **Tests :** Vérifiez les changements d’étiquette en automatisant une comparaison visuelle (par ex., à l’aide d’un visualiseur Word sans interface) si vous devez valider la sortie dans des pipelines CI.

## Prochaines étapes

Maintenant que vous maîtrisez les bases du **tutoriel de modification d’étiquette de graphique**, vous pouvez explorer :

* **Modifier la position de l’étiquette de graphique** pour d’autres séries ou types de graphiques  
* **Personnaliser le formatage de l’étiquette de données du graphique** (formats numériques, couleurs de police, remplissages d’arrière‑plan)  
* **Masquer le nom de catégorie du graphique** tout en affichant le nom de la série pour les graphiques multi‑séries  
* **Afficher la valeur de l’étiquette du graphique** conjointement avec les pourcentages pour les graphiques circulaires  

Ces sujets approfondissent votre contrôle sur l’esthétique des graphiques Word et vous préparent à des scénarios de reporting avancés.

---

*Bon codage ! Si ce tutoriel vous a été utile, partagez‑le avec vos collègues ou contribuez à l’amélioration du projet sur GitHub.*

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}