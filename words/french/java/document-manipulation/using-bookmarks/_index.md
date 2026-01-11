---
date: 2026-01-11
description: Apprenez comment afficher/masquer les signets et créer des signets Java
  en utilisant Aspose.Words for Java pour une navigation et une manipulation efficaces
  des documents.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Afficher/Masquer les signets avec Aspose.Words pour Java
url: /fr/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Afficher/Masquer les Signets avec Aspose.Words for Java

## Introduction à l’utilisation des signets dans Aspose.Words for Java

Les signets sont une fonctionnalité puissante d’Aspose.Words for Java qui vous permet **de créer bookmark java**, de naviguer vers un contenu spécifique, et même **d’afficher masquer les signets** lorsque vous devez générer différentes versions de document. Dans ce guide pas à pas, nous parcourrons la création, l’accès, la mise à jour, la copie et le basculement de la visibilité des signets, vous offrant un contrôle complet sur la manipulation du document.

## Réponses rapides
- **Quel est le but principal des signets ?** Marquer et récupérer ultérieurement des parties spécifiques d’un document.  
- **Puis‑je masquer les marqueurs de signet dans le résultat final ?** Oui — utilisez l’API show/hide pour basculer leur visibilité.  
- **Comment créer un signet à l’intérieur d’une cellule de tableau ?** Démarrez et terminez le signet avec `DocumentBuilder` pendant que le curseur se trouve dans la cellule.  
- **Est‑il possible de copier du texte signeté vers un autre document ?** Absolument — utilisez `NodeImporter` pour conserver le formatage.  
- **Quelle version d’Aspose.Words est requise ?** Toute version récente ; le code fonctionne avec la dernière build 2026.

## Qu’est‑ce que « show hide bookmarks » ?

La fonctionnalité **show hide bookmarks** vous permet d’afficher ou de masquer programmatiquement les délimiteurs de signet dans le document enregistré. Cela est utile lorsque vous souhaitez générer une sortie épurée pour les utilisateurs finaux tout en conservant les données de signet pour le traitement interne.

## Pourquoi utiliser les signets dans l’automatisation de documents Java ?

- **Navigation efficace** – Accédez directement aux sections sans parcourir tout le fichier.  
- **Génération de contenu dynamique** – Insérez, remplacez ou supprimez du texte lié à un signet.  
- **Visibilité conditionnelle** – Affichez ou masquez les marqueurs de signet selon les préférences de l’utilisateur ou le format de sortie.  
- **Réutilisabilité** – Copiez des fragments signetés entre documents tout en préservant les styles.

## Prérequis
- Java Development Kit (JDK) 8 ou supérieur.  
- Bibliothèque Aspose.Words for Java ajoutée à votre projet (Maven/Gradle ou JAR).  
- Familiarité de base avec les classes `Document` et `DocumentBuilder`.

## Guide étape par étape

### Étape 1 : Créer un signet (create bookmark java)

Pour ajouter un signet, vous le démarrez, écrivez le contenu, puis le terminez. Cet exemple crée un signet simple nommé **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Étape 2 : Accéder aux signets (access bookmarks java)

Les signets peuvent être récupérés soit par leur indice zéro‑based, soit par leur nom. Le code ci‑dessous montre les deux approches.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Étape 3 : Mettre à jour les données du signet (update bookmark text)

Vous pouvez renommer un signet ou remplacer son texte. Ceci est pratique lorsque le document sous‑jacent change.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Étape 4 : Travailler avec le texte signeté (copy bookmarked text)

Copier un fragment signeté vers un autre document tout en conservant le formatage d’origine est simple avec `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Étape 5 : Afficher et masquer les signets (show hide bookmarks)

L’extrait suivant montre comment masquer les marqueurs d’un signet dans le fichier enregistré. Passez `false` pour masquer, `true` pour afficher.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Étape 6 : Démêler les signets de lignes (bookmark table cell)

Lorsque les signets s’étendent sur plusieurs lignes de tableau, ils peuvent se mêler. Les méthodes utilitaires ci‑dessous les démêlent et vous permettent de supprimer une ligne spécifique par son signet.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Problèmes courants et solutions

| Problème | Solution |
|----------|----------|
| **Signet non trouvé** | Vérifiez que le nom du signet correspond exactement (sensible à la casse) et que le document a été enregistré après la création. |
| **Le texte copié perd le formatage** | Utilisez `ImportFormatMode.KEEP_SOURCE_FORMATTING` avec `NodeImporter` comme indiqué à l’Étape 4. |
| **Afficher/masquer n’affecte pas la sortie** | Assurez‑vous d’appeler `showHideBookmarkedContent` **avant** d’enregistrer le document. |
| **Le signet dans une cellule de tableau est ignoré** | Placez les appels start/end alors que le curseur du builder est à l’intérieur de la cellule cible. |

## FAQ

**Q : Comment créer un signet dans une cellule de tableau ?**  
R : Utilisez `DocumentBuilder` pour déplacer le curseur dans la cellule désirée, puis appelez `startBookmark` et `endBookmark` autour du contenu de la cellule.

**Q : Puis‑je copier un signet vers un autre document ?**  
R : Oui — utilisez la classe `NodeImporter` (voir Étape 4) pour importer le nœud signeté tout en préservant son formatage d’origine.

**Q : Comment supprimer une ligne par son signet ?**  
R : Localisez d’abord la ligne contenant le signet, puis appelez `remove` sur le nœud de ligne (comme démontré à l’Étape 6).

**Q : Quels sont les cas d’utilisation courants des signets ?**  
R : Génération d’une table des matières, extraction de sections spécifiques pour des rapports, et automatisation de l’assemblage de documents en fonction des sélections de l’utilisateur.

**Q : Où puis‑je trouver plus d’informations sur Aspose.Words for Java ?**  
R : Pour une documentation détaillée et les téléchargements, consultez [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Dernière mise à jour :** 2026-01-11  
**Testé avec :** Aspose.Words for Java 24.11 (2026)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}