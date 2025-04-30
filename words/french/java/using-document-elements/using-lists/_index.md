---
"description": "Apprenez à utiliser les listes dans Aspose.Words pour Java grâce à ce tutoriel étape par étape. Organisez et formatez efficacement vos documents."
"linktitle": "Utilisation des listes"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Utilisation des listes dans Aspose.Words pour Java"
"url": "/fr/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des listes dans Aspose.Words pour Java


Dans ce tutoriel complet, nous explorerons comment utiliser efficacement les listes dans Aspose.Words pour Java, une API puissante permettant de manipuler des documents Microsoft Word par programmation. Les listes sont essentielles pour structurer et organiser le contenu de vos documents. Nous aborderons deux aspects clés de l'utilisation des listes : le redémarrage des listes à chaque section et la spécification des niveaux de liste. C'est parti !

## Introduction à Aspose.Words pour Java

Avant de commencer à travailler avec des listes, découvrons Aspose.Words pour Java. Cette API fournit aux développeurs les outils nécessaires pour créer, modifier et manipuler des documents Word dans un environnement Java. C'est une solution polyvalente pour des tâches allant de la simple génération de documents à la mise en forme et à la gestion de contenu complexes.

### Configuration de votre environnement

Pour commencer, assurez-vous qu'Aspose.Words pour Java est installé et configuré dans votre environnement de développement. Vous pouvez le télécharger. [ici](https://releases.aspose.com/words/java/). 

## Redémarrage des listes à chaque section

Dans de nombreux cas, vous devrez peut-être redémarrer les listes à chaque section de votre document. Cela peut être utile pour créer des documents structurés comportant plusieurs sections, tels que des rapports, des manuels ou des articles universitaires.

Voici un guide étape par étape sur la façon d'y parvenir en utilisant Aspose.Words pour Java :

### Initialisez votre document : 
Commencez par créer un nouvel objet de document.

```java
Document doc = new Document();
```

### Ajouter une liste numérotée : 
Ajoutez une liste numérotée à votre document. Nous utiliserons le style de numérotation par défaut.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Configurer les paramètres de la liste : 
\Permettre à la liste de redémarrer à chaque section.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Configuration de DocumentBuilder : 
Créez un DocumentBuilder pour ajouter du contenu à votre document.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Ajouter des éléments de liste : 
Utilisez une boucle pour ajouter des éléments de liste à votre document. Nous insérerons un saut de section après le 15e élément.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Enregistrez votre document : 
Enregistrez le document avec les options souhaitées.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

En suivant ces étapes, vous pouvez créer des documents avec des listes qui redémarrent à chaque section, en conservant une structure de contenu claire et organisée.

## Spécification des niveaux de liste

Aspose.Words pour Java permet de spécifier des niveaux de liste, ce qui est particulièrement utile lorsque vous avez besoin de différents formats de liste dans votre document. Voyons comment procéder :

### Initialisez votre document : 
Créer un nouvel objet de document.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Créer une liste numérotée : 
Appliquez un modèle de liste numérotée à partir de Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Spécifier les niveaux de liste : 
Parcourez différents niveaux de liste et ajoutez du contenu.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Créer une liste à puces : 
Maintenant, créons une liste à puces.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Spécifier les niveaux de liste à puces : 
Similaire à la liste numérotée, spécifiez les niveaux et ajoutez du contenu.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Formatage de la liste d'arrêt : 
Pour arrêter le formatage de la liste, définissez la liste sur null.

```java
builder.getListFormat().setList(null);
```

### Enregistrez votre document : 
Enregistrez le document.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

En suivant ces étapes, vous pouvez créer des documents avec des niveaux de liste personnalisés, vous permettant de contrôler la mise en forme des listes dans vos documents.

## Code source complet
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection sera écrit uniquement si la conformité est supérieure à OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Créez une liste numérotée basée sur l'un des modèles de liste Microsoft Word
        // et l'appliquer au paragraphe actuel du générateur de documents.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Il y a neuf niveaux dans cette liste, essayons-les tous.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Créez une liste à puces basée sur l'un des modèles de liste Microsoft Word
        // et l'appliquer au paragraphe actuel du générateur de documents.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // C'est une façon d'arrêter le formatage des listes.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Créez une liste basée sur un modèle.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Pour réutiliser la première liste, nous devons recommencer la numérotation en créant une copie du formatage de la liste d'origine.
        List list2 = doc.getLists().addCopy(list1);
        // Nous pouvons modifier la nouvelle liste de n'importe quelle manière, y compris en définissant un nouveau numéro de départ.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Conclusion

Félicitations ! Vous avez appris à utiliser efficacement les listes dans Aspose.Words pour Java. Les listes sont essentielles pour organiser et présenter le contenu de vos documents. Que vous ayez besoin de redémarrer les listes à chaque section ou de spécifier des niveaux de liste, Aspose.Words pour Java vous offre les outils nécessaires pour créer des documents de qualité professionnelle.

Vous pouvez désormais utiliser ces fonctionnalités en toute confiance pour optimiser la création et la mise en forme de vos documents. Pour toute question ou besoin d'aide, n'hésitez pas à contacter le [Forum communautaire Aspose](https://forum.aspose.com/) pour le soutien.

## FAQ

### Comment installer Aspose.Words pour Java ?
Vous pouvez télécharger Aspose.Words pour Java à partir de [ici](https://releases.aspose.com/words/java/) et suivez les instructions d'installation dans la documentation.

### Puis-je personnaliser le format de numérotation des listes ?
Oui, Aspose.Words pour Java offre de nombreuses options de personnalisation des formats de numérotation des listes. Consultez la documentation de l'API pour plus de détails.

### Aspose.Words pour Java est-il compatible avec les dernières normes de documents Word ?
Oui, vous pouvez configurer Aspose.Words pour Java pour qu'il soit conforme à diverses normes de documents Word, notamment ISO 29500.

### Puis-je générer des documents complexes avec des tableaux et des images en utilisant Aspose.Words pour Java ?
Absolument ! Aspose.Words pour Java prend en charge la mise en forme avancée des documents, notamment les tableaux, les images et bien plus encore. Consultez la documentation pour des exemples.

### Où puis-je obtenir une licence temporaire pour Aspose.Words pour Java ?
Vous pouvez obtenir un permis temporaire [ici](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}