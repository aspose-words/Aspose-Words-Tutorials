---
"description": "Apprenez à ajouter des formes de groupe à des documents Word à l’aide d’Aspose.Words pour .NET avec ce didacticiel complet, étape par étape."
"linktitle": "Ajouter une forme de groupe"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Ajouter une forme de groupe"
"url": "/fr/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une forme de groupe

## Introduction

Créer des documents complexes avec des éléments visuels riches peut parfois s'avérer complexe, surtout avec des formes de groupe. Mais pas d'inquiétude ! Aspose.Words pour .NET simplifie ce processus, le rendant simple comme bonjour. Dans ce tutoriel, nous vous guiderons pas à pas pour ajouter des formes de groupe à vos documents Word. Prêt à vous lancer ? C'est parti !

## Prérequis

Avant de commencer, assurez-vous d’avoir les éléments suivants :

1. Aspose.Words pour .NET : vous pouvez le télécharger à partir du [Page de publication d'Aspose](https://releases.aspose.com/words/net/).
2. Environnement de développement : Visual Studio ou tout autre IDE compatible avec .NET.
3. Compréhension de base de C# : la familiarité avec la programmation C# est un plus.

## Importer des espaces de noms

Pour commencer, nous devons importer les espaces de noms nécessaires dans notre projet. Ces espaces donnent accès aux classes et méthodes nécessaires à la manipulation de documents Word avec Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Étape 1 : Initialiser le document

Commençons par initialiser un nouveau document Word. Imaginez que vous créez une zone vierge sur laquelle vous ajouterez vos formes de groupe.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Ici, `EnsureMinimum()` ajoute un ensemble minimal de nœuds requis pour le document.

## Étape 2 : Créer l'objet GroupShape

Ensuite, nous devons créer un `GroupShape` Objet. Cet objet servira de conteneur pour d'autres formes, nous permettant de les regrouper.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Étape 3 : Ajouter des formes au GroupShape

Maintenant, ajoutons des formes individuelles à notre `GroupShape` conteneur. Nous commencerons par une forme de bordure d'accentuation, puis ajouterons une forme de bouton d'action.

### Ajout d'une forme de bordure d'accentuation

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

Cet extrait de code crée une forme de bordure d'accentuation avec une largeur et une hauteur de 100 unités et l'ajoute au `GroupShape`.

### Ajout d'une forme de bouton d'action

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

Ici, nous créons une forme de bouton d'action, la positionnons et l'ajoutons à notre `GroupShape`.

## Étape 4 : Définir les dimensions du GroupShape

Pour garantir que nos formes s'intègrent bien dans le groupe, nous devons définir les dimensions de l' `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

Cela définit la largeur et la hauteur du `GroupShape` comme 200 unités et définit la taille des coordonnées en conséquence.

## Étape 5 : Insérer la forme de groupe dans le document

Maintenant, insérons notre `GroupShape` dans le document en utilisant `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` fournit un moyen simple d'ajouter des nœuds, y compris des formes, au document.

## Étape 6 : Enregistrer le document

Enfin, enregistrez le document dans le répertoire spécifié.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Et voilà ! Votre document avec formes de groupe est prêt.

## Conclusion

Ajouter des formes de groupe à vos documents Word n'est pas forcément compliqué. Avec Aspose.Words pour .NET, créez et manipulez facilement des formes, rendant vos documents plus attrayants et fonctionnels. Suivez les étapes de ce tutoriel et devenez un pro en un rien de temps !

## FAQ

### Puis-je ajouter plus de deux formes à un GroupShape ?
Oui, vous pouvez ajouter autant de formes que vous le souhaitez à un `GroupShape`Utilisez simplement le `AppendChild` méthode pour chaque forme.

### Est-il possible de styliser les formes dans un GroupShape ?
Absolument ! Chaque forme peut être stylisée individuellement grâce aux propriétés disponibles dans le `Shape` classe.

### Comment positionner le GroupShape dans le document ?
Vous pouvez positionner le `GroupShape` en définissant son `Left` et `Top` propriétés.

### Puis-je ajouter du texte aux formes dans GroupShape ?
Oui, vous pouvez ajouter du texte aux formes en utilisant le `AppendChild` méthode pour ajouter un `Paragraph` contenant `Run` nœuds avec texte.

### Est-il possible de regrouper des formes de manière dynamique en fonction des entrées de l'utilisateur ?
Oui, vous pouvez créer et regrouper dynamiquement des formes en fonction des entrées de l'utilisateur en ajustant les propriétés et les méthodes en conséquence.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}