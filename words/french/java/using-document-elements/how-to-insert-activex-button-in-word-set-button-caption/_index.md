---
category: general
date: 2026-07-26
description: Comment insérer un bouton ActiveX dans un document Word avec Aspose.Words
  – apprenez à définir la légende, la position et la taille du bouton en quelques
  lignes seulement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: fr
lastmod: 2026-07-26
og_description: Comment insérer un bouton ActiveX dans un document Word avec Aspose.Words.
  Suivez ce tutoriel étape par étape pour définir la légende du bouton, sa position
  et sa taille.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Comment insérer un bouton ActiveX dans Word – Guide rapide
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Comment insérer un bouton ActiveX dans Word – Définir la légende du bouton
url: /fr/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment insérer un bouton ActiveX dans Word – Définir la légende du bouton

Vous vous êtes déjà demandé **comment insérer ActiveX** des contrôles dans un fichier Word sans ouvrir l’interface ? Vous n’êtes pas le seul. Dans de nombreuses applications d’entreprise, vous avez besoin d’un bouton cliquable qui exécute une macro, et le faire de façon programmatique fait gagner des heures. Ce guide vous montre exactement **comment insérer ActiveX** un CommandButton à l’aide d’Aspose.Words for Java, et—oui—comment **définir la légende du bouton** afin que l’utilisateur sache sur quoi cliquer.

Nous parcourrons l’ensemble du processus : configuration de la bibliothèque, création d’un nouveau document, insertion du bouton, ajustement de sa taille et de sa position, attribution d’une légende conviviale, puis enregistrement du fichier. À la fin, vous disposerez d’un `.docx` exécutable qui s’ouvre dans Word avec un bouton ActiveX pleinement fonctionnel prêt à déclencher votre macro.

---

## Ce que vous apprendrez

- Installer et référencer Aspose.Words dans un projet Java.  
- Créer un nouveau `Document` et `DocumentBuilder`.  
- **Insérer ActiveX** contrôle CommandButton avec une seule ligne de code.  
- **Définir la légende du bouton**, ajuster sa position et définir ses dimensions.  
- Enregistrer le document et l'ouvrir dans Word pour voir le résultat.

Aucune expérience préalable avec ActiveX n’est requise ; il suffit de connaissances de base en Java et d’une copie d’Aspose.Words.

---

## Prérequis

- Java 8 ou version supérieure installé sur votre machine.  
- Maven ou Gradle pour la gestion des dépendances (nous montrerons l’extrait Maven).  
- Une copie sous licence ou d'évaluation d'**Aspose.Words for Java** (l’essai gratuit fonctionne bien pour cette démonstration).  
- Microsoft Word (toute version récente) pour tester le fichier généré.

---

## Étape 1 : Configurer Aspose.Words dans votre projet

Tout d’abord, ajoutez la dépendance Aspose.Words. Si vous utilisez Maven, insérez ceci dans votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Les utilisateurs de Gradle peuvent ajouter :

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Après un rapide `mvn clean install` (ou `gradle build`) la bibliothèque sera sur votre classpath et vous serez prêt à coder.

---

## Étape 2 : Créer un nouveau document et un builder

Un `Document` représente le fichier Word complet, tandis que `DocumentBuilder` vous permet de le modifier. Pensez au builder comme un stylo qui dessine sur une toile vierge.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Pourquoi commencer avec un document vierge ? Cela garantit que vous avez le contrôle total sur chaque élément ajouté, et il n’y a aucun formatage caché qui pourrait vous surprendre plus tard.

---

## Étape 3 : Insérer le contrôle ActiveX CommandButton

Passons maintenant à la star du spectacle. Aspose.Words expose `insertForms2OleControl` qui peut placer n’importe quel contrôle ActiveX que vous spécifiez. Ici, nous demandons un **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

