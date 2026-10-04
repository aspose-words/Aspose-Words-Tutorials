---
category: general
date: 2026-10-04
description: Apprenez comment initialiser DocumentBuilder pour un nouveau document
  et ajouter un bouton ActiveX avec Aspose.Words en Java. Guide étape par étape avec
  le code complet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: fr
lastmod: 2026-10-04
og_description: Initialisez DocumentBuilder pour un nouveau document et intégrez un
  bouton de commande ActiveX à l'aide de l'API Aspose.Words Java. Suivez ce tutoriel
  concis.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Initialiser DocumentBuilder pour un nouveau document – guide complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Comment initialiser DocumentBuilder pour un nouveau document en utilisant Aspose.Words
url: /fr/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment initialiser DocumentBuilder pour un nouveau document avec Aspose.Words

Si vous devez **initialiser DocumentBuilder pour un nouveau document** dans un projet Java, ce tutoriel vous montre les étapes exactes. Vous verrez comment créer un fichier Word vierge, ajouter un bouton de commande ActiveX et enregistrer le résultat — le tout avec un seul exemple de code autonome.

Travailler avec des documents Word de manière programmatique implique souvent de gérer des détails de bas niveau comme les contrôles de formulaire. À la fin de ce guide, vous pourrez intégrer un bouton ActiveX sans quitter votre IDE, ce qui est utile pour générer des modèles, des rapports automatisés ou des formulaires interactifs.

## Prérequis

* Java 17 ou version ultérieure installé  
* Maven 3.8+ (ou Gradle si vous préférez)  
* Une licence Aspose.Words for Java (l'essai gratuit fonctionne pour les tests)  
* Familiarité de base avec la syntaxe Java  

Si vous êtes nouveau avec Aspose.Words, la bibliothèque fournit une API de haut niveau pour créer, modifier et enregistrer des documents Word. La classe `DocumentBuilder` est le point d'entrée principal pour construire le contenu d'un document.

## Étape 1 : Configurer le projet Maven

Créez un nouveau projet Maven (ou ajoutez‑le à un projet existant) et incluez la dépendance Aspose.Words :

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Astuce :** Gardez la version de la bibliothèque à jour ; les versions plus récentes ajoutent la prise en charge de contrôles de formulaire supplémentaires et améliorent les performances.

## Étape 2 : Initialiser `DocumentBuilder` pour un nouveau document

Le cœur du tutoriel est l'opération **initialiser DocumentBuilder pour un nouveau document**. Vous créez d'abord une instance vide de `Document`, puis la passez au constructeur de `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c'est important :* Initialiser `DocumentBuilder` lie le builder à un objet `Document` spécifique, vous permettant d'ajouter des paragraphes, des tableaux ou des contrôles de formulaire directement à ce document. Sans cette étape, le builder n'aurait aucune cible sur laquelle travailler.

## Étape 3 : Insérer un contrôle de bouton de commande ActiveX

Aspose.Words expose la classe `Forms2OleControl` pour intégrer des contrôles ActiveX hérités. Le code suivant ajoute un **bouton de commande Forms2OleControl** à la position actuelle du curseur.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Qu'est‑ce qu'un bouton de commande ActiveX ?

Un bouton de commande ActiveX est un élément d'interface hérité qui peut exécuter des macros ou déclencher des événements lorsqu'un utilisateur clique dessus dans un document Word. Bien que les versions modernes d'Office privilégient les Content Controls, de nombreux modèles d'entreprise s'appuient encore sur ActiveX pour la compatibilité descendante.

## Étape 4 : Enregistrer le document

Après avoir inséré le contrôle, il suffit d'appeler `save`. Le fichier contiendra le bouton ActiveX et pourra être ouvert dans Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Lorsque vous ouvrez `ActiveXButton.docx` dans Word, vous verrez un bouton intitulé **Click Me**. Cliquer sur le bouton ne fera rien à moins d'y attacher une macro, mais le contrôle lui‑même est pleinement fonctionnel.

## Exemple complet et exécutable

Ci‑dessous se trouve le programme complet que vous pouvez copier‑coller dans `src/main/java/com/example/ActiveXButtonDemo.java`. Il comprend tous les imports et la gestion des erreurs nécessaires pour un test rapide.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Sortie attendue**

```
Document saved to output/ActiveXButton.docx
```

Ouvrez le fichier généré dans Microsoft Word 2016 ou une version ultérieure ; vous devriez voir un bouton intitulé *Click Me* placé en haut de la première page.

## Variations courantes et cas limites

| Scénario | Ajustement |
|----------|------------|
| **Ajouter le bouton à un paragraphe spécifique** | Déplacez le curseur du builder avec `builder.moveToParagraph(index, NodeType.PARAGRAPH);` avant d'appeler `insertForms2OleControl`. |
| **Définir la taille du bouton** | Utilisez `commandButton.setWidth(100);` et `commandButton.setHeight(30);` pour définir les dimensions en points. |
| **Ajouter une macro au bouton** | Après avoir enregistré le document, ouvrez‑le dans Word, activez l'onglet Développeur et attachez manuellement une macro VBA au bouton (les contrôles ActiveX ne peuvent pas être scriptés directement depuis Aspose.Words). |
| **Cibler le format .doc (binaire)** | Modifiez `doc.save(outputPath, SaveFormat.DOC);` pour produire un fichier Word 97‑2003 hérité. |
| **Exécuter sur Android** | Utilisez Aspose.Words pour Android via son API Java ; le même code fonctionne tant que la bibliothèque est incluse dans l'APK. |

## Conseils de dépannage

* **`java.lang.NoClassDefFoundError`** – Assurez‑vous que le JAR Aspose.Words est présent dans le classpath. Maven l'ajoute automatiquement ; pour les builds manuels, placez le JAR dans `libs/` et ajoutez‑le aux bibliothèques de votre IDE.  
* **Le bouton n'apparaît pas dans Word** – Vérifiez que l'option *Afficher les formulaires hérités* est activée dans le Centre de confiance de Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **Exception de licence** – Si vous exécutez le code sans licence valide, Aspose.Words insérera un filigrane. Enregistrez un essai gratuit ou achetez une licence pour le supprimer.

## Conclusion

Vous savez maintenant comment **initialiser DocumentBuilder pour un nouveau document**, insérer un bouton de commande ActiveX et enregistrer le résultat avec Aspose.Words for Java. Ce modèle vous permet de générer des modèles Word interactifs de manière programmatique, ce qui est particulièrement pratique pour les rapports automatisés ou les flux de travail basés sur des formulaires.

À partir d'ici, vous pouvez explorer d'autres contrôles de formulaire (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, etc.), combiner le bouton avec des macros VBA personnalisées, ou générer des documents complets incluant tableaux, images et styles — le tout en utilisant le même flux de travail `DocumentBuilder`.

---

*Prêt à créer des automatisations Word plus complexes ? Consultez nos guides sur **insérer un tableau avec DocumentBuilder**, **appliquer des styles programmatique**, et **exporter en PDF avec Aspose.Words**.*

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Comment enregistrer un document au format PDF avec Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Ajouter un filigrane à un document avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}