---
category: general
date: 2026-06-17
description: Enregistrez les avertissements de substitution de police dans Java avec
  Aspose.Words – capturez les polices manquantes lors du chargement du document et
  maintenez la cohérence de votre sortie.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: fr
og_description: Enregistrez les avertissements de substitution de police en Java avec
  Aspose.Words. Apprenez à capturer les alertes de police manquante lors du chargement
  du document et à garder vos PDF impeccables.
og_title: Enregistrer les avertissements de substitution de police en Java – Guide
  complet
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Consigner les avertissements de substitution de police en Java avec Aspose.Words
url: /fr/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Consigner les avertissements de substitution de police en Java – Guide complet

Vous vous êtes déjà demandé comment **consigner les avertissements de substitution de police** lorsqu’un document Word utilise une police que vous n’avez pas sur le serveur ? Vous n’êtes pas le seul à vous creuser la tête face aux polices manquantes qui sont silencieusement remplacées. Bonne nouvelle : Aspose.Words for Java vous offre un moyen propre de capturer ces substitutions dès le chargement d’un document.

Dans ce tutoriel, nous parcourrons un exemple pratique qui montre exactement comment enregistrer un rappel d’avertissement, filtrer les alertes de substitution de police et les écrire dans la console (ou tout autre journal que vous préférez). À la fin, vous disposerez d’un extrait réutilisable que vous pourrez intégrer à n’importe quel projet Java utilisant **Aspose.Words Java**.

## Ce que vous allez apprendre

- Comment configurer **LoadOptions** pour capturer les avertissements.
- Comment implémenter un **IWarningCallback** qui ne réagit qu’aux événements de **substitution de police**.
- Comment charger un document en toute sécurité tout en conservant une trace claire des polices manquantes.
- Astuces pour étendre la solution vers des journaux basés sur des fichiers ou des systèmes de surveillance.

### Prérequis

- Java 8 ou supérieur (le code fonctionne également avec Java 11+).
- Bibliothèque Aspose.Words for Java (version 23.10 ou ultérieure recommandée).
- Un fichier `.docx` d’exemple qui référence une police non installée sur votre machine (par ex., `MissingFont.docx`).

Aucun cadre supplémentaire n’est requis — juste du Java pur et les JARs Aspose.

---

## Étape 1 : Configurer LoadOptions pour Aspose.Words Java

Avant de pouvoir intercepter les avertissements, vous avez besoin d’une instance **LoadOptions**. Cet objet indique à Aspose.Words comment se comporter lors de l’analyse du fichier entrant.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Pourquoi cette étape est‑elle cruciale ? Sans objet `LoadOptions`, la bibliothèque substitue silencieusement les polices manquantes et vous ne voyez jamais la trace. En créant explicitement cet objet, vous ouvrez la porte à un **callback d’avertissement** personnalisé qui peut consigner exactement ce qui vous intéresse.

> **Astuce pro** : si vous chargez de nombreux documents en lot, réutilisez une même instance `LoadOptions` afin d’éviter une surcharge inutile d’objets.

---

## Étape 2 : Implémenter un callback d’avertissement pour la substitution de police

Aspose.Words fournit l’interface `IWarningCallback`. La mettre en œuvre vous permet de décider quoi faire lorsque le moteur lève un `WarningInfo`. Dans notre cas, nous ne voulons réagir qu’à `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Quelques points à retenir :

1. **Filtrage** – La condition `if` garantit que nous ignorons les avertissements non pertinents (comme les problèmes de mise en page) et que le journal reste lisible.
2. **Sécurité des threads** – Le callback s’exécute sur le même thread qui charge le document, donc aucune synchronisation supplémentaire n’est nécessaire pour une simple sortie console. Si vous écrivez dans un logger partagé, assurez‑vous qu’il soit thread‑safe.
3. **Extensibilité** – Vous voulez écrire dans un fichier ? Remplacez `System.out.println` par `java.util.logging.Logger` ou un framework de logging tiers.

---

## Étape 3 : Charger le document avec les options configurées

Maintenant que le callback est en place, chargez votre fichier Word. Au moment où Aspose.Words analyse le document, toute police manquante déclenchera le callback défini précédemment.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Si le fichier source référence une police qui n’est pas installée, vous verrez une sortie similaire à :

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Cette ligne constitue les **avertissements de substitution de police** que vous recherchiez. Vous pouvez maintenant agir — alerter un utilisateur, basculer vers une feuille de style de secours, ou simplement garder une trace pour la conformité.

---

## Étape 4 : Poursuivre le traitement normal

Après le chargement, le document se comporte comme n’importe quel autre objet `Document`. N’hésitez pas à inspecter les sections, extraire du texte ou convertir en PDF. Le journal d’avertissement s’effectue automatiquement pendant l’étape de chargement, aucune logique supplémentaire n’est requise.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

La console affichera désormais à la fois l’avertissement de substitution de police (le cas échéant) **et** le nombre de sections, confirmant que le document est pleinement fonctionnel.

---

## Astuces avancées & cas particuliers

### Journaliser dans un fichier au lieu de la console

Si vous préférez un journal persistant, remplacez l’appel `System.out.println` par un `FileWriter` :

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

N’oubliez pas de gérer correctement les `IOException` en production.

### Capturer plusieurs documents dans une boucle

Lors du traitement d’un dossier de documents, vous pouvez réutiliser le même callback :

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Comme le callback est attaché à `loadOptions`, chaque itération consigne automatiquement les événements de substitution de police.

### Gestion des polices incorporées

Aspose.Words peut incorporer les polices manquantes si vous l’activez :

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Même avec l’incorporation activée, le callback d’avertissement se déclenche, vous offrant une visibilité sur ce qui a été substitué.

---

## Exemple complet fonctionnel

Voici le programme complet, prêt à être exécuté. Copiez‑le dans une classe nommée `FontSubstitutionDiagnostics.java`, ajustez le chemin du fichier, puis lancez‑le.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Sortie attendue** (en supposant que le document source référence une police manquante) :

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

La console et le fichier `font_substitution_log.txt` contiendront l’avertissement, vous offrant une piste d’audit fiable.

---

## Conclusion

Nous venons de vous montrer comment **consigner les avertissements de substitution de police** en Java avec Aspose.Words. En configurant `LoadOptions`, en branchant un `IWarningCallback` et en chargeant le document, vous obtenez une visibilité totale sur les événements de police manquante qui pourraient autrement passer inaperçus. À partir d’ici, vous pouvez :

- Diriger les avertissements vers un service de journalisation central.
- Déclencher des alertes pour des pipelines de contrôle qualité.
- Combiner cette technique avec d’autres stratégies de **chargement de documents**, comme la conversion PDF ou le publipostage.

N’hésitez pas à expérimenter — remplacez le logger console par SLF4J, ajoutez des horodatages, ou même poussez des alertes vers un tableau de bord de surveillance. Le schéma de base reste le même, et vous disposez désormais d’une base solide pour une gestion robuste des polices dans tout flux de travail documentaire basé sur Java.

Vous avez une variante à partager ? Peut‑être avez‑vous intégré cela avec Spring Boot ou une fonction cloud. Laissez un commentaire ci‑dessous, et continuons la discussion. Bon codage !


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Capture des avertissements de substitution de police en Java avec Aspose.Words – Guide complet](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Utilisation des options et paramètres de document dans Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Activer les avertissements de substitution de police dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}