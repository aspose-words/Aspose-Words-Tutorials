---
category: general
date: 2026-07-23
description: Apprenez à ajouter Forms2OleControl à un DOCX à l’aide d’Aspose.Words.
  Ce guide étape par étape montre comment insérer un contrôle ActiveX CommandButton
  en Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: fr
lastmod: 2026-07-23
og_description: Ajoutez Forms2OleControl à un DOCX instantanément. Suivez ce guide
  pratique pour intégrer un bouton de commande ActiveX à l’aide d’Aspose.Words pour
  Java.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: Ajouter Forms2OleControl à DOCX – Tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: Ajouter Forms2OleControl à DOCX – Guide complet d'Aspose.Words
url: /fr/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter Forms2OleControl à DOCX – Guide complet Aspose.Words

Vous vous êtes déjà demandé comment **ajouter Forms2OleControl à DOCX** sans vous arracher les cheveux ? Vous n'êtes pas le seul. Que vous construisiez un rapport basé sur un modèle ou que vous ayez besoin d'un bouton cliquable dans un fichier Word, intégrer un contrôle ActiveX est la sauce secrète.

Dans ce tutoriel, nous parcourrons un exemple concret qui **ajoute Forms2OleControl à DOCX** avec Aspose.Words pour Java. Vous verrez le code complet, comprendrez pourquoi chaque ligne est importante, et obtiendrez des astuces pour gérer les particularités qui font souvent trébucher les développeurs.

## Ce que vous apprendrez

- Comment configurer Aspose.Words dans un projet Java  
- Les étapes exactes pour **insérer un contrôle ActiveX dans DOCX** (oui, le mot‑clé principal encore une fois)  
- Configurer les propriétés d’un CommandButton afin qu’il se comporte comme un véritable élément d’interface utilisateur  
- Enregistrer le document et vérifier que le contrôle est réellement intégré  

Aucune expérience préalable avec ActiveX n’est requise, mais une compréhension de base de Java et Maven/Gradle rendra le parcours plus fluide. Prêt ? Plongeons‑y.

---

## Étape 1 : Configurer Aspose.Words dans votre projet

Avant de pouvoir **ajouter Forms2OleControl à DOCX**, vous avez besoin de la bibliothèque Aspose.Words dans le classpath. La façon la plus simple est via Maven :

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Astuce :** Si vous utilisez Gradle, l’équivalent est `implementation 'com.aspose:aspose-words:24.9'`.  

Pourquoi c’est important : Aspose.Words fournit la méthode `DocumentBuilder.insertForms2OleControl()` sur laquelle nous compterons pour **insérer un contrôle ActiveX dans DOCX**. Sans la bibliothèque, le compilateur n’aurait aucune idée de ce qu’est un `Forms2OleControl`.

---

## Étape 2 : Ajouter Forms2OleControl à DOCX

Voici le cœur du tutoriel — c’est ici que nous **ajoutons réellement Forms2OleControl à DOCX**. Nous créerons un nouveau document, lancerons un `DocumentBuilder`, et appellerons la méthode d’insertion.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Que se passe-t-il ici ?**  

- `new Document()` nous donne une toile vierge. Pensez‑y comme une feuille de papier neuve prête pour **insérer un contrôle ActiveX dans DOCX**.  
- `builder.insertForms2OleControl()` crée le conteneur OLE de bas niveau qu’Aspose.Words appelle *Forms2OleControl*. C’est le seul appel d’API qui **ajoute réellement Forms2OleControl à DOCX**.  
- Définir `OleControlType.COMMANDBUTTON` indique à Word que l’objet OLE doit se comporter comme un CommandButton classique—exactement comme le bouton que vous placeriez sur un formulaire dans le concepteur d’interface.  
- Enfin, `document.save(...)` écrit le fichier .docx, conservant l’ActiveX intégré.  

---

## Étape 3 : Configurer les propriétés du CommandButton (Pourquoi c’est important)

Insérer simplement le contrôle vous donne un espace réservé vide. Pour le rendre utile, vous devez définir quelques propriétés :

