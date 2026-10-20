---
category: general
date: 2026-05-04
description: Le tutoriel de substitution de polices Aspose montre comment gérer les
  polices manquantes en Java en utilisant des rappels d’avertissement et les LoadOptions
  pour un chargement fiable des documents.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: fr
og_description: Le tutoriel de substitution de polices Aspose explique comment gérer
  les polices manquantes en Java, capturer les événements de substitution et garder
  vos documents correctement affichés.
og_title: Tutoriel de substitution de polices Aspose – Gérer les polices manquantes
tags:
- Aspose.Words
- Java
- Font Management
title: Tutoriel de substitution de polices Aspose – Gérer les polices manquantes
url: /fr/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutoriel de substitution de police Aspose – Gérer les polices manquantes

Vous avez déjà eu besoin d’un **tutoriel de substitution de police Aspose** parce qu’un DOCX que vous chargez apparaît soudainement incorrect ? Vous n’êtes pas seul — les polices manquantes sont une source sournoise de bugs qui peuvent transformer un rapport parfaitement formaté en un fouillis illisible. La bonne nouvelle, c’est qu’Aspose.Words vous offre un moyen propre de **gérer les polices manquantes** avant qu’elles ne cassent votre mise en page.

Dans ce guide, nous parcourrons un exemple Java complet, prêt à l’exécution, qui capture les avertissements de substitution de police, explique pourquoi chaque élément est important et montre comment vérifier le résultat. À la fin, vous saurez exactement comment garder vos documents impeccables même lorsque les polices d’origine ne sont pas présentes sur la machine.

## Ce que vous allez apprendre

- Comment enregistrer un `IWarningCallback` personnalisé qui écoute les événements `FONT_SUBSTITUTION`.
- Pourquoi l’utilisation de `LoadOptions` est l’approche recommandée pour une gestion fiable des polices.
- Moyens de tester la solution avec un document délibérément corrompu.
- Pièges courants (par ex., oublier de définir le callback) et solutions rapides.

**Prérequis** : Java 8+ installé, une licence valide d’Aspose.Words for Java (ou l’évaluation gratuite), et un IDE de base comme IntelliJ ou Eclipse. Aucune autre bibliothèque externe n’est nécessaire.

---

