---
date: 2025-11-28
description: Apprenez à modifier les bordures des cellules et à mettre en forme les
  tableaux avec Aspose.Words for Java. Ce guide étape par étape couvre la définition
  des bordures, l'application du style première colonne, l'ajustement automatique
  du contenu du tableau et l'application des styles de tableau.
language: fr
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Comment modifier les bordures des cellules dans les tableaux – Aspose.Words
  pour Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment modifier les bordures des cellules dans les tableaux – Aspose.Words for Java

## Introduction

Lorsqu’il s’agit de la mise en forme des documents, les tableaux jouent un rôle crucial, et **savoir comment modifier les bordures des cellules** est essentiel pour créer des mises en page claires et professionnelles. Si vous développez en Java avec Aspose.Words, vous disposez déjà d’une boîte à outils puissante. Dans ce tutoriel, nous parcourrons l’ensemble du processus de mise en forme des tableaux, de modification des bordures des cellules, d’application du *style première colonne*, et d’utilisation du *auto‑fit du contenu du tableau* pour donner à vos documents un aspect soigné.

## Réponses rapides
- **Quelle est la classe principale pour créer des tables ?** `DocumentBuilder` crée des tables et des cellules de façon programmatique.  
- **Comment modifier l’épaisseur de la bordure d’une seule cellule ?** Utilisez `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Puis‑je appliquer un style de tableau prédéfini ?** Oui – appelez `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Quelle méthode ajuste automatiquement un tableau à son contenu ?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Ai‑je besoin d’une licence pour la production ?** Une licence valide d’Aspose.Words est requise pour une utilisation hors période d’essai.

## Qu’est‑ce que « comment modifier les bordures des cellules » dans Aspose.Words ?

Modifier les bordures des cellules signifie personnaliser les lignes visuelles qui séparent les cellules — couleur, largeur et style de ligne. Aspose.Words expose une API riche qui vous permet d’ajuster ces propriétés au niveau du tableau, de la ligne ou de chaque cellule, vous offrant ainsi un contrôle précis sur l’apparence de vos documents.

## Pourquoi utiliser Aspose.Words for Java pour le style des tableaux ?

- **Aspect cohérent sur toutes les plateformes** – le même code de style fonctionne sous Windows, Linux et macOS.  
- **Pas de dépendance à Microsoft Word** – générez ou modifiez des documents côté serveur.  
- **Bibliothèque de styles riche** – styles de tableau intégrés (par ex., *style première colonne*) et capacités complètes d’auto‑fit.  

## Prérequis

1. **Java Development Kit (JDK) 8+** – assurez‑vous que `java` est dans votre PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse ou tout autre éditeur de votre choix.  
3. **Aspose.Words for Java** – téléchargez le JAR le plus récent depuis le [site officiel](https://releases.aspose.com/words/java/).  
4. **Connaissances de base en Java** – vous devez être à l’aise avec la création d’un projet Maven/Gradle et l’ajout de JAR externes.

## Importer les packages

Pour commencer à travailler avec les tableaux, vous avez besoin des classes principales d’Aspose.Words :

```java
import com.aspose.words.*;
```

Cette unique importation vous donne accès à `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` et bien d’autres utilitaires.

## Comment modifier les bordures des cellules

Nous allons créer un tableau simple, modifier ses bordures globales, puis personnaliser les cellules individuelles.

### Étape 1 : Charger un nouveau document

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Étape 2 : Créer le tableau et définir les bordures globales

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Étape 3 : Modifier les bordures d’une seule cellule

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Ce que fait le code
- **Bordures globales** – `table.setBorders` applique à tout le tableau une ligne noire de 2 points.  
- **Ombrage de cellule** – montre comment colorer des cellules individuelles (rouge et vert).  
- **Bordures personnalisées** – la troisième cellule reçoit une bordure de 4 points sur tous les côtés, ce qui la fait ressortir.

## Application des styles de tableau (y compris le style première colonne)

Les styles de tableau vous permettent d’appliquer un aspect cohérent en un seul appel. Nous montrerons également comment activer le *style première colonne* et ajuster automatiquement le tableau à son contenu.

### Étape 4 : Créer un nouveau document pour le style

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Étape 5 : Appliquer un style prédéfini et activer le formatage de la première colonne

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Étape 6 : Remplir le tableau avec des données

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Pourquoi c’est important
- **Identifiant de style** – `MEDIUM_SHADING_1_ACCENT_1` donne au tableau un aspect épuré et ombré.  
- **Style première colonne** – mettre en évidence la première colonne améliore la lisibilité, surtout dans les rapports.  
- **Bandes de lignes** – les couleurs de ligne alternées facilitent la lecture de grands tableaux.  
- **Auto‑fit** – garantit que la largeur du tableau s’adapte au contenu, évitant le texte tronqué.

## Problèmes courants et dépannage

| Problème | Cause typique | Solution rapide |
|----------|---------------|-----------------|
| Les bordures n’apparaissent pas | Utilisation de `clearFormatting()` après la définition des bordures | Définissez les bordures **après** le nettoyage du format, ou réappliquez‑les. |
| L’ombrage est ignoré sur les cellules fusionnées | Ombrage appliqué avant la fusion | Appliquez l’ombrage **après** la fusion des cellules. |
| La largeur du tableau dépasse les marges de la page | Aucun auto‑fit appliqué | Appelez `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` ou définissez une largeur fixe. |
| Le style n’est pas appliqué | Valeur `StyleIdentifier` incorrecte | Vérifiez que l’identifiant existe dans la version d’Aspose.Words que vous utilisez. |

## Questions fréquentes

**Q : Puis‑je utiliser des styles de tableau personnalisés qui ne sont pas inclus dans les options par défaut ?**  
R : Oui, vous pouvez créer et appliquer des styles personnalisés par programme. Consultez la [documentation d’Aspose.Words](https://reference.aspose.com/words/java/) pour plus de détails.

**Q : Comment appliquer une mise en forme conditionnelle aux cellules ?**  
R : Utilisez la logique Java standard pour inspecter les valeurs des cellules, puis appelez les méthodes de mise en forme appropriées (par ex., changer la couleur d’arrière‑plan si une valeur dépasse un seuil).

**Q : Est‑il possible de formater les cellules fusionnées de la même façon que les cellules normales ?**  
R : Absolument. Après la fusion des cellules, appliquez l’ombrage ou les bordures en utilisant les mêmes API `CellFormat`.

**Q : Que faire si le tableau doit se redimensionner dynamiquement en fonction d’une saisie utilisateur ?**  
R : Ajustez les largeurs de colonne ou appelez de nouveau `autoFit` après l’insertion de nouvelles données pour recalculer la mise en page.

**Q : Où puis‑je trouver davantage d’exemples de style de tableau ?**  
R : Le [site officiel de la documentation API Aspose.Words](https://reference.aspose.com/words/java/) propose un ensemble complet d’exemples.

## Conclusion

Vous disposez maintenant d’une boîte à outils complète pour **modifier les bordures des cellules**, appliquer le *style première colonne*, et **ajuster automatiquement le contenu du tableau** avec Aspose.Words for Java. En maîtrisant ces techniques, vous pourrez produire des documents à la fois riches en données et visuellement attrayants—parfaits pour les rapports, factures et tout autre livrable critique pour l’entreprise.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Dernière mise à jour :** 2025-11-28  
**Testé avec :** Aspose.Words for Java 24.12 (dernière version au moment de la rédaction)  
**Auteur :** Aspose