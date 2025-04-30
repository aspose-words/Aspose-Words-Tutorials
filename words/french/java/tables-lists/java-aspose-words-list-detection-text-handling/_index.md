---
"date": "2025-03-28"
"description": "Apprenez à maîtriser la détection de listes, la gestion de texte et bien plus encore avec Aspose.Words pour Java. Ce guide aborde la détection des listes séparées par des espaces, la suppression des espaces, la détermination de l'orientation du document, la désactivation de la détection automatique de la numérotation et la gestion des hyperliens."
"title": "Détection de listes maîtresses et gestion de texte en Java avec Aspose.Words &#58; un guide complet"
"url": "/fr/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Détection de listes principales et gestion de texte en Java avec Aspose.Words : guide complet

## Introduction

Travailler avec des documents en texte brut présente souvent des difficultés pour identifier des données structurées comme des listes, en raison de délimiteurs incohérents et de problèmes de formatage. La bibliothèque Aspose.Words pour Java offre des fonctionnalités performantes pour résoudre ces problèmes, notamment la détection de numérotations contenant des espaces, la suppression des espaces, la détermination de l'orientation du document, la désactivation de la détection automatique de numérotation et la gestion des hyperliens dans les documents texte. Ce tutoriel vous permet de manipuler efficacement des données textuelles avec Aspose.Words.

**Ce que vous apprendrez :**
- Techniques de détection de listes séparées par des espaces
- Méthodes pour supprimer les espaces indésirables du contenu du document
- Approches pour déterminer le sens de lecture d'un fichier texte
- Façons de désactiver la détection automatique de numérotation
- Stratégies pour détecter et gérer les hyperliens dans les documents en texte brut

Passons en revue les prérequis nécessaires avant de mettre en œuvre ces fonctionnalités.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

### Bibliothèques requises :
- **Aspose.Words pour Java**:Version 25.3 ou ultérieure.

### Configuration de l'environnement :
- Assurez-vous que votre environnement de développement prend en charge Maven ou Gradle, car ils sont nécessaires pour gérer les dépendances.

### Prérequis en matière de connaissances :
- Compréhension de base de la programmation Java
- Familiarité avec les systèmes de construction Maven ou Gradle

## Configuration d'Aspose.Words

Pour commencer à utiliser Aspose.Words pour Java dans votre projet, vous devez inclure la dépendance nécessaire. Voici comment :

**Expert :**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle :**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Acquisition de licence

Pour utiliser pleinement Aspose.Words, pensez à obtenir une licence :
- **Essai gratuit**:Disponible pour tester les fonctionnalités.
- **Licence temporaire**:À des fins d'évaluation sans limitation.
- **Achat**:Une licence complète pour une utilisation continue.

Une fois que vous avez votre licence, initialisez-la dans votre application pour débloquer toutes les fonctionnalités de la bibliothèque.

## Guide de mise en œuvre

Décomposons chaque fonctionnalité et voyons comment les implémenter à l’aide d’Aspose.Words pour Java.

### Détecter la numérotation avec des espaces

**Aperçu:** Cette fonctionnalité vous permet d'identifier les listes dans les documents en texte brut qui utilisent des espaces comme délimiteurs.

#### Étape 1 : Charger le document
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### Étape 2 : Valider la détection de la liste
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*Paramètres et méthodes :*
- `setDetectNumberingWithWhitespaces(true)`: Configure l'analyseur pour reconnaître les listes avec des délimiteurs d'espaces.
- `doc.getLists().getCount()`: Récupère le nombre de listes détectées dans le document.

### Couper les espaces de début et de fin

**Aperçu:** Cette fonctionnalité supprime les espaces inutiles au début ou à la fin des lignes dans les documents en texte brut, garantissant ainsi une mise en forme du texte propre.

#### Étape 1 : Configurer les options de chargement
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### Étape 2 : Vérifier le découpage
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*Configurations clés :*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: Supprime les espaces à partir du début des lignes.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`: Supprime les espaces aux fins de ligne.

### Détecter la direction du document

**Aperçu:** Déterminez si un document doit être lu de droite à gauche (RTL), comme pour un texte hébreu ou arabe.

#### Étape 1 : Définir la détection automatique
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### Désactiver la détection automatique de numérotation

**Aperçu:** Empêcher la bibliothèque de détecter et de formater automatiquement les éléments de la liste.

#### Étape 1 : Configurer les options de chargement
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### Détecter les hyperliens dans le texte

**Aperçu:** Identifier et gérer les hyperliens dans les documents en texte brut.

#### Étape 1 : Définir les options de détection
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"} ;
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## Applications pratiques

1. **Systèmes de gestion de contenu (CMS) :** Formatez automatiquement le contenu généré par les utilisateurs dans des listes structurées.
2. **Outils d'extraction de données :** Utilisez la détection de liste pour organiser les données non structurées à des fins d’analyse.
3. **Pipelines de traitement de texte :** Améliorez le prétraitement des documents en réduisant les espaces et en détectant la direction du texte.

## Considérations relatives aux performances

Pour optimiser les performances :
- Chargez des documents avec un minimum d’opérations, en vous concentrant sur les fonctionnalités nécessaires.
- Gérez l'utilisation de la mémoire en traitant les documents volumineux par morceaux lorsque cela est possible.

## Conclusion

En exploitant Aspose.Words pour Java, vous pouvez gérer efficacement les données textuelles dans les documents en texte brut. De la détection des listes séparées par des espaces à la gestion de l'orientation du texte et des hyperliens, ces puissants outils permettent une manipulation robuste des documents. Pour en savoir plus, consultez le [Documentation d'Aspose.Words](https://reference.aspose.com/words/java/) ou essayez un essai gratuit.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}