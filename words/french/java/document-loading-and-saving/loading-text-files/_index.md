---
date: 2025-12-27
description: Apprenez comment définir la direction, charger des fichiers txt, supprimer
  les espaces et convertir des txt en docx en utilisant Aspose.Words pour Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Comment définir la direction et charger des fichiers texte avec Aspose.Words
  pour Java
url: /fr/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir la direction et charger des fichiers texte avec Aspose.Words pour Java

## Introduction au chargement de fichiers texte avec Aspose.Words pour Java

Dans ce guide, vous découvrirez **comment définir la direction** lors du chargement de documents texte brut et verrez des méthodes pratiques pour **charger des txt**, **supprimer les espaces**, et **convertir des txt en docx** à l’aide d’Aspose.Words pour Java. Que vous construisiez un service de conversion de documents ou que vous ayez besoin d’un contrôle fin sur la détection des listes, ce tutoriel vous accompagne à chaque étape avec des explications claires et du code prêt à l’exécution.

## Réponses rapides
- **Comment définir la direction du texte pour un fichier TXT chargé ?** Utilisez `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` ou spécifiez `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Aspose.Words peut‑il détecter les listes numérotées dans du texte brut ?** Oui – activez `DetectNumberingWithWhitespaces` dans `TxtLoadOptions`.
- **Comment supprimer les espaces en début et en fin de ligne ?** Définissez `TxtLeadingSpacesOptions.TRIM` et `TxtTrailingSpacesOptions.TRIM`.
- **Est‑il possible de convertir un fichier TXT en DOCX en une seule ligne ?** Chargez le TXT avec `TxtLoadOptions` et appelez `Document.save("output.docx")`.
- **Quelle version de Java est requise ?** Java 8+ suffit pour Aspose.Words 24.x.

## Qu’est‑ce que « comment définir la direction » dans Aspose.Words ?

Lorsqu’un fichier texte contient des scripts de droite à gauche (par ex., hébreu ou arabe), la bibliothèque doit connaître l’ordre de lecture. L’énumération `DocumentDirection` vous permet de **définir la direction** manuellement ou de laisser Aspose la détecter automatiquement, garantissant une mise en page correcte et un formatage bidi.

## Pourquoi utiliser Aspose.Words pour charger des fichiers TXT ?

- **Détection précise des listes** – gère les listes numérotées, à puces et délimitées par des espaces.
- **Gestion fine des espaces** – supprime ou conserve les espaces en début et en fin.
- **Détection automatique de la direction du texte** – idéal pour les documents multilingues.
- **Conversion en une étape** – chargez un `.txt` et enregistrez-le en `.docx`, `.pdf` ou tout autre format supporté.

## Prérequis
- Java 8 ou version supérieure.
- Bibliothèque Aspose.Words pour Java (ajoutez la dépendance Maven/Gradle ou le JAR à votre projet).
- Connaissances de base des flux d’E/S Java.

## Guide étape par étape

### Étape 1 : Détection des listes (comment charger txt)

Pour charger un document texte et détecter automatiquement les listes, créez une instance de `TxtLoadOptions` et activez la détection des listes. Le code ci‑dessous montre plusieurs styles de listes et active la numérotation sensible aux espaces.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Astuce :** Si vous n’avez besoin que de la détection de listes de base, vous pouvez ignorer l’option d’espaces – Aspose reconnaîtra toujours les modèles standards `1.` et `1)`.

### Étape 2 : Options de gestion des espaces (comment supprimer les espaces)

Les espaces en début et en fin de ligne provoquent souvent des problèmes de formatage. Utilisez `TxtLeadingSpacesOptions` et `TxtTrailingSpacesOptions` pour contrôler ce comportement.

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

> **Pourquoi c’est important :** Supprimer les espaces évite les indentations indésirables dans le DOCX résultant, rendant le document propre sans post‑traitement manuel.

### Étape 3 : Contrôle de la direction du texte (comment définir la direction)

Pour les langues de droite à gauche, définissez la direction du document avant le chargement. L’exemple ci‑dessous charge un fichier texte hébreu et affiche le drapeau bidi pour confirmer la direction.

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

> **Erreur fréquente :** Oublier de définir `DocumentDirection` peut entraîner un texte arabe/hébreu illisible où les caractères apparaissent dans le mauvais ordre.

## Code source complet pour charger des fichiers texte avec Aspose.Words pour Java

Ci‑dessous se trouve le code complet, prêt à l’exécution, qui combine la détection des listes, la gestion des espaces et le contrôle de la direction. Vous pouvez le copier‑coller dans une seule classe et exécuter les trois méthodes de test individuellement.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Problèmes courants et solutions

| Problème | Cause | Solution |
|----------|-------|----------|
| Listes non détectées | `DetectNumberingWithWhitespaces` laissé à `false` pour les listes délimitées par des espaces | Activez `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Indentation supplémentaire après le chargement | Les espaces en début de ligne ont été conservés | Définissez `TxtLeadingSpacesOptions.TRIM` |
| Le texte hébreu apparaît inversé | Direction du document non définie ou définie à `LEFT_TO_RIGHT` | Utilisez `DocumentDirection.AUTO` ou `RIGHT_TO_LEFT` |
| Le DOCX de sortie est vide | Le flux d’entrée n’a pas été réinitialisé avant le deuxième chargement | Re‑créez `ByteArrayInputStream` pour chaque appel de chargement |