| Propriété | Objectif | Valeur typique |
|----------|---------|---------------|
| `setOleControlType` | Définit le type de contrôle ActiveX (Button, CheckBox, etc.) | `OleControlType.COMMANDBUTTON` |
| `setName` | Identifiant interne utilisé par les macros Word ou les scripts VBA | `"MyButton"` |
| `setCaption` | Le texte affiché sur la surface du bouton | `"Click Me"` |

Si vous omettez cela, le bouton apparaît avec un nom générique et aucune étiquette—rien que l’utilisateur ne cliquerait. De plus, rappelez‑vous que les contrôles ActiveX sont **spécifiques à la plateforme** ; ils ne fonctionnent que sur des machines Windows avec les bibliothèques COM appropriées installées.

> **Attention :** Lorsque vous ouvrez le DOCX généré sur une plateforme non‑Windows (par ex., macOS), Word affichera une image d’espace réservé au lieu d’un vrai bouton. C’est une limitation normale d’ActiveX, pas un bug dans votre code.

---

## Étape 4 : Enregistrer et vérifier le document

La fonction `document.save(...)` écrit un fichier DOCX standard que toute version moderne de Microsoft Word peut ouvrir. Après avoir exécuté le programme, ouvrez `ActiveXButton.docx` :

1. Localisez le bouton « Click Me » à l’endroit où vous l’avez inséré.  
2. Cliquez avec le bouton droit sur le bouton → **Properties** pour confirmer le nom et la légende.  
3. Cliquez sur le bouton ; Word affichera une boîte de dialogue simple si vous avez attaché une macro (hors du cadre de ce guide).  

Si le bouton est absent, vérifiez que vous avez correctement utilisé l’**exemple Aspose.Words Forms2OleControl** et que le dossier de sortie existe.  

> **Cas particulier :** Si vous avez besoin que le bouton déclenche une macro, vous devrez ajouter du code VBA au document après l’enregistrement. Aspose.Words peut injecter du VBA en utilisant l’API `Document.getBuiltInDocumentProperties()`, mais cela constitue un tutoriel complet à part.  

---

## Variations courantes et pièges

### Utiliser un autre contrôle ActiveX
Si vous voulez une case à cocher au lieu d’un bouton, il suffit de changer le type de contrôle :

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### Intégrer plusieurs contrôles
Appelez `builder.insertForms2OleControl()` plusieurs fois, en déplaçant le curseur avec `builder.moveTo()` ou en insérant du texte entre les appels. Chaque appel ajoute un nouveau conteneur OLE, vous permettant de créer des formulaires complexes dans un seul DOCX.

### Travailler avec .NET
La même logique s’applique à C#—les noms de méthodes sont identiques (`DocumentBuilder.InsertForms2OleControl()`). Si vous êtes sur .NET, remplacez la syntaxe Java par son équivalent C#, mais le concept d’**intégration d’un CommandButton dans un document Word** reste inchangé.

---

## Conclusion

Vous disposez maintenant d’un exemple fonctionnel, de bout en bout, qui **ajoute Forms2OleControl à DOCX** en utilisant Aspose.Words pour Java. En créant un document vierge, en insérant le contrôle ActiveX, en configurant ses propriétés et en enregistrant le fichier, vous avez maîtrisé les étapes essentielles pour **insérer un contrôle ActiveX dans DOCX** et pouvez étendre ce modèle à d’autres types de contrôles.

Et ensuite ? Essayez de combiner cette technique avec la fusion et publipostage d’Aspose.Words pour générer des formulaires personnalisés, ou explorez l’ajout de macros VBA pour que le bouton fasse réellement quelque chose. Le ciel est la limite lorsque vous associez le code de l’**exemple Aspose.Words Forms2OleControl** à votre propre logique métier.

Bon codage, et n’hésitez pas à laisser un commentaire si vous rencontrez des problèmes !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words pour Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Ajouter des signets Word avec Aspose.Words pour Java – Insérer, Mettre à jour, Supprimer](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [Comment ajouter un filigrane aux documents avec Aspose.Words pour Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}