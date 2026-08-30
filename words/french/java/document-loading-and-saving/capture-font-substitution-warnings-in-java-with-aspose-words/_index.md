---
category: general
date: 2026-06-27
description: Apprenez à capturer les avertissements de substitution de police en Java
  à l’aide d’Aspose.Words. Ce tutoriel pas à pas couvre également les rappels d’avertissement
  et l’utilisation de LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: fr
og_description: Capturez les avertissements de substitution de polices en Java avec
  Aspose.Words. Suivez ce guide pour configurer les callbacks d’avertissement, utiliser
  LoadOptions et gérer les polices manquantes.
og_title: Capturer les avertissements de substitution de police en Java – Tutoriel
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Capture des avertissements de substitution de police en Java avec Aspose.Words
  – Guide complet
url: /fr/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturer les avertissements de substitution de police en Java avec Aspose.Words – Guide complet

Vous avez déjà eu besoin de **capturer les avertissements de substitution de police** lors du chargement d'un DOCX utilisant des polices exotiques ? Vous n'êtes pas le seul. Dans de nombreux projets réels—pensez aux générateurs de rapports automatisés ou aux convertisseurs de documents par lots—les polices manquantes déclenchent des substitutions silencieuses qui peuvent ruiner la fidélité de la mise en page.  

Heureusement, Aspose.Words vous offre un moyen simple d'écouter ces avertissements. Dans ce tutoriel, nous parcourrons la configuration de **LoadOptions**, le branchement d'un **callback d'avertissement Aspose.Words**, et l'affichage de chaque avis de *substitution de police* dans la console. À la fin, vous saurez exactement quand une police a été remplacée et comment réagir programmatiquement.

> **Ce que vous obtiendrez :** un extrait Java entièrement exécutable, une explication du *pourquoi* chaque élément est important, et des conseils pour gérer les cas limites comme les répertoires de polices personnalisées.

## Prérequis et ce dont vous aurez besoin

Before we dive in, make sure you have:

- Java 8 ou une version plus récente installée (le code fonctionne également avec Java 11+).
- Le dernier JAR Aspose.Words for Java (téléchargez-le depuis le site officiel ou Maven Central).
- Un fichier DOCX qui référence des polices non installées sur votre machine (par ex., un *font‑rich.docx* que vous pouvez trouver dans le jeu de démonstration Aspose).
- Un IDE décente (IntelliJ IDEA, Eclipse, ou même VS Code avec les extensions Java).

Aucune bibliothèque externe au-delà d'Aspose.Words n'est requise, et l'exemple s'exécute dans une simple méthode `main`.

## Étape 1 : Configurer LoadOptions – Le point d'entrée pour le chargement personnalisé

`LoadOptions` est le sac de configuration d'Aspose.Words qui indique à la bibliothèque *comment* lire un document. Par défaut, il substitue silencieusement les polices manquantes, mais vous pouvez modifier ce comportement avec un callback d'avertissement.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Pourquoi c'est important :** Sans `LoadOptions`, le document se charge silencieusement et vous perdez la visibilité sur les polices manquantes. En créant une instance, vous obtenez un point d'accroche pour le système d'avertissement.

## Étape 2 : Définir un callback d'avertissement pour *capturer les avertissements de substitution de police*

