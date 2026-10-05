---
category: general
date: 2026-02-21
description: Masquer une ligne dans un tableau avec C# et Aspose.Words. Apprenez comment
  masquer une ligne, comment masquer une ligne dans Word, et supprimer une ligne d’un
  tableau rapidement et en toute sécurité.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: fr
og_description: Masquer une ligne dans un tableau avec C# et Aspose.Words. Ce guide
  montre comment masquer une ligne, supprimer une ligne d’un tableau et masquer une
  ligne dans des documents Word.
og_title: Masquer une ligne dans un tableau avec C# – Méthode rapide et fiable
tags:
- C#
- Aspose.Words
- Word Automation
title: Masquer une ligne dans un tableau avec C# – Guide simple pour supprimer des
  lignes de tableau
url: /fr/net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Masquer une ligne dans un tableau – Tutoriel complet C#

Vous avez déjà eu besoin de **masquer une ligne dans un tableau** lors de la génération d'un document Word de façon programmatique ? Vous n'êtes pas le seul — les développeurs demandent constamment *comment masquer une ligne* sans casser la mise en page. Bonne nouvelle ? Avec quelques lignes de C# et la puissante bibliothèque Aspose.Words, vous pouvez masquer une ligne, la retirant effectivement du résultat final, tout en gardant votre code propre.

Dans ce guide, nous parcourrons l’ensemble du processus : charger un `.docx`, sélectionner la ligne exacte, définir sa propriété `Hidden`, puis enregistrer le résultat. À la fin, vous saurez exactement comment **hide row in Word**, comment **remove row from table** si vous préférez la suppression, et vous disposerez d’un extrait prêt à l’emploi que vous pourrez intégrer à n’importe quel projet .NET. Aucun référentiel externe requis — seulement le code et des explications claires.

**Ce que vous obtiendrez**  
- Un guide pas à pas de l’API C#.  
- Un code complet et exécutable (y compris les imports).  
- Des astuces pour les cas limites comme les lignes masquées dans des cellules fusionnées.  
- Des conseils pro sur le moment d’*hide row* vs. *remove row from table*.

