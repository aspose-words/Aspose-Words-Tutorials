---
category: general
date: 2026-04-04
description: Capturez les avertissements de substitution de police lors du chargement
  de documents Word avec Aspose.Words for Java et détectez automatiquement les polices
  manquantes. Suivez ce guide étape par étape.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: fr
og_description: Capturez les avertissements de substitution de police lors du chargement
  de documents Word avec Aspose.Words pour Java et détectez les polices manquantes
  en quelques étapes simples.
og_title: Capture des avertissements de substitution de police – Détecter les polices
  manquantes
tags:
- Aspose.Words
- Java
- Document Processing
title: Capturer les avertissements de substitution de police – Détecter les polices
  manquantes
url: /fr/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturer les avertissements de substitution de police – Détecter les polices manquantes

Vous avez déjà eu besoin de **capturer les avertissements de substitution de police** lors de l'ouverture d'un fichier Word, pour découvrir qu'une police cruciale est manquante ? Vous n'êtes pas seul. Dans de nombreux flux de travail d'entreprise, une police manquante peut transformer un rapport parfaitement formaté en un désordre illisible, et le seul indice que vous obtenez est un avertissement silencieux que la plupart des développeurs ne voient jamais.

La bonne nouvelle, c'est qu'Aspose.Words for Java vous permet d'intercepter le processus de chargement et **de détecter les polices manquantes** avant qu'elles ne vous posent problème plus tard. Dans ce tutoriel, nous parcourrons un exemple complet et exécutable qui affiche chaque avertissement de substitution directement dans la console, afin que vous puissiez décider d'incorporer la bonne police, de la remplacer ou d'alerter l'utilisateur.

À la fin de ce guide, vous saurez comment :

* Configurer un objet `LoadOptions` avec un rappel d'avertissement personnalisé.
* Filtrer le rappel afin qu'il ne réagisse qu'aux événements de substitution de police.
* Charger n'importe quel fichier `.docx` et voir les avertissements instantanément.
* Étendre la solution pour consigner les avertissements, lancer des exceptions, ou même installer automatiquement les polices manquantes.

Aucune documentation externe requise — juste quelques lignes de Java et le JAR Aspose.Words.

## Prérequis

Avant de commencer, assurez-vous d'avoir :

* Java 8 ou une version plus récente installée (la dernière version LTS fonctionne le mieux).
* Aspose.Words for Java 23.11 ou ultérieur – vous pouvez récupérer l'artifact Maven ou le JAR simple depuis le site Aspose.
* Un document Word qui référence une police que vous n'avez pas sur votre machine de développement (par ex., « MyFancyFont »).
* Un IDE ou éditeur de texte de votre choix – j'utilise IntelliJ IDEA, mais Eclipse ou VS Code conviennent également.

Si l'un de ces éléments vous est inconnu, faites une pause et installez-le d'abord ; le reste du tutoriel suppose qu'ils sont prêts.

---

## Capturer les avertissements de substitution de police avec Aspose.Words

Le cœur de la solution réside dans une instance `LoadOptions`. En assignant un `IWarningCallback`, nous pouvons intercepter chaque avertissement émis par la bibliothèque pendant la phase de chargement.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Pourquoi cela fonctionne :**  
`LoadOptions` indique à Aspose.Words comment traiter le fichier entrant. L'interface `IWarningCallback` est un crochet qui reçoit un objet `WarningInfo` pour *chaque* avertissement. En vérifiant `info.getWarningType()`, nous filtrons tout sauf `SUBSTITUTED_FONT`. La propriété `description` contient un message lisible tel que « Font 'MyFancyFont' was substituted with 'Arial' ».

### Sortie console attendue

Si le document source référence une police qui n’est pas installée, vous verrez quelque chose comme :

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Si le document n'utilise que des polices présentes sur la machine, le rappel reste silencieux et vous obtenez simplement la ligne finale « Document loaded successfully. ».

## Détecter les polices manquantes dans votre document