## Questions fréquemment posées

### Q : Qu’est‑ce qu’Aspose.Words pour Java ?
A : Aspose.Words pour Java est une bibliothèque puissante de traitement de documents qui permet aux développeurs de créer, manipuler et convertir des documents Word de manière programmatique dans des applications Java. Elle prend en charge un large éventail de fonctionnalités, du simple chargement de texte à la mise en forme et à la conversion complexes.

### Q : Comment commencer avec Aspose.Words pour Java ?
A : 1. Téléchargez et installez la bibliothèque Aspose.Words pour Java. 2. Consultez la documentation à l’adresse [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) pour des informations détaillées et des exemples. 3. Explorez le code d’exemple et les tutoriels pour apprendre à utiliser la bibliothèque efficacement.

### Q : Comment charger un document texte avec Aspose.Words pour Java ?
A : Utilisez la classe `TxtLoadOptions` avec le constructeur `Document`. Spécifiez des options telles que la détection des listes, la gestion des espaces ou la direction du texte comme démontré dans les sections étape par étape ci‑dessus.

### Q : Puis‑je convertir un document texte chargé en d’autres formats ?
A : Oui. Après avoir chargé le fichier TXT dans un objet `Document`, appelez `doc.save("output.pdf")`, `doc.save("output.docx")` ou tout autre format supporté.

### Q : Comment gérer les espaces dans les documents texte chargés ?
A : Contrôlez les espaces en début et en fin de ligne avec `TxtLeadingSpacesOptions` et `TxtTrailingSpacesOptions`. Définissez-les sur `TRIM` pour supprimer les espaces indésirables, ou sur `PRESERVE` si vous devez conserver l’espacement original.

### Q : Quelle est l’importance de la direction du texte dans Aspose.Words pour Java ?
A : La direction du texte garantit le rendu correct des scripts de droite à gauche (hébreu, arabe, etc.). En définissant `DocumentDirection`, vous assurez que le texte bidi s’affiche correctement dans le document résultant.

### Q : Où trouver plus de ressources et d’assistance pour Aspose.Words pour Java ?
A : Visitez la [Documentation Aspose.Words pour Java](https://reference.aspose.com/words/java/) pour les références API, des exemples de code et des guides détaillés. Vous pouvez également rejoindre les forums de la communauté Aspose ou contacter le support Aspose pour des questions spécifiques.

### Q : Aspose.Words pour Java convient‑il aux projets commerciaux ?
A : Oui. Elle propose des options de licence pour un usage personnel et commercial. Consultez les conditions de licence sur le site Aspose afin de choisir le plan adapté à votre projet.

## Conclusion
Vous disposez maintenant d’une boîte à outils complète pour **charger des fichiers txt**, **détecter les listes**, **supprimer les espaces** et **définir la direction** lors de la conversion de texte brut en documents Word riches avec Aspose.Words pour Java. Appliquez ces modèles pour automatiser les flux de travail documentaires, améliorer la prise en charge multilingue et garantir un résultat propre et professionnel à chaque fois.

---

**Dernière mise à jour :** 2025-12-27  
**Testé avec :** Aspose.Words pour Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}