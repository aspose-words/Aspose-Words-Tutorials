---
date: 2026-01-16
description: Apprenez à mettre en évidence les fautes d’orthographe dans Word en utilisant
  Aspose.Words pour Java, et découvrez comment définir le nombre de caractères par
  ligne, personnaliser les options d’affichage et nettoyer les styles.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Surligner les fautes d'orthographe dans Word avec Aspose.Words Java
url: /fr/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des options et paramètres de document dans Aspose.Words for Java

## Introduction à l’utilisation des options et paramètres de document dans Aspose.Words for Java

Dans ce guide complet, vous apprendrez **comment mettre en évidence les fautes d’orthographe dans Word** à l’aide d’Aspose.Words for Java tout en maîtrisant les paramètres associés tels que les options d’affichage, la mise en page et le nettoyage des styles. Que vous soyez un développeur chevronné ou que vous débutiez, les exemples ci‑dessous vous aideront à créer des documents robustes, sensibles aux erreurs, compatibles avec les différentes versions de Word.

## Réponses rapides
- **Comment mettre en évidence les fautes d’orthographe dans Word ?** Utilisez `setShowSpellingErrors(true)` sur l’objet `Document`.  
- **Puis‑je également afficher les fautes grammaticales ?** Oui — appelez `setShowGrammaticalErrors(true)`.  
- **Quelle méthode définit le nombre de caractères par ligne ?** `getPageSetup().setCharactersPerLine(int)`.  
- **Quelle API optimise pour une version spécifique de Word ?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Existe‑t‑il un moyen de nettoyer les styles inutilisés ?** Utilisez `CleanupOptions` avec `setUnusedStyles(true)` et appelez `doc.cleanup(options)`.

## Comment mettre en évidence les fautes d’orthographe dans Word ?

Aspose.Words rend simple l’activation de la mise en évidence des fautes d’orthographe. Lorsque le document est ouvert dans Microsoft Word, les mots mal orthographiés apparaissent avec le soulignement rouge familier, aidant les utilisateurs finaux à repérer les problèmes instantanément.

## Comment définir le nombre de caractères par ligne

Contrôler le nombre de caractères par ligne est essentiel pour les mises en page à largeur fixe (par ex., les listes de code ou les formulaires hérités). La classe `PageSetup` fournit `setCharactersPerLine(int)` qui vous permet de définir cette valeur avec précision.

## Comment afficher les fautes grammaticales

Au‑delà de l’orthographe, vous pouvez également activer l’affichage des fautes grammaticales. Cela est utile pour la rédaction de contenus qui doivent respecter des guides de style ou pour la création d’outils de relecture.

## Optimisation des documents pour la compatibilité

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Un aspect clé de la gestion des documents est d’assurer la compatibilité avec les différentes versions de Microsoft Word. Aspose.Words for Java offre une méthode simple pour optimiser les documents pour des versions spécifiques de Word. Dans l’exemple ci‑dessus, nous optimisons un document pour Word 2016, garantissant une compatibilité fluide.

## Identification des fautes grammaticales et orthographiques

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

La précision est primordiale lorsqu’on travaille avec des documents. Aspose.Words for Java vous permet de mettre en évidence les fautes grammaticales et orthographiques dans vos documents, rendant la relecture et l’édition plus efficaces.

## Nettoyage des styles et listes inutilisés

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Gérer efficacement les styles et listes d’un document est essentiel pour maintenir la cohérence. Aspose.Words for Java vous permet de nettoyer les styles et listes inutilisés, assurant une structure de document épurée et organisée.

## Suppression des styles en double

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Les styles en double peuvent entraîner confusion et incohérence dans vos documents. Avec Aspose.Words for Java, vous pouvez facilement supprimer les styles en double, préservant la clarté et la cohérence du document.

## Personnalisation des options d’affichage du document

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Adapter l’expérience de visualisation de vos documents est crucial. Aspose.Words for Java vous permet de définir diverses options d’affichage, telles que la mise en page et le pourcentage de zoom, afin d’améliorer la lisibilité du document.

## Configuration de la mise en page du document

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Une configuration de page précise est indispensable pour le formatage des documents. Aspose.Words for Java vous donne la possibilité de définir les modes de mise en page, **les caractères par ligne** et les lignes par page, garantissant que vos documents soient visuellement attrayants.

## Définition des langues d’édition

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Les langues d’édition jouent un rôle essentiel dans le traitement des documents. Avec Aspose.Words for Java, vous pouvez définir et personnaliser les langues d’édition pour répondre aux besoins linguistiques de votre document.

## Conclusion

Dans ce guide, nous avons exploré les différentes options et paramètres de document disponibles dans Aspose.Words for Java. De l’optimisation et de l’affichage des erreurs à la suppression des styles inutilisés et aux options d’affichage, cette bibliothèque puissante offre des capacités étendues pour gérer et personnaliser vos documents.

## FAQ's

### Comment optimiser un document pour une version spécifique de Word ?

Pour optimiser un document pour une version spécifique de Word, utilisez la méthode `optimizeFor` et spécifiez la version souhaitée. Par exemple, pour optimiser pour Word 2016 :

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Comment mettre en évidence les fautes grammaticales et orthographiques dans un document ?

Vous pouvez activer l’affichage des fautes grammaticales et orthographiques dans un document en utilisant le code suivant :

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Quel est l’objectif du nettoyage des styles et listes inutilisés ?

Le nettoyage des styles et listes inutilisés aide à maintenir une structure de document propre et organisée. Il élimine le désordre superflu, améliorant la lisibilité et la cohérence du document.

### Comment supprimer les styles en double d’un document ?

Pour supprimer les styles en double d’un document, utilisez la méthode `cleanup` avec l’option `duplicateStyle` définie sur `true`. Voici un exemple :

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Comment personnaliser les options d’affichage d’un document ?

Vous pouvez personnaliser les options d’affichage du document en utilisant la classe `ViewOptions`. Par exemple, pour définir le type de vue sur la mise en page et le zoom à 50 % :

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Conseils supplémentaires et pièges courants

- **Activez à la fois la vérification orthographique et grammaticale** lorsque vous avez besoin d’une relecture complète. Oublier l’un des indicateurs (`setShowGrammaticalErrors` ou `setShowSpellingErrors`) peut laisser des erreurs non détectées.  
- **Lors de la définition des caractères par ligne**, rappelez‑vous que la valeur interagit avec la police sélectionnée et les marges de la page. Testez avec la mise en page réelle du document pour éviter des sauts de ligne inattendus.  
- **Les opérations de nettoyage sont irréversibles** sur le fichier original. Travaillez toujours sur une copie ou utilisez le contrôle de version pour préserver le style d’origine.  
- **Les préférences de langue d’édition** influencent le comportement du correcteur orthographique. Si vous ciblez des documents multilingues, ajoutez toutes les langues pertinentes à `LanguagePreferences`.

---

**Dernière mise à jour :** 2026-01-16  
**Testé avec :** Aspose.Words for Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}