Vous vous demandez peut‑être, *« Un avertissement de substitution est‑il identique à une police manquante ? »* Dans la plupart des cas, oui — Aspose.Words remplace une police manquante par une police de secours et le signale via `SUBSTITUTED_FONT`. Cependant, il existe des cas limites où une police est présente mais le style exact (gras‑italique, fonctionnalités OpenType spécifiques) ne l’est pas, entraînant une substitution subtile.

Pour être absolument certain d’avoir capturé chaque lacune, vous pouvez combiner le rappel d’avertissement avec une inspection post‑chargement :

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Astuce :** Si vous trouvez des runs qui référencent encore la police manquante, vous pouvez les remplacer à la volée  :

```java
font.setName("Arial"); // fallback
```

Ainsi vous garantissez un résultat visuel cohérent, même si l'avertissement original a été supprimé.

## Pièges courants et comment les éviter

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Oublier de définir le rappel** | `LoadOptions` utilise par défaut un rappel no‑op, donc les avertissements disparaissent. | Appelez toujours `loadOptions.setWarningCallback(...)` avant le chargement. |
| **Utiliser le mauvais type d'avertissement** | `WarningType.SUBSTITUTED_FONT` est le seul enum qui signale les polices manquantes. | Filtrez exactement sur `WarningType.SUBSTITUTED_FONT` ; les autres types (p. ex., `UNKNOWN_FILE_FORMAT`) ne sont pas liés. |
| **Coder en dur les chemins de fichiers** | Fonctionne localement mais échoue dans les pipelines CI/CD. | Utilisez un chemin relatif ou passez l'emplacement du fichier en argument de ligne de commande. |
| **Ignorer les polices Unicode** | Certaines polices manquantes ne posent problème que pour certains caractères. | Testez avec un document contenant l'ensemble complet de caractères que vous prévoyez de prendre en charge. |
| **Exécuter sur un serveur sans tête sans configuration de polices** | Le serveur peut ne disposer d'aucune police de secours, entraînant des substitutions inattendues. | Installez un jeu minimal de polices courantes (Arial, Times New Roman) sur le serveur. |

## Étendre la solution

Maintenant que vous pouvez **capturer les avertissements de substitution de police**, vous pourriez vouloir :

* **Consigner les avertissements dans un fichier** – remplacez `System.out.println` par un logger comme SLF4J.
* **Lancer une exception** – utile dans les pipelines automatisés où une police manquante doit faire échouer la construction  :

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Installer automatiquement les polices manquantes** – téléchargez le TTF/OTF requis à l'exécution et ajoutez‑le au `GraphicsEnvironment` Java. C’est un scénario plus avancé, mais tout à fait possible.

## Diagramme (optionnel)

![Diagramme du flux de capture des avertissements de substitution de police montrant LoadOptions → WarningCallback → sortie console](capture-font-substitution-warnings-diagram.png)

*Texte alternatif :* « Diagramme du flux de capture des avertissements de substitution de police illustrant comment Aspose.Words dirige les avertissements de police manquante vers un rappel personnalisé. »

## Conclusion

Nous venons de couvrir comment **capturer les avertissements de substitution de police** et **détecter les polices manquantes** lors du chargement de documents Word avec Aspose.Words for Java. En configurant un objet `LoadOptions` et en implémentant un petit `IWarningCallback`, vous obtenez une visibilité complète sur le processus de secours de police, vous permettant de consigner, remplacer ou interrompre en cas de polices manquantes.

En résumé : définissez le rappel, filtrez sur `SUBSTITUTED_FONT`, chargez le document, et gérez la sortie selon les besoins de votre application. À partir de là, vous pouvez étendre aux frameworks de journalisation, aux vérifications CI, ou même à la fourniture automatisée de polices.

Vous voulez aller plus loin ? Essayez :

* **Incorporer les polices** directement dans le document enregistré (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` avec `FontEmbeddingMode.EMBED_ALL`).
* **Générer un PDF** après avoir corrigé les polices, en veillant à ce que le rendu final soit exactement comme prévu.
* **Analyser un dossier complet** de documents à la recherche de polices manquantes et produire un rapport récapitulatif.

C’est tout pour le moment — bon codage, et que vos documents s’affichent toujours avec la bonne police !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}