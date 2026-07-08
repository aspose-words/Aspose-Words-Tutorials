---
category: general
date: 2026-07-06
description: Créer DocumentConfig en Java pour suivre les polices manquantes avec
  Aspose.Words – un guide complet, étape par étape, destiné aux développeurs.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: fr
og_description: Créez DocumentConfig en Java pour suivre les polices manquantes avec
  Aspose.Words. Découvrez le flux de travail complet, de la configuration à la gestion
  des avertissements.
og_title: Créer DocumentConfig en Java – Suivre les polices manquantes
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Créer DocumentConfig en Java – Suivre les polices manquantes avec Aspose.Words
url: /fr/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer DocumentConfig en Java – Suivre les polices manquantes avec Aspose.Words

**Créer DocumentConfig en Java** pour surveiller les avertissements de substitution de police lors du chargement d’un document Word. Vous vous êtes déjà demandé pourquoi certains caractères semblent étranges après l’ouverture d’un DOCX ? Il est fort probable que la police d’origine ne soit pas installée sur la machine, et Aspose.Words la remplace silencieusement. Dans ce tutoriel, nous vous montrons exactement comment **suivre les polices manquantes** afin de ne jamais être surpris par un glyphe errant.

Nous passerons en revue tout ce dont vous avez besoin : la configuration Maven/Gradle, le code qui crée un `DocumentConfig`, un `IWarningCallback` personnalisé qui ne filtre que les alertes de substitution de police, et une méthode rapide pour consigner ces messages. À la fin, vous disposerez d’un exemple exécutable qui affiche chaque avertissement de police manquante dans la console (ou dans un fichier, si vous le préférez).

---

## Ce que vous allez apprendre

- Pourquoi un `DocumentConfig` est l’endroit idéal pour intercepter les événements de substitution de police.  
- Comment **suivre les polices manquantes** sans polluer vos journaux avec des avertissements non pertinents.  
- Un programme Java complet, prêt à copier‑coller, qui démontre la technique.  
- Des astuces pour étendre la solution : par exemple, écrire les avertissements dans une base de données ou envoyer des alertes par e‑mail.

### Prérequis

| Exigence | Raison |
|----------|--------|
| Java 8 ou version supérieure | Aspose.Words for Java prend en charge JDK 8+. |
| Bibliothèque Aspose.Words for Java (dernière version) | Fournit `DocumentConfig`, `IWarningCallback`, etc. |
| Un IDE ou un outil de construction (IntelliJ, Eclipse, Maven/Gradle) | Pour compiler et exécuter l’exemple. |
| Un fichier DOCX qui référence des polices que vous n’avez pas installées | Pour voir l’avertissement en action. |

Si vous avez déjà un projet, ajoutez simplement la dépendance Aspose et vous êtes prêt à partir.

---

## Étape 1 : Ajouter Aspose.Words à votre build

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Astuce pro :** La version d’essai gratuite fonctionne parfaitement pour les tests, mais pensez à appliquer une licence en production pour supprimer le filigrane d’évaluation.

---

## Étape 2 : Créer DocumentConfig et enregistrer un Warning Callback

Le cœur de la solution se trouve dans cet extrait. Nous **créons un DocumentConfig**, y attachons un `IWarningCallback` personnalisé, et indiquons de **suivre uniquement les polices manquantes**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Pourquoi cela fonctionne :** Lorsque Aspose.Words analyse un document, il génère des objets `WarningInfo` pour chaque irrégularité. En fournissant un callback, vous interceptez ces avertissements *avant* qu’ils ne disparaissent dans le néant. La condition `if` garantit que nous ne **suivons que les polices manquantes**, en ignorant les autres avertissements comme les balises obsolètes ou les fonctionnalités non prises en charge.

---

## Étape 3 : Exécuter l’exemple et observer la sortie

Placez un DOCX qui référence une police que vous n’avez pas (par ex., “Comic Sans MS” sur une machine Linux). Exécutez le programme :

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Vous devriez voir quelque chose de similaire à :

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Chaque ligne correspond à une police manquante qu’Aspose a automatiquement remplacée. S’il n’y a aucune police manquante, le programme reste silencieux — exactement ce que vous voulez pour un journal propre.

---

## Étape 4 : Persister la liste des polices manquantes (optionnel)

Afficher les messages dans la console est pratique pour les démonstrations, mais dans un service réel vous souhaiterez probablement stocker les données. Voici une façon rapide d’écrire les avertissements dans un fichier texte.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Désormais, chaque événement de police manquante ajoute une ligne à `missing-fonts.log`. Vous pourrez ensuite analyser ce fichier, l’alimenter dans un tableau de bord de surveillance, ou même déclencher une alerte si une police critique disparaît de votre serveur.

---

## Étape 5 : Pièges courants et comment les éviter

| Symptom | Cause probable | Solution |
|---------|----------------|----------|
| Aucun avertissement n’apparaît alors que le DOCX utilise des polices inconnues | Callback non enregistré ou `setWarningCallback` appelé après le chargement du document | Assurez‑vous que `config.setWarningCallback(...)` est exécuté **avant** la création de l’instance `Document`. |
| L’application plante avec `NullPointerException` | `info.getDescription()` renvoie `null` pour certains types d’avertissements rares | Protégez contre le null : `String desc = info.getDescription(); if (desc != null) …` |
| Trop d’avertissements non pertinents inondent la console | Le filtre ne cible que `FONT_SUBSTITUTION` ? | Revérifiez la condition `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Ralentissement des performances sur de gros lots | Écriture synchronisée dans le fichier pour chaque avertissement | Regroupez les écritures ou utilisez un `BufferedWriter` pour réduire la surcharge d’E/S. |

---

## Étape 6 : Étendre la solution – De la console à l’entreprise

- **Journalisation en base de données** : Remplacez le `FileWriter` par un insert JDBC ; stockez `documentName`, `missingFont` et `timestamp`.  
- **Alertes e‑mail** : Intégrez JavaMail ; envoyez un résumé après le traitement d’un lot de documents.  
- **Logique de substitution personnalisée** : Au lieu de laisser Aspose choisir une police de secours, vous pouvez charger une collection locale de polices via `FontSettings.setFontsFolder()` et relancer le chargement si une substitution survient.

Ces extensions conservent l’idée centrale — **créer DocumentConfig** et **suivre les polices manquantes** — tout en permettant une mise à l’échelle en production.

---

## Conclusion

Vous disposez maintenant d’un modèle solide, prêt à copier‑coller, pour **créer un DocumentConfig** en Java et l’utiliser afin de **suivre les polices manquantes** avec Aspose.Words. L’approche est légère, ne nécessite que quelques lignes de code, et vous donne un contrôle total sur la façon dont les avertissements de substitution de police sont gérés. Que vous construisiez un service de conversion de documents, un générateur de rapports automatisé ou un outil d’audit de conformité, connaître exactement quelles polices sont absentes peut vous faire gagner des heures de débogage.

Prochaines étapes ? Essayez de remplacer la sortie console par un journal JSON structuré, ou intégrez le callback dans un micro‑service Spring Boot qui traite les téléchargements en temps réel. Et si vous rencontrez des cas particuliers — par exemple une police OpenType personnalisée qu’Aspose ne parvient pas à analyser — laissez un commentaire ci‑dessous ; nous résoudrons le problème ensemble.

Bon codage, et que vos PDFs s’affichent toujours avec les polices attendues !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Utiliser les polices dans Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [Personnaliser les couleurs de thème et les polices dans Aspose.Words Java : Guide complet](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Comment créer des documents PDF avec Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}