---
"description": "Apprenez à cloner et combiner des documents dans Aspose.Words pour Java. Guide étape par étape avec exemples de code source."
"linktitle": "Clonage et combinaison de documents"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Clonage et combinaison de documents dans Aspose.Words pour Java"
"url": "/fr/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Clonage et combinaison de documents dans Aspose.Words pour Java


## Introduction au clonage et à la combinaison de documents dans Aspose.Words pour Java

Dans ce tutoriel, nous découvrirons comment cloner et combiner des documents avec Aspose.Words pour Java. Nous aborderons différents scénarios, notamment le clonage d'un document, l'insertion de documents aux points de remplacement, les signets et les opérations de publipostage.

## Étape 1 : Clonage d'un document

Pour cloner un document dans Aspose.Words pour Java, vous pouvez utiliser le `deepClone()` méthode. Voici un exemple simple :

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Ce code créera un clone profond du document d'origine et l'enregistrera en tant que nouveau fichier.

## Étape 2 : Insertion de documents aux points de remplacement

Vous pouvez insérer des documents à des emplacements spécifiques dans un autre document. Voici comment procéder :

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Dans cet exemple, nous utilisons un `FindReplaceOptions` objet pour spécifier un gestionnaire de rappel pour le remplacement. `InsertDocumentAtReplaceHandler` la classe gère la logique d'insertion.

## Étape 3 : Insérer des documents dans les signets

Pour insérer un document à un signet spécifique dans un autre document, vous pouvez utiliser le code suivant :

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Ici, nous trouvons le signet par nom et utilisons le `insertDocument` méthode pour insérer le contenu du `subDoc` document à l'emplacement du signet.

## Étape 4 : Insertion de documents lors du publipostage

Vous pouvez insérer des documents lors d'une opération de publipostage dans Aspose.Words pour Java. Voici comment :

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

Dans cet exemple, nous définissons un rappel de fusion de champs à l'aide de `InsertDocumentAtMailMergeHandler` classe pour gérer l'insertion du document spécifié par le champ « Document_1 ».

## Conclusion

Le clonage et la combinaison de documents dans Aspose.Words pour Java peuvent être réalisés grâce à diverses techniques. Que vous ayez besoin de cloner un document, d'insérer du contenu aux points de remplacement, des signets ou lors d'un publipostage, Aspose.Words offre de puissantes fonctionnalités pour manipuler vos documents en toute fluidité.

## FAQ

### Comment cloner un document dans Aspose.Words pour Java ?

Vous pouvez cloner un document dans Aspose.Words pour Java en utilisant le `deepClone()` méthode. Voici un exemple :

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Comment puis-je insérer un document dans un signet ?

Pour insérer un document dans un signet dans Aspose.Words pour Java, vous pouvez rechercher le signet par son nom, puis utiliser le `insertDocument` Méthode pour insérer le contenu. Voici un exemple :

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Comment insérer des documents lors du publipostage dans Aspose.Words pour Java ?

Vous pouvez insérer des documents lors d'un publipostage dans Aspose.Words pour Java en définissant un rappel de fusion de champs et en spécifiant le document à insérer. Voici un exemple :

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

Dans cet exemple, le `InsertDocumentAtMailMergeHandler` la classe gère la logique d'insertion du « DocumentField » lors du publipostage.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}