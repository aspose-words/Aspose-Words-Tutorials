---
title: Ajoutez un champ de formulaire case à cocher à un document Word avec Aspose.Words for .NET
weight: 210
limit:
description: Apprenez comment ajouter programmétiquement un champ de formulaire case à cocher à un nouveau document Word en utilisant Aspose.Words for .NET et enregistrer le fichier.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajoutez un champ de formulaire case à cocher à un document Word avec Aspose.Words
Ce tutoriel montre comment créer un nouveau document Word et utiliser le DocumentBuilder d'Aspose.Words for .NET pour insérer un champ de formulaire case à cocher. En suivant les étapes, vous verrez le code exact nécessaire pour ajouter l'élément interactif, puis enregistrer le document dans un fichier. C’est un moyen rapide de créer programmétiquement des fichiers Word simples avec des formulaires activés.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Que représente le quatrième argument (0) dans InsertCheckBox ?**
A: Il spécifie la taille visuelle de la case à cocher en points ; une valeur de 0 indique à Aspose.Words d’utiliser la taille par défaut.

**Q: Puis-je insérer plusieurs cases à cocher avec le même nom ?**
A: Non – chaque nom de champ de formulaire doit être unique ; essayer d’insérer une autre case à cocher nommée "CheckBox" déclenchera une ArgumentException.

**Q: Comment ajouter une case à cocher à un document existant plutôt qu’à un nouveau ?**
A: Chargez d’abord le document (par ex., `Document doc = new Document("Existing.docx");`) puis créez un DocumentBuilder pour ce document et appelez `InsertCheckBox` à la position du curseur souhaitée.

**Q: Comment puis‑je lire l’état de la case à cocher insérée après l’enregistrement du document ?**
A: Récupérez le champ de formulaire via `doc.Range.FormFields["CheckBox"]` et examinez sa propriété `Checked` pour voir s’il était coché.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}