---
category: general
date: 2026-03-14
description: Ajoutez rapidement une ombre à la forme et apprenez comment modifier
  l’angle de l’ombre, enregistrer le document avec l’ombre, et bien plus dans ce tutoriel
  C# étape par étape.
draft: false
keywords:
- add shadow to shape
- change shadow angle
- how to add shape shadow
- save document with shadow
language: fr
og_description: Ajoutez rapidement une ombre à une forme, apprenez à modifier l’angle
  de l’ombre et enregistrez le document avec l’ombre en utilisant Aspose.Words pour
  .NET.
og_title: Ajouter une ombre à une forme en C# – Guide complet d'Aspose.Words
tags:
- Aspose.Words
- C#
- Document Automation
title: Ajouter une ombre à une forme en C# – Guide complet d'Aspose.Words
url: /fr/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-aspose-words-guide/
---

translate code placeholders.

Also translate table content.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une ombre à une forme en C# – Guide complet Aspose.Words

Vous avez déjà eu besoin **d’ajouter une ombre à une forme** sans savoir quelles propriétés modifier ? Vous n’êtes pas seul ; de nombreux développeurs rencontrent ce problème lorsqu’ils stylisent des documents Word par programmation. La bonne nouvelle, c’est qu’avec Aspose.Words vous pouvez activer une ombre réaliste, ajuster son angle et enregistrer les modifications en un seul flux de travail propre.  

Dans ce tutoriel, nous passerons en revue tout ce qu’il faut savoir : du chargement d’un document, à l’activation de l’ombre, en passant par le réglage fin de son apparence, jusqu’à **enregistrer le document avec l’ombre**. À la fin, vous pourrez répondre à « comment ajouter une ombre à une forme » sans fouiller des posts de forum épars.

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (v23.10 ou ultérieure – l’API que nous utilisons n’a pas changé depuis)
- Un IDE compatible .NET (Visual Studio, Rider ou VS Code)
- Un fichier Word simple (`input.docx`) contenant déjà au moins une forme (un rectangle, une image ou un SmartArt convient)
- Des connaissances de base en C# – si vous avez déjà écrit un « Hello World », vous êtes prêt

> **Astuce pro :** Si vous n’avez pas de document prêt, créez‑en rapidement un dans Word, insérez une forme via *Insertion → Formes*, puis enregistrez‑le sous `input.docx` dans le dossier de votre projet.

## Étape 1 – Charger le document et récupérer la forme cible

La première chose consiste à charger le fichier Word en mémoire et à localiser la forme que vous souhaitez décorer. Aspose.Words traite chaque élément de dessin comme un nœud `Shape`, que vous pouvez récupérer avec `GetChild`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the Word document that contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// If you have multiple shapes, change the index or loop through them.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

**Pourquoi c’est important :**  
`Document` est le point d’entrée pour toute manipulation. L’appel `GetChild` parcourt l’arbre des nœuds en profondeur, garantissant que vous obtenez la toute première forme, quel que soit son emplacement (en‑tête, pied de page, corps). Si vous sautez cette étape et essayez d’accéder directement à `shape`, vous obtiendrez une `NullReferenceException`.

## Étape 2 – Activer l’effet d’ombre

Les ombres sont désactivées par défaut, il faut donc les activer avant de modifier les propriétés visuelles. Ce n’est qu’une seule ligne, mais elle débloque toute une gamme d’options.

```csharp
// Turn the shadow on.
shape.Shadow.Enabled = true;
```

> **Le saviez‑vous ?** L’objet `Shadow` existe même lorsque la fonctionnalité est désactivée, vous pouvez donc le pré‑configurer et l’activer plus tard sans code supplémentaire.

## Étape 3 – Configurer les propriétés principales de l’ombre

Nous arrivons à la partie amusante : définir la couleur, la transparence, le flou, la distance et la taille. Ces valeurs sont exprimées en points ou en pourcentages, comme dans l’interface Word.

```csharp
// Basic visual settings
shape.Shadow.Color = Color.Black;          // Shadow colour
shape.Shadow.Transparency = 0.3f;          // 30 % transparent
shape.Shadow.BlurRadius = 5.0f;            // Softness of the edge
shape.Shadow.Distance = 3.0f;              // Gap between shape and shadow
shape.Shadow.Size = 100;                   // Scale of the shadow (percent)
```

**Explication :**  
- **Color** détermine la teinte ; le noir convient à la plupart des cas, mais vous pouvez l’adapter aux couleurs de votre marque.  
- **Transparency** est un flottant compris entre `0` (opaque) et `1` (complètement invisible).  
- **BlurRadius** contrôle le degré de « flou » de l’ombre ; des valeurs plus élevées donnent un rendu plus doux.  
- **Distance** éloigne l’ombre de la forme, créant de la profondeur.  
- **Size** met à l’échelle l’ombre proportionnellement – 100 % signifie que l’ombre a la même taille que la forme.

## Étape 4 – Modifier l’angle de l’ombre (mot‑clé secondaire)

