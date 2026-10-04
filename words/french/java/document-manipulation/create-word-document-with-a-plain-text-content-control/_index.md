---
category: general
date: 2026-10-04
description: Créer un document Word en Java qui inclut un contrôle de contenu texte
  simple et un espace réservé. Apprenez comment ajouter un espace réservé à la balise
  et comment insérer un sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: fr
lastmod: 2026-10-04
og_description: Créer un document Word avec un contrôle de contenu texte brut et un
  espace réservé. Ce tutoriel montre comment ajouter un espace réservé à la balise
  et comment insérer un sdt à l’aide d’Aspose.Words pour Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Créer un document Word avec contrôle de contenu – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Créer un document Word avec un contrôle de contenu texte brut
url: /fr/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec un contrôle de contenu texte brut

Si vous devez **créer un document Word** contenant une zone modifiable par l'utilisateur, un contrôle de contenu texte brut est l'approche la plus fiable. Ce tutoriel montre exactement comment insérer une balise de document structuré (SDT), définir un texte de substitution, et enregistrer le résultat sous forme de **docx avec texte de substitution**. Vous verrez un exemple complet et exécutable en Java qui fonctionne avec Aspose.Words for Java 23.8.

Le guide couvre toutes les prérequis, explique pourquoi chaque appel d'API est important, et fournit des astuces pour gérer les cas limites tels que les textes de substitution multilingues ou les balises imbriquées. À la fin, vous pourrez générer un fichier Word qui invite les utilisateurs à « Enter text… » directement dans le document.

## Prérequis

Avant de commencer, assurez‑vous d'avoir :

* Java 17 (ou version ultérieure) installé et configuré dans votre PATH.  
* Maven 3.8+ pour gérer les dépendances.  
* Une licence Aspose.Words for Java (l'évaluation fonctionne pour les tests).  
* Un IDE de développement (IntelliJ IDEA, Eclipse ou VS Code).

Ajoutez Aspose.Words à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Créer un document Word avec un contrôle de contenu texte brut

Le flux de travail principal se compose de quatre étapes logiques. Chaque étape est encapsulée dans une méthode clairement nommée afin que vous puissiez réutiliser la logique dans des projets plus importants.

### Étape 1 : Initialiser le document et le constructeur

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Pourquoi c'est important :** `Document` représente le fichier Word en mémoire. `DocumentBuilder` est l'API fluide qui vous permet d'insérer des paragraphes, des tableaux et des SDT. Commencer avec un document vide garantit que le texte de substitution apparaît dès le tout début, ce qui est utile pour les modèles.

### Étape 2 : Insérer une balise de document structuré texte brut (SDT)

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Pourquoi c'est important :** `StructuredDocumentTagType.PLAIN_TEXT` crée un contrôle de contenu qui n'accepte que des caractères simples, évitant ainsi tout formatage accidentel. L'appel `setPlaceholderName` remplit le texte d'indice gris que les utilisateurs voient avant de taper — c'est l'opération **add placeholder to tag** qui donne au document l'apparence d'un formulaire.

### Étape 3 : Ajouter du contenu ordinaire après le SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Pourquoi c'est important :** Ajouter du contenu après le contrôle vérifie que le SDT ne consomme pas tout le flux du document. Cela montre également comment mélanger des balises structurées avec des paragraphes ordinaires, une exigence courante lors de la création de modèles.

### Étape 4 : Enregistrer le fichier résultant

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Pourquoi c'est important :** La méthode `save` écrit le modèle en mémoire dans un fichier physique **docx avec texte de substitution**. Le fichier généré peut être ouvert dans Microsoft Word, LibreOffice ou toute bibliothèque supportant le format OpenXML.

## Code source complet

Assembler les pièces vous donne un programme autonome que vous pouvez compiler et exécuter :

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Résultat attendu

Exécuter le programme crée `SdtDemo.docx`. Ouvrir le fichier dans Word affiche :

* Un texte de substitution gris « Enter text… » à l'intérieur d'un contrôle de contenu texte brut nommé **MyTag**.  
* La ligne **After SDT** immédiatement sous le contrôle.

Le texte de substitution disparaît dès que l'utilisateur tape, préservant le formatage original.

## Variantes courantes et cas limites

| Scénario | Modification recommandée |
|----------|--------------------------|
| **Texte de substitution multilingue** | Utilisez des caractères Unicode dans `setPlaceholderName`, par exemple `sdt.setPlaceholderName("Введите текст…");`. |
| **Contrôles de contenu imbriqués** | Insérez un deuxième SDT à l'intérieur du premier en appelant `builder.moveTo(sdt.getParagraph());` avant le second `insertStructuredDocumentTag`. |
| **Contrôle en lecture seule** | Appelez `sdt.setLockContentControl(true);` pour empêcher les utilisateurs de supprimer la balise. |
| **Texte enrichi au lieu de texte brut** | Remplacez `StructuredDocumentTagType.PLAIN_TEXT` par `StructuredDocumentTagType.RICH_TEXT`. |
| **Enregistrement vers un flux** | Utilisez `doc.save(OutputStream, SaveFormat.DOCX);` lorsque vous devez envoyer le fichier via HTTP. |

## Astuces professionnelles

* **Réutiliser les ID de balise** – Si vous générez de nombreux documents à partir du même modèle, conservez le nom de balise (`"MyTag"`) cohérent afin que le traitement en aval (par ex., publipostage) puisse le localiser de manière fiable.  
* **Performance** – Pour les grands modèles, créez le `DocumentBuilder` une seule fois et réutilisez‑le ; insérer de nombreux SDT dans une boucle est plus rapide que de recréer le constructeur à chaque itération.  
* **Tests** – Après avoir généré le DOCX, vérifiez programmatique que le texte de substitution existe avec `doc.getRange().getStructuredDocumentTags().getCount()`.

## Conclusion

Vous savez maintenant comment **créer un document Word** contenant un **contrôle de contenu texte brut** avec un texte de substitution personnalisé, produisant ainsi efficacement un **docx avec texte de substitution** prêt à recevoir les saisies de l'utilisateur. L'exemple montre le cycle complet depuis l'initialisation du document, **how to insert sdt**, **add placeholder to tag**, l'ajout de contenu ordinaire, et enfin l'enregistrement du fichier.

### Prochaines étapes

* Explorez **how to insert sdt** à l'intérieur des tableaux pour des mises en page de type formulaire.  
* Combinez cette technique avec la fusion de **docx with placeholder** pour créer des générateurs de rapports automatisés.  
* Expérimentez d'autres types de contrôles (`RICH_TEXT`, `CHECKBOX`) pour créer des formulaires Word plus riches.

N'hésitez pas à adapter le code à votre propre moteur de modèles, et partagez vos résultats dans les commentaires !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d'API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Créer un document Word Java – Ajouter une forme rectangulaire avec effet d'ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Comment créer des documents PDF avec Aspose.Words for Java | API de traitement de documents](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}