> **Prérequis :** Visual Studio (ou tout IDE C#) et le package NuGet Aspose.Words for .NET (version 23.9 ou supérieure). Si vous débutez avec Aspose.Words, la bibliothèque est une solution purement gérée — aucune installation d’Office n’est nécessaire.

---

## Masquer une ligne dans un tableau – Implémentation étape par étape

Voici l’exemple complet et autonome. Il montre la tâche **principale** — *hide row in table* — et indique également comment *remove row from table* si vous décidez de la supprimer.

![Exemple de masquage d'une ligne dans un tableau](hide-row-in-table.png "Capture d'écran montrant un tableau Word avec la troisième ligne masquée")

### 1. Charger le document source  

Tout d’abord, nous devons charger le fichier Word en mémoire. La classe `Document` représente le fichier entier.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*Pourquoi c’est important :* Charger le document vous donne accès aux sections, corps et tableaux. Sans cette étape, vous ne pouvez pas manipuler les lignes du tout.

### 2. Localiser le tableau souhaité  

Par simplicité, nous récupérons le premier tableau de la première section, mais vous pouvez rechercher par index, nom ou même contenu.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **Astuce :** Si votre document contient plusieurs tableaux, parcourez `doc.GetChildNodes(NodeType.Table, true)` et choisissez celui dont vous avez besoin.

### 3. Choisir la ligne à masquer  

Ici nous ciblons la troisième ligne (index zéro‑based `2`). Vous pouvez également utiliser `Rows.Count` pour vérifier que l’index existe.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*Pourquoi c’est important :* Sélectionner la bonne ligne est le cœur du **how to hide row**. Une mauvaise indexation masquera le mauvais contenu.

### 4. Masquer la ligne sélectionnée  

Définir `Hidden = true` indique à Aspose.Words d’omettre la ligne lors de l’enregistrement du document. La ligne reste présente dans le modèle d’objet, vous pouvez donc la réafficher plus tard si besoin.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **Conseil pro :** Si vous voulez réellement *remove row from table* au lieu de masquer, appelez `table.Rows.Remove(rowToHide);`. Le masquage préserve les métadonnées de la ligne, ce qui peut être pratique pour le formatage conditionnel.

### 5. Enregistrer le document mis à jour  

Enfin, écrivez les modifications sur le disque.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

Lorsque vous ouvrez `output.docx` dans Word, la troisième ligne sera invisible — exactement ce que signifie **hide row in word** en pratique.

---

## Comment masquer une ligne – Variations courantes et cas limites

### Masquer plusieurs lignes  

Si vous devez masquer plusieurs lignes, parcourez la collection :

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### Gérer les cellules fusionnées  

Une ligne masquée contenant une cellule fusionnée verticalement peut générer des avertissements de mise en page. L’approche sûre consiste à séparer la fusion avant de masquer :

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### Compatibilité avec les versions plus anciennes de Word  

Aspose.Words écrit l’attribut `w:hideMark`, compris par Word 2007+ et LibreOffice. Si vous ciblez Word 97‑2003 (`.doc`), la ligne masquée sera toujours omise, mais les tableaux complexes peuvent s’afficher différemment. Privilégiez le format `.docx` pour des résultats prévisibles.

### Quand *Hide Row* vs. *Remove Row from Table*  

- **Hide Row** – Conservez la ligne pour la réafficher plus tard, préservez la hauteur de ligne pour les calculs de saut de page.  
- **Remove Row** – Réduisez la taille du fichier, supprimez définitivement les données. Utilisez `table.Rows.Remove(row)` si vous êtes sûr que la ligne ne sera plus nécessaire.

---

## Conseils pro & Pièges à éviter

- **Conseil pro :** Vérifiez toujours `table.Rows.Count` avant d’accéder à un index afin d’éviter `ArgumentOutOfRangeException`.  
- **Attention à :** Les lignes masquées participent toujours aux calculs du tableau comme la hauteur totale. Si vous remarquez des espaces inattendus, envisagez de définir `row.Height = 0` après le masquage.  
- **Performance :** Masquer des lignes est peu coûteux ; supprimer des lignes déclenche un re‑layout complet du tableau, ce qui peut être plus lent sur de très gros documents.  
- **Tests :** Ouvrez le fichier enregistré dans Word et utilisez **Reveal Formatting** (`Shift+F1`) pour vérifier que le drapeau `Hidden` de la ligne est bien activé.

---

## Exemple complet fonctionnel (prêt à copier‑coller)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**Résultat attendu :** Ouvrez `output.docx` et vous verrez le tableau sans la troisième ligne, le reste du contenu restant intact. La ligne masquée fait toujours partie du modèle du document, vous pouvez donc plus tard définir `row.Hidden = false` pour la rendre visible à nouveau.

---

## Conclusion

Nous venons de couvrir **how to hide row** dans un tableau Word avec C#. En chargeant le document, en localisant le tableau, en sélectionnant la ligne cible, en la marquant comme masquée, puis en enregistrant, vous réalisez une opération propre de *hide row in table* sans supprimer les données. Le même schéma vous permet de *remove row from table* si vous avez besoin d’un changement permanent, et les conseils supplémentaires vous aident à éviter les pièges courants liés aux cellules fusionnées ou aux versions plus anciennes de Word.

Prêt pour le prochain défi ? Essayez de combiner cette technique avec une logique conditionnelle — masquez des lignes en fonction de l’entrée utilisateur, ou générez des rapports dynamiques où certaines sections disparaissent automatiquement. Vous pouvez également explorer **hide row in word** pour les en‑têtes, pieds de page ou même des sections entières.

Des questions sur *hide row c#* ou besoin d’aide pour intégrer cela dans un flux de travail plus large ? Laissez un commentaire ci‑dessous ou consultez nos tutoriels associés sur **manipulating tables in Word with Aspose.Words**. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}