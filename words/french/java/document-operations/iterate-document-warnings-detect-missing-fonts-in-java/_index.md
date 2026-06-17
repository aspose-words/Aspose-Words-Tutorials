---
category: general
date: 2026-04-28
description: Parcourir les avertissements du document dans un fichier Word pour détecter
  les polices manquantes, récupérer les noms des polices manquantes et afficher les
  détails des polices manquantes à l’aide d’Aspose.Words pour Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: fr
og_description: Parcourir les avertissements du document pour détecter les polices
  manquantes, récupérer leurs noms et afficher leurs détails avec un exemple complet
  en Java.
og_title: 'Parcourir les avertissements du document : détecter les polices manquantes
  en Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Parcourir les avertissements de document : détecter les polices manquantes
  en Java'
url: /fr/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Itérer les avertissements de document – Détecter les polices manquantes en Java

Vous avez déjà eu besoin d'**itérer les avertissements de document** en ouvrant un fichier Word et vous vous êtes demandé quelles polices manquaient ? Vous n'êtes pas seul. Les polices manquantes peuvent altérer l’apparence d’un rapport, et sans moyen de les repérer vous pourriez livrer un document qui ne ressemble en rien à l’original.  

Dans ce tutoriel, nous vous montrerons comment **détecter les polices manquantes** en chargeant un document Word, en itérant ses avertissements, en récupérant les noms des polices manquantes, puis en affichant ces informations — le tout avec Aspose.Words for Java.  

Nous couvrirons tout, de la toute première ligne de code à la sortie console attendue, afin que vous puissiez copier‑coller une solution fonctionnelle dans votre projet dès maintenant. Aucun document supplémentaire n’est requis.

## Prérequis

- Java 8 ou version supérieure installé.
- Bibliothèque Aspose.Words for Java (la dernière version au 28‑04‑2026).
- Un fichier Word pouvant contenir des polices non installées sur votre machine (par ex., `doc-with-missing-font.docx`).

Si vous avez déjà tout cela, tant mieux — vous êtes prêt à **load word document** et à commencer l’itération.

## Étape 1 – Charger le document Word avec les options par défaut

Avant de pouvoir **itérer les avertissements de document**, le fichier doit être chargé en mémoire. Aspose.Words vous le permet avec un simple appel au constructeur. Utiliser les `LoadOptions` par défaut suffit généralement, mais nous montrerons la création explicite pour plus de clarté.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Pourquoi c’est important :**  
> Le chargement du document incite Aspose.Words à analyser le fichier à la recherche de ressources qu’il ne peut pas résoudre, comme des polices non installées localement. Ces problèmes sont stockés sous forme d'**avertissements**, que nous **itérerons** dans l’étape suivante.

## Étape 2 – Itérer les avertissements de document pour trouver les problèmes de police

Voici le cœur de la solution : nous parcourons chaque avertissement que la bibliothèque a collecté lors du chargement. Les objets `WarningInfo` nous indiquent ce qui a échoué, et nous pouvons filtrer les `FontSubstitutionWarning` pour **détecter les polices manquantes**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Astuce :** La vérification `instanceof` garantit que nous ne traitons que les avertissements liés aux polices, en ignorant les autres, comme les problèmes de chargement d’images. Cela rend la boucle efficace et concentre la sortie sur les polices dont vous avez réellement besoin pour **retrieve missing font**.

### Sortie console attendue

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Si le document ne contient aucune police manquante, la boucle se termine simplement sans rien afficher—aucun **print missing font**.

## Étape 3 – Pourquoi ne pas simplement attraper une exception ?

Vous pourriez vous demander : « Pourquoi ne pas entourer l’appel `new Document(...)` d’un try‑catch et rechercher une exception ? » La réponse est double :

1. **Informations granulaire :** Les exceptions indiquent seulement qu’une opération a échoué. Les avertissements donnent le nom exact de la police et la police de secours choisie par Aspose.Words.
2. **Problèmes non fatals :** Les polices manquantes sont généralement non fatales ; le document se charge tout de même, mais la fidélité visuelle est compromise. En **itérant les avertissements de document**, vous conservez la possibilité de traiter le reste du fichier.

## Étape 4 – Extension de l’exemple : Collecter les polices manquantes dans une liste

Parfois, vous avez besoin des polices manquantes pour un traitement ultérieur—peut‑être les incorporer ou alerter l’utilisateur via l’UI. Voici une petite modification qui rassemble les noms dans un `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Vous disposez ainsi d’un moyen propre de **retrieve missing font** de façon programmatique, que vous pouvez transmettre à un module de reporting ou à un assistant d’installation de polices.

## Étape 5 – Considérations pratiques

- **Substitutions multiples :** Une même police manquante peut être remplacée par différentes polices à différents endroits du document. La liste d’avertissements contiendra chaque occurrence, ce qui peut entraîner des entrées dupliquées.
- **Performance :** Le chargement de documents très volumineux peut générer des milliers d’avertissements. Si vous ne vous intéressez qu’aux polices, filtrez dès le début comme indiqué pour garder la boucle rapide.
- **Polices multiplateformes :** Sous Linux, la police de substitution par défaut est souvent *Liberation Sans*. Sous Windows, il peut s’agir de *Arial*. Connaître la police de secours vous aide à décider si vous devez fournir des polices personnalisées avec votre application.

## Étape 6 – Aide visuelle

Voici une capture d’écran de la sortie console (le texte alternatif inclut le mot‑clé principal pour le SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Texte alternatif :* *exemple d’itération des avertissements de document affichant les noms des polices manquantes et les détails de substitution.*

## Conclusion

Vous venez d’apprendre comment **itérer les avertissements de document** avec Aspose.Words for Java, **détecter les polices manquantes**, **load word document** en toute sécurité, **retrieve missing font** et **print missing font** dans la console. Le snippet complet fonctionne tel quel, et vous pouvez l’adapter pour l’enregistrer dans un fichier, afficher une boîte de dialogue UI, ou même incorporer automatiquement les polices manquantes.

Ensuite, vous voudrez peut‑être explorer comment **load word document** avec des sources de polices personnalisées (par ex., en ajoutant un dossier de polices d’entreprise) ou comment incorporer directement les polices manquantes dans le fichier afin de préserver la mise en page sur toutes les machines. Ces deux sujets s’appuient naturellement sur ce que nous venons de couvrir.

Bon codage, et que vos PDF conservent toujours exactement l’apparence que vous avez prévue !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}