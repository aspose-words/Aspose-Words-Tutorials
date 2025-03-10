---
title: Recherche et remplacement de texte dans Aspose.Words pour Java
linktitle: Recherche et remplacement de texte
second_title: API de traitement de documents Java Aspose.Words
description: Découvrez comment rechercher et remplacer du texte dans des documents Word avec Aspose.Words pour Java. Guide étape par étape avec des exemples de code. Améliorez vos compétences en manipulation de documents Java.
weight: 15
url: /fr/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recherche et remplacement de texte dans Aspose.Words pour Java


## Introduction à la recherche et au remplacement de texte dans Aspose.Words pour Java

Aspose.Words pour Java est une API Java puissante qui vous permet de travailler avec des documents Word par programmation. L'une des tâches courantes lors du traitement de documents Word consiste à rechercher et à remplacer du texte. Que vous ayez besoin de mettre à jour des espaces réservés dans des modèles ou d'effectuer des manipulations de texte plus complexes, Aspose.Words pour Java peut vous aider à atteindre vos objectifs efficacement.

## Prérequis

Avant de plonger dans les détails de la recherche et du remplacement de texte, assurez-vous que les conditions préalables suivantes sont remplies :

- Environnement de développement Java
- Bibliothèque Aspose.Words pour Java
- Un exemple de document Word avec lequel travailler

 Vous pouvez télécharger la bibliothèque Aspose.Words pour Java à partir de[ici](https://releases.aspose.com/words/java/).

## Recherche et remplacement de texte simple

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créer un DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Rechercher et remplacer du texte
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

 Dans cet exemple, nous chargeons un document Word, créons un`DocumentBuilder` , et utilisez le`replace` méthode pour rechercher et remplacer « ancien texte » par « nouveau texte » dans le document.

## Utilisation des expressions régulières

Les expressions régulières offrent de puissantes fonctionnalités de recherche et de remplacement de modèles. Aspose.Words pour Java prend en charge les expressions régulières pour des opérations de recherche et de remplacement plus avancées.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créer un DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Utiliser des expressions régulières pour rechercher et remplacer du texte
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Dans cet exemple, nous utilisons un modèle d’expression régulière pour rechercher et remplacer du texte dans le document.

## Ignorer le texte à l'intérieur des champs

Vous pouvez configurer Aspose.Words pour ignorer le texte à l'intérieur des champs lors de l'exécution d'opérations de recherche et de remplacement.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créez une instance FindReplaceOptions et définissez IgnoreFields sur true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Utiliser les options lors du remplacement du texte
doc.getRange().replace("text-to-replace", "new-text", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Ceci est utile lorsque vous souhaitez exclure du remplacement du texte à l'intérieur des champs, tels que les champs de fusion.

## Ignorer le texte à l'intérieur de la suppression des révisions

Vous pouvez configurer Aspose.Words pour ignorer le texte à l'intérieur des révisions de suppression pendant les opérations de recherche et de remplacement.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créez une instance FindReplaceOptions et définissez IgnoreDeleted sur true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Utiliser les options lors du remplacement du texte
doc.getRange().replace("text-to-replace", "new-text", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Cela vous permet d'exclure du remplacement le texte qui a été marqué pour suppression dans les modifications suivies.

## Ignorer le texte dans les révisions d'insertion

Vous pouvez configurer Aspose.Words pour ignorer le texte à l'intérieur des révisions d'insertion pendant les opérations de recherche et de remplacement.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créez une instance FindReplaceOptions et définissez IgnoreInserted sur true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Utiliser les options lors du remplacement du texte
doc.getRange().replace("text-to-replace", "new-text", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Cela vous permet d'exclure du remplacement le texte marqué comme inséré dans les modifications suivies.

## Remplacement du texte par HTML

Vous pouvez utiliser Aspose.Words pour Java pour remplacer du texte par du contenu HTML.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créer une instance FindReplaceOptions avec un rappel de remplacement personnalisé
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Utiliser les options lors du remplacement du texte
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

 Dans cet exemple, nous utilisons une coutume`ReplaceWithHtmlEvaluator` pour remplacer le texte par du contenu HTML.

## Remplacement du texte dans les en-têtes et les pieds de page

Vous pouvez rechercher et remplacer du texte dans les en-têtes et les pieds de page de votre document Word.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Obtenez la collection d'en-têtes et de pieds de page
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choisissez le type d'en-tête ou de pied de page dans lequel vous souhaitez remplacer le texte (par exemple, HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Créez une instance FindReplaceOptions et appliquez-la à la plage du pied de page
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Cela vous permet d'effectuer des remplacements de texte spécifiquement dans les en-têtes et les pieds de page.

## Affichage des modifications apportées aux ordres d'en-tête et de pied de page

Vous pouvez utiliser Aspose.Words pour afficher les modifications apportées aux ordres d'en-tête et de pied de page dans votre document.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Obtenez la première section
Section firstPageSection = doc.getFirstSection();

//Créez une instance FindReplaceOptions et appliquez-la à la plage du document
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Remplacer le texte qui affecte l'ordre des en-têtes et des pieds de page
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Cela vous permet de visualiser les changements liés aux ordres d'en-tête et de pied de page dans votre document.

## Remplacement du texte par des champs

Vous pouvez remplacer du texte par des champs en utilisant Aspose.Words pour Java.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créez une instance FindReplaceOptions et définissez un rappel de remplacement personnalisé pour les champs
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Utiliser les options lors du remplacement du texte
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

 Dans cet exemple, nous remplaçons le texte par des champs et spécifions le type de champ (par exemple,`FieldType.FIELD_MERGE_FIELD`).

## Remplacement par un évaluateur

Vous pouvez utiliser un évaluateur personnalisé pour déterminer le texte de remplacement de manière dynamique.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créez une instance FindReplaceOptions et définissez un rappel de remplacement personnalisé
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Utiliser les options lors du remplacement du texte
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Dans cet exemple, nous utilisons un évaluateur personnalisé (`MyReplaceEvaluator`) pour remplacer le texte.

## Remplacement par Regex

Aspose.Words pour Java vous permet de remplacer du texte à l'aide d'expressions régulières.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Utiliser des expressions régulières pour rechercher et remplacer du texte
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Dans cet exemple, nous utilisons un modèle d’expression régulière pour rechercher et remplacer du texte dans le document.

## Reconnaissance et substitutions dans les modèles de remplacement

Vous pouvez reconnaître et effectuer des substitutions dans les modèles de remplacement à l'aide d'Aspose.Words pour Java.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créez une instance FindReplaceOptions avec UseSubstitutions défini sur true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Utiliser les options lors du remplacement du texte par un motif
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Cela vous permet d'effectuer des substitutions dans les modèles de remplacement pour des remplacements plus avancés.

## Remplacement par une chaîne

Vous pouvez remplacer du texte par une simple chaîne en utilisant Aspose.Words pour Java.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Remplacer le texte par une chaîne
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Dans cet exemple, nous remplaçons « texte à remplacer » par « nouvelle chaîne » dans le document.

## Utilisation de la commande héritée

Vous pouvez utiliser l’ordre hérité lors de l’exécution d’opérations de recherche et de remplacement.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Créez une instance FindReplaceOptions et définissez UseLegacyOrder sur true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Utiliser les options lors du remplacement du texte
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Cela vous permet d'utiliser l'ordre hérité pour les opérations de recherche et de remplacement.

## Remplacement de texte dans un tableau

Vous pouvez rechercher et remplacer du texte dans les tableaux de votre document Word.

```java
// Charger le document
Document doc = new Document("your-document.docx");

// Obtenir une table spécifique (par exemple, la première table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//Utilisez FindReplaceOptions pour remplacer du texte dans le tableau
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Enregistrer le document modifié
doc.save("modified-document.docx");
```

Cela vous permet d'effectuer des remplacements de texte spécifiquement dans les tableaux.

## Conclusion

Aspose.Words pour Java offre des fonctionnalités complètes pour rechercher et remplacer du texte dans des documents Word. Que vous ayez besoin d'effectuer des remplacements de texte simples ou des opérations plus avancées à l'aide d'expressions régulières, de manipulations de champs ou d'évaluateurs personnalisés, Aspose.Words pour Java est là pour vous. Assurez-vous d'explorer la documentation complète et les exemples fournis par Aspose pour exploiter tout le potentiel de cette puissante bibliothèque Java.

## FAQ

### Comment télécharger Aspose.Words pour Java ?

 Vous pouvez télécharger Aspose.Words for Java à partir du site Web en visitant[ce lien](https://releases.aspose.com/words/java/).

### Puis-je utiliser des expressions régulières pour le remplacement de texte ?

Oui, vous pouvez utiliser des expressions régulières pour le remplacement de texte dans Aspose.Words pour Java. Cela vous permet d'effectuer des opérations de recherche et de remplacement plus avancées et plus flexibles.

### Comment puis-je ignorer le texte à l'intérieur des champs lors du remplacement ?

Pour ignorer le texte à l'intérieur des champs lors du remplacement, vous pouvez définir le`IgnoreFields` propriété de la`FindReplaceOptions` à`true`Cela garantit que le texte dans les champs, tels que les champs de fusion, est exclu du remplacement.

### Puis-je remplacer du texte dans les en-têtes et les pieds de page ?

 Oui, vous pouvez remplacer du texte dans les en-têtes et les pieds de page de votre document Word. Accédez simplement à l'en-tête ou au pied de page approprié et utilisez le`replace` méthode avec le désiré`FindReplaceOptions`.

### À quoi sert l’option UseLegacyOrder ?

 Le`UseLegacyOrder` option dans`FindReplaceOptions` vous permet d'utiliser l'ordre hérité lors de l'exécution d'opérations de recherche et de remplacement. Cela peut être utile dans certains scénarios où le comportement de l'ordre hérité est souhaité.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