La méthode renvoie un objet `Forms2OleControl`, vous donnant un accès programmatique aux propriétés du bouton. C’est ici que **comment insérer activex** devient une ligne de code—pas besoin de bricoler avec les API COM de bas niveau.

---

## Étape 4 : Position, taille et définir la légende du bouton

Un bouton qui flotte au milieu de la page n’est pas très utile. Vous voudrez le placer là où les utilisateurs s’attendent à le voir, lui donner une taille raisonnable, et—le plus important—**définir la légende du bouton** afin qu’ils sachent ce que le clic déclenchera.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Pourquoi ces nombres ?** Word utilise les points (1 pt ≈ 1/72 pouce). `100 pt` ≈ 1,4 po depuis la gauche, `150 pt` ≈ 2,1 po depuis le haut—approximativement le centre d’une page A4 standard. Ajustez-les selon votre mise en page.

Définir la légende est crucial ; sans elle, le bouton ressemble à un rectangle vide. La méthode `setCaption` accepte n’importe quelle chaîne, vous pouvez donc la localiser plus tard si besoin.

---

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Vous pouvez choisir n’importe quel dossier ; assurez‑vous simplement que le chemin existe.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Lorsque vous ouvrez `ActiveXButton.docx` dans Word, vous verrez un bouton bien placé portant la légende **« Click Me »**. Si vous double‑cliquez dessus, Word vous demandera d’activer les macros (les contrôles ActiveX étant considérés comme macro‑activés). Vous pourrez alors lier une routine VBA à l’événement `Click` du bouton.

---

## Cas particuliers et astuces que vous pourriez manquer

- **Format macro‑activé** : Word désactive les contrôles ActiveX dans les fichiers `.docx` simples à moins que l’utilisateur n’active les macros. Si vous avez besoin que le bouton fonctionne immédiatement, envisagez d’enregistrer au format `.docm` (macro‑activé) en utilisant `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibilité** : Les versions plus anciennes de Word (pré‑2007) utilisent le format binaire `.doc`. Aspose.Words peut enregistrer dans ce format, mais les propriétés du contrôle peuvent s’afficher légèrement différemment.
- **Paramètres de sécurité** : Certains environnements d’entreprise verrouillent ActiveX. Si votre bouton n’apparaît pas, vérifiez le Centre de confiance de Word → Paramètres ActiveX.
- **Boutons multiples** : Vous en voulez plusieurs ? Répétez simplement l’appel `insertForms2OleControl` et ajustez les valeurs `Left`/`Top` de chaque bouton. Conservez les objets retournés afin de pouvoir définir des légendes individuelles.
- **Styliser la légende** : La légende hérite de la police par défaut. Pour la modifier, il faudrait éditer le XML sous‑jacent ou appliquer un style Word après l’insertion—au‑delà du cadre de ce guide rapide, mais réalisable avec l’API `ParagraphFormat` d’Aspose.Words.

---

## Exemple complet fonctionnel

Voici la classe Java complète, prête à être exécutée. Copiez‑collez‑la dans votre IDE, ajustez le chemin de sortie, puis cliquez sur **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Résultat attendu** : Après l’exécution, la console indique l’emplacement d’enregistrement. L’ouverture du fichier généré dans Word montre un bouton placé approximativement au centre de la page, libellé « Click Me ». Un clic déclenchera l’événement standard ActiveX click (vous devrez y associer une macro VBA pour répondre).

---

## Conclusion

Vous savez maintenant **comment insérer ActiveX** des contrôles CommandButton dans un document Word de façon programmatique avec Aspose.Words, et vous avez vu exactement comment **définir la légende du bouton**, positionner et dimensionner le contrôle. Cette approche élimine le travail manuel d’interface, s’intègre proprement aux générateurs de rapports automatisés, et vous donne un contrôle complet sur le

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insérer des formes dans des documents Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insérer une image en ligne dans un document Word en utilisant Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insérer une image dans l’en‑tête d’un document Word | Aspose.Words pour .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}