Aspose.Words transmet les événements d'avertissement via l'interface `IWarningCallback`. Implémentez‑la en ligne (ou comme classe séparée) et filtrez pour `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Explication :**  
- `info.getWarningType()` indique la catégorie de l'avertissement.  
- `WarningType.FONT_SUBSTITUTION` est la valeur d'énumération qui nous intéresse.  
- `info.getDescription()` contient un message lisible par l'homme, par ex., *« Police 'Comic Sans MS' non trouvée, substituée par 'Arial' ». *

En affichant la description, vous **capturez les avertissements de substitution de police** en temps réel.

## Étape 3 : Charger le document en utilisant les LoadOptions configurés

Maintenant que le callback est en place, chargez votre DOCX. Le callback d'avertissement se déclenche automatiquement pendant l'analyse.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Remplacez `YOUR_DIRECTORY` par le chemin réel de votre fichier de test. Lorsque le constructeur `Document` s'exécute, toute police manquante déclenche le callback défini précédemment, et vous verrez les messages de substitution dans la console.

## Étape 4 : Vérifier le document chargé (facultatif mais utile)

Après le chargement, vous pouvez vouloir confirmer l'intégrité du document — nombre de pages, extraction de texte, etc. Cette étape n'est pas requise pour capturer les avertissements, mais elle vous aide à voir l'impact des substitutions.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Si une police a été substituée, la mise en page peut légèrement changer ; vérifier le nombre de pages peut révéler ces modifications.

## Étape 5 : Avancé – Gérer les polices substituées programmatiquement

Parfois, vous ne voulez pas seulement consigner l'avertissement — vous pourriez devoir intégrer une police de secours ou ajuster le style. Voici un modèle rapide que vous pouvez adopter.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

En indiquant à Aspose.Words un dossier contenant les polices originales, vous pouvez *éviter* totalement la substitution. Si le dossier est absent, le callback d'avertissement capture toujours l'événement, vous offrant une stratégie de secours.

## Exemple complet fonctionnel

En assemblant le tout, voici le programme complet, prêt à être exécuté :

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Sortie console attendue** (lorsqu'une police manquante est rencontrée) :

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Si toutes les polices sont présentes, le callback reste silencieux—rien n'est affiché, ce qui est exactement ce à quoi vous vous attendez.

## Pièges courants & astuces pro

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Le callback ne se déclenche jamais** | Vous avez oublié d'attacher le callback à `LoadOptions` **ou** vous avez utilisé le constructeur par défaut de `Document` sans passer `loadOptions`. | Appelez toujours `loadOptions.setWarningCallback(...)` **et** utilisez la surcharge `new Document(path, loadOptions)`. |
| **Trop d'avertissements encombrent le journal** | Les gros documents avec de nombreuses polices manquantes génèrent un avertissement par substitution. | Filtrez davantage en vérifiant `info.getDescription()` pour des noms de police spécifiques, ou regroupez les avertissements dans une liste pour un traitement ultérieur. |
| **Les polices substituées affectent la mise en page** | La police de secours peut avoir des métriques différentes (taille, espacement). | Fournissez un dossier de polices personnalisé (voir Étape 5) ou ajustez le style du document après le chargement. |
| **Exécution sur un serveur sans interface graphique** | Le remplacement de police par défaut peut dépendre de polices système non installées sur le serveur. | Incluez les polices requises avec votre application et pointez `FontSettings` vers ce dossier. |

## Questions fréquentes

**Q : Cela fonctionne-t-il avec le PDF ou d’autres formats ?**  
R : Oui. Le callback d'avertissement est indépendant du format ; il se déclenche pour tout type de document qu'Aspose.Words charge (DOC, DOCX, RTF, HTML, etc.). La seule différence réside dans l'ensemble des avertissements qui peuvent apparaître.

**Q : Puis‑je capturer d'autres types d'avertissements, comme les avertissements de *résolution d'image* ?**  
R : Absolument. Dans la méthode `warning`, inspectez `info.getWarningType()` pour d'autres valeurs d'énumération telles que `WarningType.IMAGE_RESOLUTION`. Puis gérez‑les en conséquence.

**Q : Et si j’ai besoin de la liste des polices substituées après le chargement du document ?**  
R : Enregistrez chaque `info.getDescription()` dans une `List<String>` à l'intérieur du callback. Après le chargement, vous disposerez d'une collection que vous pourrez consigner, envoyer à un service de surveillance, ou utiliser pour déclencher une routine de téléchargement de polices.

## Conclusion

Vous savez maintenant **comment capturer les avertissements de substitution de police** en Java avec Aspose.Words, pourquoi chaque élément du puzzle est important, et comment étendre la solution pour des scénarios réels. En exploitant `LoadOptions`, un `callback d'avertissement Aspose.Words` et éventuellement `FontSettings`, vous obtenez une visibilité complète sur les polices manquantes et pouvez garantir la fiabilité de vos pipelines de conversion de documents.

Prêt pour l'étape suivante ? Essayez de remplacer le `System.out.println` par un logger comme SLF4J, ou intégrez la liste des avertissements dans une interface qui alerte les utilisateurs avant qu'ils finalisent une conversion par lots. Vous pouvez également explorer le **callback d'avertissement Aspose.Words** pour d'autres types d'avertissements, tels que les *fonctionnalités non prises en charge* ou les alertes d'*image haute résolution*.

Bon codage, et que vos PDF ne subissent plus jamais de substitutions de police inattendues !

![Screenshot showing console output of captured font substitution warnings](image-placeholder.png "capture font substitution warnings")

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités d'API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Activer les avertissements de substitution de police dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Comment définir LoadOptions dans Aspose.Words pour Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Comment créer des documents PDF avec Aspose.Words pour Java | API de traitement de documents](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}