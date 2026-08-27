---
category: general
date: 2026-01-11
description: Apprenez à capturer les avertissements de substitution de police avec
  Aspose.Words pour Java. Ce tutoriel étape par étape couvre également les LoadOptions
  et les rappels d’avertissement.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: fr
og_description: Capturez les avertissements de substitution de police avec Aspose.Words
  pour Java. Suivez ce guide pour configurer LoadOptions et un rappel d’avertissement
  afin de charger les documents de manière fiable.
og_title: Capturer les avertissements de substitution de police en Java – Tutoriel
  complet
tags:
- Aspose.Words
- Java
- Document Processing
title: Capturer les avertissements de substitution de police en Java avec Aspose.Words
  – Guide complet
url: /fr/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture des avertissements de substitution de police – Tutoriel complet Java

Vous avez déjà eu besoin de **capturer les avertissements de substitution de police** lors de l'ouverture d'un document Word avec des polices manquantes ? C’est un problème fréquent, surtout lorsque vous générez des PDF ou imprimez sur un serveur qui ne possède pas toutes les polices installées. Bonne nouvelle ? Aspose.Words for Java rend cela simple — il suffit de configurer un objet `LoadOptions` et d’y brancher un rappel d’avertissement. Dans ce guide, vous verrez exactement comment faire, pourquoi c’est important, et à quoi vous attendre lorsque l’avertissement se déclenche.

Nous aborderons également des sujets connexes comme **Aspose.Words font substitution**, l’utilisation d’un **Java warning callback**, et les meilleures pratiques pour **LoadOptions usage**. À la fin, vous disposerez d’un extrait prêt à l’exécution qui consigne chaque événement de police manquante, afin que votre traitement en aval ne vous surprenne jamais.

## Prérequis

- Java 17 (ou tout JDK récent) installé et configuré.
- Aspose.Words for Java 23.10 (ou plus récent) sur votre classpath.
- Un document Word qui référence une police que vous n’avez pas localement (par ex., `DocWithMissingFont.docx`).
- Familiarité de base avec les blocs try/catch Java — rien de compliqué.

Si l’un de ces points vous est inconnu, faites une pause et installez la bibliothèque depuis Maven Central :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Maintenant que les bases sont en place, passons au code.

## Étape 1 : Configurer un rappel d’avertissement pour **capturer les avertissements de substitution de police**

La première chose dont vous avez besoin est un rappel que Aspose.Words invoquera chaque fois qu’il rencontre une police manquante. C’est ici que nous **capturons les avertissements de substitution de police**. Le rappel implémente l’interface `IWarningCallback` et vérifie le `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Pourquoi c’est important :** Sans rappel, Aspose.Words remplace silencieusement la police manquante par une police par défaut, et vous ne savez jamais que le rendu visuel a changé. En capturant l’avertissement, vous pouvez consigner, alerter, ou même interrompre le chargement si la police manquante est critique.

## Étape 2 : Configurer **LoadOptions** et enregistrer le rappel

Nous créons maintenant une instance de `LoadOptions` et y attachons notre `FontWarningCallback`. Cette étape est essentielle pour **LoadOptions usage** et garantit que chaque chargement de document passe par le même filtre d’avertissement.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Astuce :** Vous pouvez réutiliser le même objet `LoadOptions` pour plusieurs documents, ce qui économise quelques lignes de code répétitif et garantit une gestion cohérente des **document loading warnings** dans votre application.

## Étape 3 : Charger le document et observer la sortie

Avec le rappel configuré, chargez simplement votre fichier Word. Si le document référence une police qui n’est pas installée, le rappel se déclenchera et affichera les détails dans la console.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Sortie console attendue

En supposant que `DocWithMissingFont.docx` référence la police manquante *« Comic Sans MS »*, vous verrez quelque chose comme :

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Si le document ne contient **aucune police manquante**, la console affichera uniquement la ligne finale, confirmant que votre rappel n’a généré aucun faux positif.

## Étape 4 : Gestion des cas limites et des pièges courants

### Polices manquantes multiples

Si un document utilise plusieurs polices indisponibles, le rappel s’exécute une fois par police. Vous recevrez une série de messages, chacun avec son propre `source` et `description`. Aucun code supplémentaire n’est requis — assurez‑vous simplement que votre système de journalisation peut gérer des appels successifs rapides.

### Suppression des avertissements

Dans de rares cas, vous pourriez vouloir ignorer certaines substitutions (par ex., vous savez qu’un remplacement particulier est acceptable). Étendez la logique du rappel :

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Sécurité des threads

`LoadOptions` d’Aspose.Words n’est pas thread‑safe par défaut. Si vous chargez des documents en parallèle, créez une instance distincte de `LoadOptions` par thread, ou synchronisez le rappel pour éviter les conditions de concurrence.

## Étape 5 : Vérifier la police substituée dans le document résultant

Après le chargement, vous pouvez vouloir confirmer que la substitution a bien eu lieu. L’API vous permet d’itérer sur tous les runs et d’inspecter le nom de police effectif :

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Cet extrait affiche chaque run de texte avec sa police finale. C’est une vérification de bon sens pratique lorsque vous construisez des pipelines automatisés de conversion PDF.

## Exemple complet fonctionnel

En rassemblant tous les éléments, voici le programme complet, prêt à l’exécution :

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Enregistrez ceci sous le nom `FontSubstitutionInfo.java`, compilez avec `javac`, et exécutez `java FontSubstitutionInfo`. Vous devriez voir les messages d’avertissement (le cas échéant) suivis de la liste des runs et de leurs polices finales.

## Aide visuelle

![Capture d'écran de la sortie console montrant les avertissements de substitution de police](/images/font-substitution-warning.png "exemple d'avertissement de substitution de police")

*Texte alternatif :* **capture font substitution warnings** – sortie console après le chargement d’un document avec des polices manquantes.

## Conclusion

Vous savez maintenant comment **capturer les avertissements de substitution de police** avec Aspose.Words for Java. En configurant un objet `LoadOptions` et en fournissant un `IWarningCallback` personnalisé, vous obtenez une visibilité totale sur tout événement de police manquante qui pourrait autrement affecter silencieusement l’apparence de votre document. Cette technique s’intègre directement à la gestion de **Aspose.Words font substitution**, assure des **document loading warnings** fiables, et vous offre la flexibilité de consigner, alerter ou interrompre selon vos règles métier.

### Et après ?

- Explorer les modèles de **Java warning callback** pour d’autres types d’avertissements (par ex., `DEPRECATED_FEATURE`).
- Combiner cette approche avec la **PDF conversion** pour garantir que les polices substituées ne cassent pas la mise en page.
- Approfondir l’utilisation de **LoadOptions usage** — expérimenter avec `Password`, `Encoding` et `ResourceLoadingCallback` pour des scénarios plus avancés.

N’hésitez pas à ajuster le rappel, à diriger les avertissements vers un framework de journalisation, ou même à lancer une exception personnalisée si une police critique est manquante. Les possibilités sont infinies, et vous disposez maintenant d’une base solide pour construire.

Bon codage, et que vos documents s’affichent toujours exactement comme vous le souhaitez !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}