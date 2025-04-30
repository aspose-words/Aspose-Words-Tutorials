---
"description": "Apprenez à générer un tableau à partir d'un DataTable avec Aspose.Words pour Java. Créez facilement des documents Word professionnels avec des tableaux formatés."
"linktitle": "Générer un tableau à partir d'une table de données"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Générer un tableau à partir d'une table de données"
"url": "/fr/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Générer un tableau à partir d'une table de données

## Introduction

Créer dynamiquement des tables à partir de sources de données est une tâche courante dans de nombreuses applications. Que vous génériez des rapports, des factures ou des synthèses de données, pouvoir renseigner une table avec des données par programmation peut vous faire gagner beaucoup de temps et d'efforts. Dans ce tutoriel, nous allons découvrir comment générer une table à partir d'une DataTable avec Aspose.Words pour Java. Nous décomposerons le processus en étapes faciles à comprendre, vous assurant ainsi une compréhension claire de chaque partie.

## Prérequis

Avant de plonger dans le code, assurons-nous que vous disposez de tout ce dont vous avez besoin pour commencer :

1. Kit de développement Java (JDK) : Assurez-vous que le JDK est installé sur votre machine. Vous pouvez le télécharger depuis le [Site Web d'Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. Aspose.Words pour Java : vous aurez besoin de la bibliothèque Aspose.Words. Vous pouvez télécharger la dernière version ici. [Page des sorties d'Aspose](https://releases.aspose.com/words/java/).

3. IDE : un environnement de développement intégré (IDE) comme IntelliJ IDEA ou Eclipse facilitera le codage.

4. Connaissances de base de Java : la familiarité avec les concepts de programmation Java vous aidera à mieux comprendre les extraits de code.

5. Exemple de données : Pour ce tutoriel, nous utiliserons un fichier XML nommé « Liste de personnes.xml » pour simuler une source de données. Vous pouvez créer ce fichier avec des exemples de données à des fins de test.

## Étape 1 : Créer un nouveau document

Tout d'abord, nous devons créer un nouveau document où notre tableau sera hébergé. C'est le canevas de notre travail.

```java
Document doc = new Document();
```

Ici, nous instancions un nouveau `Document` objet. Cela servira de document de travail où nous construirons notre table.

## Étape 2 : Initialiser DocumentBuilder

Ensuite, nous utiliserons le `DocumentBuilder` classe, qui nous permet de manipuler le document plus facilement.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le `DocumentBuilder` L'objet fournit des méthodes pour insérer des tableaux, du texte et d'autres éléments dans le document.

## Étape 3 : Définir l’orientation de la page

Comme nous nous attendons à ce que notre tableau soit large, nous allons définir l’orientation de la page sur paysage.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Cette étape est cruciale car elle garantit que notre tableau s'adapte parfaitement à la page sans être coupé.

## Étape 4 : Charger les données à partir de XML

Maintenant, nous devons charger nos données du fichier XML dans un `DataTable`C'est de là que proviennent nos données.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

Ici, nous lisons le fichier XML et récupérons la première table de l'ensemble de données. `DataTable` contiendra les données que nous souhaitons afficher dans notre document.

## Étape 5 : Importer la table depuis DataTable

Vient maintenant la partie passionnante : importer nos données dans le document sous forme de tableau.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

Nous appelons la méthode `importTableFromDataTable`, en passant le `DocumentBuilder`, notre `DataTable`, et un booléen pour indiquer s'il faut inclure les en-têtes de colonne.

## Étape 6 : Styliser la table

Une fois que nous avons notre table, nous pouvons appliquer un peu de style pour lui donner une belle apparence.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Ce code applique un style prédéfini au tableau, améliorant son attrait visuel et sa lisibilité.

## Étape 7 : supprimer les cellules indésirables

Si vous avez des colonnes que vous ne souhaitez pas afficher, comme une colonne d'image, vous pouvez facilement les supprimer.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Cette étape garantit que notre tableau affiche uniquement les informations pertinentes.

## Étape 8 : Enregistrer le document

Enfin, nous sauvegardons notre document avec le tableau généré.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Cette ligne enregistre le document dans le répertoire spécifié, vous permettant de consulter les résultats.

## La méthode importTableFromDataTable

Regardons de plus près le `importTableFromDataTable` méthode. Cette méthode est responsable de la création de la structure de la table et de son remplissage avec des données.

### Étape 1 : Démarrer la table

Tout d’abord, nous devons démarrer un nouveau tableau dans le document.

```java
Table table = builder.startTable();
```

Ceci initialise une nouvelle table dans notre document.

### Étape 2 : Ajouter des en-têtes de colonnes

Si nous voulons inclure des en-têtes de colonnes, nous vérifions le `importColumnHeadings` drapeau.

```java
if (importColumnHeadings) {
    // Conserver le formatage d'origine
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Définir la mise en forme des titres
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Insérer les noms de colonnes
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Restaurer le formatage d'origine
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

Ce bloc de code formate la ligne d'en-tête et insère les noms des colonnes à partir du `DataTable`.

### Étape 3 : Remplir le tableau avec des données

Maintenant, nous parcourons chaque ligne du `DataTable` pour insérer des données dans le tableau.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

Dans cette section, nous traitons différents types de données, en formatant les dates de manière appropriée tout en insérant d'autres données sous forme de texte.

### Étape 4 : Terminer la table

Enfin, nous terminons le tableau une fois toutes les données insérées.

```java
builder.endTable();
```

Cette ligne marque la fin de notre tableau, permettant à `DocumentBuilder` pour savoir que nous en avons terminé avec cette section.

## Conclusion

Et voilà ! Vous avez appris à générer un tableau à partir d'un DataTable avec Aspose.Words pour Java. En suivant ces étapes, vous pourrez facilement créer des tableaux dynamiques dans vos documents à partir de différentes sources de données. Que vous génériez des rapports ou des factures, cette méthode simplifiera votre flux de travail et améliorera votre processus de création de documents.

## FAQ

### Qu'est-ce qu'Aspose.Words pour Java ?
Aspose.Words pour Java est une bibliothèque puissante permettant de créer, de manipuler et de convertir des documents Word par programmation.

### Puis-je utiliser Aspose.Words gratuitement ?
Oui, Aspose propose une version d'essai gratuite. Vous pouvez la télécharger ici. [ici](https://releases.aspose.com/).

### Comment styliser des tableaux dans Aspose.Words ?
Vous pouvez appliquer des styles à l’aide d’identifiants de style prédéfinis et d’options fournies par la bibliothèque.

### Quels types de données puis-je insérer dans des tableaux ?
Vous pouvez insérer différents types de données, notamment du texte, des nombres et des dates, qui peuvent être formatés en conséquence.

### Où puis-je obtenir de l'aide pour Aspose.Words ?
Vous pouvez trouver du soutien et poser des questions sur le [Forum Aspose](https://forum.aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}