![Diagramme du tutoriel de substitution de police Aspose](https://example.com/images/font-substitution-diagram.png "Diagramme du tutoriel de substitution de police Aspose")

## Étape 1 – Définir un callback d’avertissement pour capturer les substitutions  

La première chose qu’Aspose.Words fait lorsqu’il ne trouve pas la police demandée est de déclencher un événement `WarningInfo`. En implémentant `IWarningCallback`, vous pouvez enregistrer, afficher ou même interrompre le chargement si vous le souhaitez.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**Pourquoi c’est important** – Sans callback, vous ne sauriez jamais qu’Aspose a remplacé *Arial* par *Liberation Sans* (ou tout autre substitut choisi). Ce remplacement silencieux peut entraîner des déplacements de mise en page, notamment dans les tableaux ou les dispositions à plusieurs colonnes.

---

## Étape 2 – Attacher le callback à `LoadOptions`

`LoadOptions` est le point central de tout ce qui influence la lecture d’un document. En branchant le callback ici, vous garantissez que **tout** document chargé avec ces options déclenchera votre logique d’avertissement.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**Astuce** – Si vous prévoyez de charger plusieurs documents en lot, réutilisez la même instance de `LoadOptions`. Cela économise le coût de création d’objets et maintient votre journalisation cohérente.

---

## Étape 3 – Charger un document qui pourrait nécessiter une substitution de police  

Nous lisons maintenant réellement un fichier dont nous savons qu’il manque une police. Remplacez `YOUR_DIRECTORY` par le dossier contenant vos fichiers de test.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

Lorsque le chargeur rencontre un glyphe qui ne peut pas être rendu, le callback de **l’Étape 1** affiche un message convivial dans la console. Par exemple :

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**Cas limite** – Si le document contient des polices *intégrées*, Aspose les utilisera d’abord et ignorera l’avertissement. C’est le comportement attendu ; vous ne voyez des avertissements que pour les polices réellement manquantes.

---

## Étape 4 – Enregistrer le document (maintenant avec les polices substituées)

Après la fin du chargement, Aspose a déjà remplacé les polices manquantes en interne. En enregistrant le document, la substitution est préservée, de sorte que la sortie ressemble exactement à ce que vous avez vu dans la console.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Ouvrez `loaded.docx` dans Word ou LibreOffice et vous verrez la mise en page inchangée, même si la police d’origine n’est pas installée sur votre machine.

---

## Étape 5 – Vérifier le résultat programmatique (optionnel)

Si vous voulez être absolument certain qu’aucune substitution inattendue ne s’est glissée, vous pouvez interroger la table des polices du document après le chargement.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

La sortie doit contenir la police de secours (par ex., *Arial*) à la place de celle qui manque. Cela est pratique pour les pipelines automatisés où vous devez garantir que le PDF ou le DOCX final respecte les exigences de la charte graphique.

---

## Astuces pro & pièges courants

- **Astuce pro :** Définissez `loadOptions.setFontSettings(new FontSettings())` si vous devez indiquer à Aspose un dossier de polices personnalisé avant le chargement. Cela réduit le nombre de substitutions.
- **Attention :** Oublier d’appeler `setWarningCallback`. Le code s’exécutera tout de même, mais vous manquerez les messages de diagnostic cruciaux.
- **Note de performance :** Charger de gros documents avec de nombreuses polices manquantes peut générer beaucoup d’avertissements. Envisagez de limiter la sortie ou d’écrire dans un fichier de log plutôt que dans `System.out`.
- **Et si vous devez interrompre le chargement en cas de substitution ?** Remplacez l’appel `System.out.println` par `throw new RuntimeException(info.getDescription())` dans le callback. Cela force l’échec du chargement, ce qui est utile pour les scénarios de conformité stricte.

---

## Questions fréquentes

**Q : Cette méthode fonctionne-t-elle avec les formats PDF ou image ?**  
R : Le callback d’avertissement est spécifique à la phase de chargement des formats de traitement Word (`.docx`, `.doc`, `.rtf`, etc.). Le rendu PDF utilise un pipeline différent, mais vous pouvez toujours capturer les avertissements liés aux polices via `PdfLoadOptions`.

**Q : Puis‑je substituer une police spécifique par une autre de mon choix ?**  
R : Oui. Créez un objet `FontSettings`, appelez `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")`, puis assignez‑le à `loadOptions.setFontSettings(fontSettings)`.

**Q : Le callback est‑il thread‑safe ?**  
R : L’implémentation par défaut n’est pas synchronisée. Si vous chargez des documents en parallèle, assurez‑vous que votre implémentation du callback gère l’accès concurrent (par ex., en utilisant `ConcurrentLinkedQueue` pour la journalisation).

---

## Conclusion

Vous disposez maintenant d’un **tutoriel complet de substitution de police Aspose** qui montre comment **gérer les polices manquantes** de façon élégante en Java. En définissant un `IWarningCallback` personnalisé, en l’attachant à `LoadOptions` et en enregistrant le document, vous conservez une sortie cohérente quel que soit le jeu de polices installé sur la machine hôte.  

À partir d’ici, vous pourriez explorer :

- Tables de substitution de polices personnalisées pour des remplacements conformes à la charte graphique.  
- Intégrer le logger d’avertissement avec SLF4J ou Log4j pour des diagnostics de niveau production.  
- Étendre le callback pour collecter des statistiques sur un lot de documents.

Testez-le, ajustez les polices de secours, et laissez vos documents rester magnifiques même lorsque les polices d’origine disparaissent. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}