Si vous voulez que la source de lumière provienne d’une direction différente, ajustez la propriété `Angle`. C’est ici que le mot‑clé **change shadow angle** prend tout son sens.

```csharp
// Rotate the light source – 45 degrees is a common default.
shape.Shadow.Angle = 45;   // Angle in degrees (0‑360)
```

> **Et si vous vouliez un effet dramatique ?** Essayez `0` pour une lumière de gauche à droite, `90` pour un éclairage du haut, ou `180` pour une ombre inversée. Rappelez‑vous que les angles sont cycliques, donc `360` équivaut à `0`.

## Étape 5 – Enregistrer le document avec l’ombre

Une fois que l’ombre a l’apparence souhaitée, persistez les modifications. La méthode `Save` écrit un nouveau fichier tout en laissant l’original intact.

```csharp
// Save the modified document.
doc.Save("YOUR_DIRECTORY/output.docx");
```

Vous avez maintenant un `output.docx` où la forme possède une ombre soignée. Ouvrez‑le dans Word pour vérifier – vous devriez voir un halo subtil, semi‑transparent, décalé selon l’angle que vous avez défini.

## Exemple complet fonctionnel

Voici le programme complet, prêt à être copié‑collé dans une application console. Les commentaires expliquent chaque bloc.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (adjust index if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable shadow.
        shape.Shadow.Enabled = true;

        // 4️⃣ Set visual properties.
        shape.Shadow.Color = Color.Black;
        shape.Shadow.Transparency = 0.3f;
        shape.Shadow.BlurRadius = 5.0f;
        shape.Shadow.Distance = 3.0f;
        shape.Shadow.Size = 100;

        // 5️⃣ Change shadow angle (how to add shape shadow from a different direction).
        shape.Shadow.Angle = 45; // Try 0, 90, 180, etc.

        // 6️⃣ Save the result – this is the step that lets you **save document with shadow**.
        doc.Save("YOUR_DIRECTORY/output.docx");

        System.Console.WriteLine("Shadow applied and document saved successfully!");
    }
}
```

### Résultat attendu

- L’ouverture de `output.docx` montre la forme d’origine entourée d’une ombre douce et noire.  
- Modifier `Angle` à `90` fera apparaître l’ombre directement sous la forme, simulant un éclairage du plafond.  
- Ajuster `Transparency` à `0.0f` donne une ombre opaque, tandis que `1.0f` la rend invisible (utile pour basculer).

## Pièges courants & comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **`shape` est `null`** | Le document ne contient aucune forme ou l’indice est incorrect. | Vérifiez que le fichier Word possède une forme, ou parcourez `doc.GetChildNodes(NodeType.Shape, true)` pour trouver la bonne. |
| **L’ombre n’apparaît pas dans Word** | `Shadow.Enabled` reste à `false` ou le type de forme ne supporte pas les ombres (ex. texte simple). | Assurez‑vous de travailler avec un objet `Shape` (images, dessins, SmartArt) et que `Enabled = true`. |
| **Couleur inattendue** | `Color` défini différemment de ce que vous voyez dans Word à cause de la surcharge du thème. | Utilisez `Color.FromArgb(0,0,0)` pour un noir pur, ou adaptez‑le au thème du document avec `shape.Shadow.ThemeColor`. |
| **Ralentissement des performances** | Modification de nombreuses formes dans un gros document sans regroupement. | Enveloppez les changements dans `doc.BeginUpdateWords()` / `doc.EndUpdateWords()` (Aspose.Words v24+). |

## Extensions de l’exemple

- **Formes multiples :** Parcourez toutes les formes et appliquez une ombre uniforme, ou variez `Angle` par forme pour un effet 3‑D.  
- **Couleurs dynamiques :** Récupérez les valeurs de couleur depuis un fichier de configuration pour respecter la charte graphique.  
- **Ombres conditionnelles :** N’ajoutez une ombre que si la largeur de la forme dépasse un certain seuil – idéal pour mettre en avant de grands diagrammes.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.Width > 200) // width in points
    {
        s.Shadow.Enabled = true;
        s.Shadow.Color = Color.Gray;
        s.Shadow.Angle = 30;
    }
}
```

## Conclusion

Nous avons couvert tout le cycle de **l’ajout d’une ombre à une forme** avec Aspose.Words pour .NET : chargement du document, activation de l’ombre, personnalisation de la couleur, du flou, de la distance, **modification de l’angle de l’ombre**, puis **enregistrement du document avec l’ombre**. Le code est autonome, fonctionne avec n’importe quelle version récente d’Aspose.Words, et montre à la fois le « comment » et le « pourquoi » de chaque propriété.

Prêt pour l’étape suivante ? Essayez les ombres en dégradé, ou combinez cette technique avec des effets de texte pour créer des rapports accrocheurs. Si vous rencontrez des cas particuliers – comme des formes dans les en‑têtes ou pieds de page – rappelez‑vous les astuces de traversée de l’arbre de nœuds que nous avons abordées.  

Bon codage, et que vos documents aient toujours la profondeur parfaite !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}