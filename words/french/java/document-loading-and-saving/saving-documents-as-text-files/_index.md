---
title: Enregistrer des documents sous forme de fichiers texte dans Aspose.Words pour Java
linktitle: Enregistrer des documents sous forme de fichiers texte
second_title: API de traitement de documents Java Aspose.Words
description: Découvrez comment enregistrer des documents sous forme de fichiers texte dans Aspose.Words pour Java. Suivez notre guide étape par étape avec des exemples de code Java.
weight: 24
url: /fr/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer des documents sous forme de fichiers texte dans Aspose.Words pour Java


## Introduction à l'enregistrement de documents sous forme de fichiers texte dans Aspose.Words pour Java

Dans ce didacticiel, nous allons découvrir comment enregistrer des documents sous forme de fichiers texte à l'aide de la bibliothèque Aspose.Words pour Java. Aspose.Words est une API Java puissante pour travailler avec des documents Word et propose diverses options pour enregistrer des documents dans différents formats, y compris du texte brut. Nous aborderons les étapes à suivre pour y parvenir et fournirons un exemple de code Java en cours de route.

## Prérequis

Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :

- Kit de développement Java (JDK) installé sur votre système.
-  Bibliothèque Aspose.Words pour Java intégrée à votre projet. Vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/java/).
- Connaissances de base de la programmation Java.

## Étape 1 : Créer un document

Pour enregistrer un document sous forme de fichier texte, nous devons d'abord créer un document à l'aide d'Aspose.Words. Voici un extrait de code Java simple pour créer un document avec du contenu :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Dans ce code, nous créons un nouveau document et y ajoutons du texte, y compris du texte dans différentes langues.

## Étape 2 : définir les options d’enregistrement du texte

Ensuite, nous devons définir les options d'enregistrement de texte qui spécifient comment le document doit être enregistré en tant que fichier texte. Nous pouvons configurer divers paramètres tels que l'ajout de marques bidi, l'indentation de liste, etc. Examinons deux exemples :

### Exemple 1 : Ajout de marques Bidi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 Dans cet exemple, nous créons un`TxtSaveOptions` objet et définir le`AddBidiMarks`propriété à`true` pour inclure les marques bidi dans la sortie de texte.

### Exemple 2 : Utilisation du caractère de tabulation pour l'indentation de la liste

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Ici, nous configurons les options d’enregistrement pour utiliser un caractère de tabulation pour l’indentation de la liste avec un compte de 1.

## Étape 3 : Enregistrer le document au format texte

Maintenant que nous avons défini les options d'enregistrement du texte, nous pouvons enregistrer le document sous forme de fichier texte. Le code suivant montre comment procéder :

```java
doc.save("output.txt", saveOptions);
```

 Remplacer`"output.txt"` avec le chemin du fichier souhaité où vous souhaitez enregistrer le fichier texte.

## Code source complet pour l'enregistrement de documents sous forme de fichiers texte dans Aspose.Words pour Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Créez une liste avec trois niveaux d’indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Créez une liste avec trois niveaux d’indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Conclusion

Dans ce didacticiel, nous avons appris à enregistrer des documents sous forme de fichiers texte dans Aspose.Words pour Java. Nous avons couvert les étapes de création d'un document, défini les options d'enregistrement de texte et enregistré le document au format texte. Aspose.Words offre une grande flexibilité en matière d'enregistrement de documents, vous permettant d'adapter la sortie à vos besoins spécifiques.

## FAQ

### Comment ajouter des marques bidi à la sortie de texte ?

 Pour ajouter des marques bidi à la sortie de texte, définissez le`AddBidiMarks` propriété de`TxtSaveOptions` à`true`. Par exemple:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Puis-je personnaliser le caractère d’indentation de la liste ?

 Oui, vous pouvez personnaliser le caractère d'indentation de la liste en configurant le`ListIndentation` propriété de`TxtSaveOptions`Par exemple, pour utiliser un caractère de tabulation pour l'indentation d'une liste, vous pouvez procéder comme suit :

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words pour Java est-il adapté à la gestion de texte multilingue ?

Oui, Aspose.Words pour Java est adapté à la gestion de textes multilingues. Il prend en charge plusieurs langues et encodages de caractères, ce qui en fait un choix polyvalent pour travailler avec des documents dans différentes langues.

### Comment puis-je accéder à plus de documentation et de ressources pour Aspose.Words pour Java ?

 Vous pouvez trouver une documentation et des ressources complètes pour Aspose.Words pour Java sur le site Web de documentation Aspose :[Documentation Aspose.Words pour Java](https://reference.aspose.com/words/java/).

### Où puis-je télécharger Aspose.Words pour Java ?

 Vous pouvez télécharger la bibliothèque Aspose.Words pour Java à partir du site Web d'Aspose :[Télécharger Aspose.Words pour Java](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
