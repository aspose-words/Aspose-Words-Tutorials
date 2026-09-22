---
title: Ajoutez un champ de formulaire Combo Box à un document Word avec Aspose.Words for .NET
weight: 310
limit:
description: Apprenez à ajouter un champ de formulaire combo box avec des éléments prédéfinis à un document Word en utilisant Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajoutez un champ de formulaire Combo Box à un document Word avec Aspose.Words
Ce tutoriel montre comment utiliser le DocumentBuilder d'Aspose.Words for .NET pour créer un nouveau document Word et insérer un champ de formulaire combo box rempli d'éléments prédéfinis. En suivant le code étape par étape, vous verrez comment configurer les options de la combo box puis enregistrer le document pour une utilisation dans des formulaires interactifs.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: Que représente le tableau `items` passé à `InsertComboBox` ?**
A: Il définit la liste de chaînes qui apparaissent comme options sélectionnables dans le menu déroulant de la combo box.

**Q: Comment puis‑je changer l'élément sélectionné par défaut lorsque le document est ouvert ?**
A: Définissez le troisième argument (`selectedIndex`) de `InsertComboBox` à l'index basé sur zéro de l'élément par défaut souhaité (par ex., `2` pour \"Three\").

**Q: Est‑il possible de placer la combo box à un emplacement spécifique dans le document ?**
A: Oui — déplacez le curseur du `DocumentBuilder` à l'endroit souhaité en utilisant des méthodes comme `MoveToParagraph`, `InsertParagraph` ou `Write` avant d'appeler `InsertComboBox`.

**Q: Quel format de fichier est créé par ce code et peut‑il être ouvert dans les versions antérieures de Word ?**
A: Le code enregistre un fichier `.docx`, qui peut être ouvert par Word 2007 et versions ultérieures, ainsi que par toute application prenant en charge le format OpenXML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}