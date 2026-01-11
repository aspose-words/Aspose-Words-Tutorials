---
date: 2026-01-11
description: Apprenez à nettoyer un document Word en utilisant les options de nettoyage
  d’Aspose.Words for Java, notamment la suppression des paragraphes vides, des lignes
  de tableau vides et des champs inutilisés.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Nettoyer le document Word à l’aide des options de nettoyage Aspose.Words (Java)
url: /fr/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nettoyer un document Word à l'aide des options de nettoyage Aspose.Words (Java)

Dans ce tutoriel, vous découvrirez comment **nettoyer des fichiers de document Word** avec Aspose.Words for Java. Que vous génériez des factures, des contrats ou des rapports de fusion massive, des paragraphes vides indésirables, des champs inutilisés ou des lignes de tableau vides peuvent rendre le résultat final peu professionnel. Nous parcourrons chaque option de nettoyage étape par étape, vous montrerons le code exact dont vous avez besoin et expliquerons *pourquoi* chaque paramètre est important afin que vous puissiez produire des documents soignés à chaque fois.

## Réponses rapides
- **Que signifie « nettoyer un document Word » ?** Supprimer les paragraphes vides, les régions de fusion inutilisées, les lignes de tableau vides et d’autres éléments redondants après une opération de fusion.
- **Quelle option de nettoyage supprime les paragraphes vides ?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.
- **Comment supprimer les lignes de tableau vides ?** Utilisez `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.
- **Puis‑je me débarrasser des champs qui n’ont jamais été remplis ?** Oui – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` ou `REMOVE_EMPTY_FIELDS`.
- **Ai‑je besoin d’une licence pour exécuter ces exemples ?** Une version d’essai gratuite suffit pour l’évaluation ; une licence commerciale est requise pour la production.

## Qu’est‑ce que « Nettoyer un document Word » dans le contexte de la fusion de courrier ?
Lorsque vous effectuez une fusion de courrier, Aspose.Words insère des données dans les champs et les régions de fusion. Si certains champs reçoivent `null` ou des chaînes vides, le document peut se retrouver avec des paragraphes errants, des tableaux vides ou des régions de remplacement. Les **options de nettoyage** éliminent automatiquement ces artefacts, laissant un document propre et prêt à être imprimé.

## Pourquoi utiliser les options de nettoyage ?
- **Aspect professionnel :** Plus de lignes blanches ni de tableaux orphelins.  
- **Taille de fichier réduite :** La suppression des éléments inutilisés diminue le poids du document.  
- **Traitement en aval simplifié :** Les documents propres sont plus faciles à convertir en PDF, HTML ou autres formats.  
- **Gain de temps :** Un paramètre en une ligne remplace les scripts de post‑traitement manuels.

## Prérequis
- Environnement de développement Java (JDK 8+).  
- Bibliothèque Aspose.Words for Java – téléchargez‑la depuis [here](https://releases.aspose.com/words/java/).  
- Familiarité de base avec les concepts de fusion de courrier.

## Guide étape par étape

### Étape 1 : Comment supprimer les paragraphes vides (Java)
Tout d’abord, nous montrons comment éliminer les paragraphes qui ne contiennent aucun texte visible. Cela est particulièrement utile lorsqu’un champ de fusion se résout à `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Que se passe‑t‑il ici ?**  
- `REMOVE_EMPTY_PARAGRAPHS` indique à Aspose.Words de supprimer tout paragraphe qui reste vide après la fusion.  
- L’activation de `cleanupParagraphsWithPunctuationMarks` supprime également les paragraphes composés uniquement de ponctuation (par ex. « ? »).

### Étape 2 : Comment supprimer les régions non fusionnées
Si une région de fusion n’a aucune donnée correspondante, vous pouvez la supprimer entièrement.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Pourquoi c’est important :**  
Les régions inutilisées laissent souvent des sections vides ou des titres errants. Le drapeau `REMOVE_UNUSED_REGIONS` les nettoie automatiquement.

### Étape 3 : Comment supprimer les champs vides
Lorsqu’un champ reçoit une chaîne vide, vous pouvez vouloir que le champ entier soit retiré plutôt que de laisser un espace réservé vide.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Étape 4 : Comment supprimer les champs inutilisés
Si certains champs ne sont jamais référencés pendant la fusion, vous pouvez les éliminer complètement.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Étape 5 : Comment supprimer les champs contenant
Parfois, un champ de fusion se trouve à l’intérieur d’un paragraphe que vous souhaitez également supprimer.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Étape 6 : Comment supprimer les lignes de tableau vides
Les tableaux se retrouvent souvent avec des lignes ne contenant que des champs vides. Cette option supprime ces lignes.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Problèmes courants & dépannage
- **Paragraphes non supprimés :** Assurez‑vous d’appeler `setCleanupParagraphsWithPunctuationMarks(true)` *après* avoir défini l’option de nettoyage.  
- **Lignes de tableau vides persistantes :** Vérifiez que les cellules du tableau contiennent réellement des chaînes vides (et non des espaces).  
- **Champs inutilisés qui restent :** Revérifiez que vous utilisez le bon enum (`REMOVE_UNUSED_FIELDS`) et que les champs de fusion ne sont pas remplis accidentellement ailleurs.

## Questions fréquentes

**Q : Quelle est la différence entre `REMOVE_EMPTY_FIELDS` et `REMOVE_UNUSED_FIELDS` ?**  
R : `REMOVE_EMPTY_FIELDS` supprime les champs qui reçoivent une chaîne vide ou `null` pendant la fusion, tandis que `REMOVE_UNUSED_FIELDS` élimine les champs qui n’ont jamais été référencés par l’opération de fusion.

**Q : Puis‑je combiner plusieurs options de nettoyage ?**  
R : Oui. La méthode `setCleanupOptions` accepte un OU bit‑à‑bit des valeurs d’enum, vous permettant de nettoyer paragraphes, tableaux et régions en un seul appel.

**Q : L’activation de `cleanupParagraphsWithPunctuationMarks` affecte‑t‑elle le texte normal ?**  
R : Elle ne supprime que les paragraphes composés exclusivement de caractères de ponctuation (par ex. « ? » ou « --- »). Les phrases normales restent intactes.

**Q : Peut‑on personnaliser les caractères de ponctuation pris en compte ?**  
R : L’API actuelle utilise un ensemble prédéfini de caractères de ponctuation. Pour un comportement personnalisé, vous devrez post‑traiter le document après la fusion.

**Q : Ces options de nettoyage fonctionnent‑elles avec la conversion PDF ?**  
R : Absolument. Une fois le document Word nettoyé, vous pouvez le convertir en PDF, HTML ou tout autre format supporté sans transporter les éléments indésirables.

## Conclusion
Vous disposez maintenant d’une boîte à outils complète pour **nettoyer des fichiers de document Word** lors d’une fusion de courrier avec Aspose.Words for Java. En sélectionnant les `MailMergeCleanupOptions` appropriées, vous pouvez supprimer automatiquement les paragraphes vides, les lignes de tableau vides, les champs inutilisés, etc., et obtenir un document élégant, prêt pour la production, à chaque fois.

---

**Dernière mise à jour :** 2026-01-11  
**Testé avec :** Aspose.Words for Java 24.11  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}