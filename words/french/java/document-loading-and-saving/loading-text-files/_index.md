---
title: Chargement de fichiers texte avec Aspose.Words pour Java
linktitle: Chargement de fichiers texte avec
second_title: API de traitement de documents Java Aspose.Words
description: Exploitez la puissance d'Aspose.Words pour Java. Apprenez à charger des documents texte, à gérer des listes, à gérer des espaces et à contrôler la direction du texte.
weight: 13
url: /fr/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chargement de fichiers texte avec Aspose.Words pour Java


## Introduction au chargement de fichiers texte avec Aspose.Words pour Java

Dans ce guide, nous verrons comment charger des fichiers texte à l'aide d'Aspose.Words pour Java et les manipuler comme des documents Word. Nous aborderons divers aspects tels que la détection des listes, la gestion des espaces et le contrôle de la direction du texte.

## Étape 1 : Détection des listes

Pour charger un document texte et détecter des listes, vous pouvez suivre ces étapes :

```java
// Créez un document en texte brut sous la forme d’une chaîne avec des parties pouvant être interprétées comme des listes.
// Lors du chargement, les trois premières listes seront toujours détectées par Aspose.Words,
// et des objets de liste seront créés pour eux après le chargement.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
//La quatrième liste, avec un espace entre le numéro de liste et le contenu des éléments de la liste,
// ne sera détecté comme une liste que si « DetectNumberingWithWhitespaces » dans un objet LoadOptions est défini sur true,
// pour éviter que les paragraphes commençant par des chiffres soient détectés par erreur comme des listes.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Chargez le document tout en appliquant LoadOptions comme paramètre et vérifiez le résultat.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 Ce code montre comment charger un document texte avec différents formats de liste et utiliser le`DetectNumberingWithWhitespaces` option pour détecter correctement les listes.

## Étape 2 : Options de gestion des espaces

Pour contrôler les espaces de début et de fin lors du chargement d'un document texte, vous pouvez utiliser le code suivant :

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

 Dans cet exemple, nous chargeons un document texte et coupons les espaces de début et de fin à l'aide de`TxtLeadingSpacesOptions.TRIM` et`TxtTrailingSpacesOptions.TRIM`.

## Étape 3 : Contrôler la direction du texte

Pour spécifier la direction du texte lors du chargement d'un document texte, vous pouvez utiliser le code suivant :

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Ce code définit la direction du document sur la détection automatique (`DocumentDirection.AUTO`et charge un document texte avec du texte hébreu. Vous pouvez ajuster la direction du document selon vos besoins.

## Code source complet pour le chargement de fichiers texte avec Aspose.Words pour Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Créez un document en texte brut sous la forme d’une chaîne avec des parties pouvant être interprétées comme des listes.
	// Lors du chargement, les trois premières listes seront toujours détectées par Aspose.Words,
	// et des objets de liste seront créés pour eux après le chargement.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// La quatrième liste, avec un espace entre le numéro de liste et le contenu des éléments de la liste,
	// ne sera détecté comme une liste que si « DetectNumberingWithWhitespaces » dans un objet LoadOptions est défini sur true,
	// pour éviter que les paragraphes commençant par des chiffres soient détectés par erreur comme des listes.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Chargez le document tout en appliquant LoadOptions comme paramètre et vérifiez le résultat.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Conclusion

Dans ce guide, nous avons découvert comment charger des fichiers texte à l'aide d'Aspose.Words pour Java, détecter des listes, gérer des espaces et contrôler la direction du texte. Ces techniques vous permettent de manipuler efficacement des documents texte dans vos applications Java.

## FAQ

### Qu'est-ce que Aspose.Words pour Java ?

Aspose.Words for Java est une puissante bibliothèque de traitement de documents qui permet aux développeurs de créer, de manipuler et de convertir des documents Word par programmation dans des applications Java. Elle offre une large gamme de fonctionnalités pour travailler avec du texte, des tableaux, des images et d'autres éléments de document.

### Comment puis-je démarrer avec Aspose.Words pour Java ?

Pour démarrer avec Aspose.Words pour Java, suivez ces étapes :
1. Téléchargez et installez la bibliothèque Aspose.Words pour Java.
2.  Consultez la documentation à l'adresse[Référence de l'API Aspose.Words pour Java](https://reference.aspose.com/words/java/) pour des informations détaillées et des exemples.
3. Explorez l'exemple de code et les didacticiels pour apprendre à utiliser efficacement la bibliothèque.

### Comment charger un document texte à l'aide d'Aspose.Words pour Java ?

 Pour charger un document texte à l'aide d'Aspose.Words pour Java, vous pouvez utiliser le`TxtLoadOptions` classe et la`Document` classe. Assurez-vous de spécifier les options appropriées pour la gestion des espaces et la direction du texte selon vos besoins. Reportez-vous au guide étape par étape de cet article pour un exemple détaillé.

### Puis-je convertir un document texte chargé vers d’autres formats ?

 Oui, Aspose.Words pour Java vous permet de convertir un document texte chargé en différents formats, notamment DOCX, PDF, etc. Vous pouvez utiliser le`Document` classe pour effectuer des conversions. Consultez la documentation pour des exemples de conversion spécifiques.

### Comment gérer les espaces dans les documents texte chargés ?

 Vous pouvez contrôler la manière dont les espaces de début et de fin sont gérés dans les documents texte chargés à l'aide de`TxtLoadOptions` Des options comme`TxtLeadingSpacesOptions` et`TxtTrailingSpacesOptions`vous permettent de couper ou de conserver les espaces selon vos besoins. Reportez-vous à la section « Options de gestion des espaces » de ce guide pour un exemple.

### Quelle est l’importance de la direction du texte dans Aspose.Words pour Java ?

L'orientation du texte est essentielle pour les documents contenant des écritures ou des langues mixtes, telles que l'hébreu ou l'arabe. Aspose.Words pour Java fournit des options permettant de spécifier l'orientation du texte, garantissant ainsi un rendu et un formatage corrects du texte dans ces langues. La section « Contrôle de l'orientation du texte » de ce guide montre comment définir l'orientation du texte.

### Où puis-je trouver plus de ressources et d'assistance pour Aspose.Words pour Java ?

 Pour des ressources, de la documentation et de l'assistance supplémentaires, visitez le[Documentation Aspose.Words pour Java](https://reference.aspose.com/words/java/)Vous pouvez également participer aux forums de la communauté Aspose.Words ou contacter le support Aspose pour obtenir de l'aide sur des problèmes ou des demandes spécifiques.

### Aspose.Words pour Java est-il adapté aux projets commerciaux ?

Oui, Aspose.Words for Java convient aussi bien aux projets personnels qu'aux projets commerciaux. Il propose des options de licence pour s'adapter à divers scénarios d'utilisation. Assurez-vous de consulter les conditions de licence et les tarifs sur le site Web d'Aspose pour choisir la licence appropriée pour votre projet.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
