---
category: general
date: 2026-07-16
description: Le tutoriel cmake build x64 montre comment utiliser CMake pour générer
  une solution Visual Studio 2022 et créer un projet VS sur un hôte 64 bits. Il comprend
  les étapes de définition du répertoire source.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: fr
lastmod: 2026-07-16
og_description: 'cmake build x64 expliqué : apprenez comment définir le répertoire
  source, générer une solution Visual Studio 2022 et compiler un projet VS sur un
  hôte 64 bits.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Guide pas à pas pour générer et construire des solutions
  VS 2022
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: Compilation cmake x64 – Guide complet pour générer et construire des projets
  VS 2022
url: /fr/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Guide complet pour générer et construire des projets VS 2022

Vous vous êtes déjà demandé **comment utiliser CMake** pour produire une solution Visual Studio 64 bits sans perdre patience ? Vous n'êtes pas seul. Dans ce tutoriel, nous parcourrons un workflow **cmake build x64** qui définit le répertoire source, lance le générateur pour Visual Studio 2022, puis construit le projet VS – le tout avec quelques commandes Bash simples.

À la fin du guide, vous disposerez d’un script reproductible que vous pourrez placer dans n’importe quel dépôt, ainsi qu’une bonne compréhension des concepts sous‑jacents pour l’adapter à vos besoins.

---

## Ce que vous allez apprendre

- **Définir le répertoire source** correctement afin que CMake sache où se trouve votre `CMakeLists.txt`.  
- **cmake generate visual studio** – invoquer le générateur Visual Studio 2022 avec les bons indicateurs d’hôte et d’architecture.  
- Effectuer un **cmake build x64** de la solution générée, en sélectionnant éventuellement la configuration Release.  
- Comprendre les pièges courants lorsque vous essayez de **build vs project** sur une machine 64 bits.  

Aucune connaissance préalable de CMake n’est requise ; il vous suffit d’un terminal et d’une installation récente de Visual Studio.

---

## Prérequis

| Prérequis | Pourquoi c’est important |
|-------------|----------------|
| CMake ≥ 3.20 | Prend en charge les indicateurs `-Thost=` et `-Ax64` utilisés pour les builds 64 bits. |
| Visual Studio 2022 (Community, Professional ou Enterprise) | Le générateur `Visual Studio 17 2022` pointe vers cette version. |
| Un shell compatible Bash (Git Bash, WSL, PowerShell avec alias `bash`) | Le script ci‑dessous utilise la syntaxe Bash pour plus de clarté. |
| Arborescence source contenant un `CMakeLists.txt` valide | CMake ne peut pas générer de solution sans ce fichier. |

Si l’un de ces éléments manque, installez‑les d’abord : CMake depuis <https://cmake.org/download/> et VS 2022 via le programme d’installation Microsoft.

---

## Étape 1 – Définir les répertoires source et build (`set source directory`)

Avant d’appeler CMake, vous devez lui indiquer **où** chercher les fichiers du projet. Hard‑coder les chemins rend le script fragile, nous allons donc utiliser des variables d’environnement que vous pourrez ajuster par projet.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Pourquoi c’est important :**  
> CMake considère le *répertoire source* (`SRC_DIR`) comme la racine du projet. Le *répertoire de build* (`BUILD_DIR`) est l’endroit où résident tous les fichiers intermédiaires, les caches et le fichier `.sln` final. Les garder séparés évite de polluer votre arborescence source et rend le nettoyage trivial (`rm -rf "$BUILD_DIR"`).

Vous pouvez remplacer `YOUR_DIRECTORY` par n’importe quel chemin absolu ou relatif ; assurez‑vous simplement que le dossier contient un `CMakeLists.txt`.

---

## Étape 2 – Générer une solution Visual Studio 2022 (`cmake generate visual studio`)

Nous demandons maintenant à CMake de produire une solution VS 2022 ciblant **x64**. Les indicateurs clés sont :

- `-G "Visual Studio 17 2022"` – sélectionne le générateur VS 2022.  
- `-Thost=x64` – indique à CMake que l’*hôte* (l’IDE) s’exécute en processus 64 bits.  
- `-Ax64` – force le projet généré à être construit pour l’architecture x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Que se passe‑t‑il en arrière‑plan ?**  
> CMake lit le `CMakeLists.txt` depuis `$SRC_DIR`, résout tous les appels `add_executable()` et `add_library()`, puis crée un fichier `.sln` et un ensemble de fichiers `.vcxproj` dans `$BUILD_DIR`. Ces projets sont alors prêts à être ouverts dans Visual Studio ou à être construits depuis la ligne de commande.

Si vous exécutez la commande et voyez une longue liste de messages de configuration se terminant par `-- Configuring done` et `-- Generating done`, vous avez réussi l’étape **cmake generate visual studio**.

---

## Étape 3 – Construire la solution générée (`cmake build x64`)

Avec la solution en place, l’étape logique suivante est de la compiler. CMake peut piloter la construction pour vous, en déléguant à MSBuild en arrière‑plan.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Pourquoi utiliser `--config Release` ?**  
> Les projets Visual Studio supportent plusieurs configurations (Debug, Release, RelWithDebInfo, etc.). Spécifier `Release` garantit que les binaires sont optimisés pour la production et que le `.exe` ou `.dll` résultant se trouve sous `Release/` dans l’arbre de build.

Si vous préférez une construction Debug, remplacez `Release` par `Debug`. La commande fonctionne de la même façon, montrant que **how to use CMake** pour différentes configurations n’est qu’une question de changer cet indicateur.

---

## Étape 4 – Vérifier la construction (`build vs project` sanity check)

Une compilation réussie doit vous laisser un exécutable ou une bibliothèque. Vérifions qu’il existe :

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Pièges courants :**  
> - Oublier d’exécuter l’étape du générateur après avoir modifié `CMakeLists.txt` fera échouer cette vérification.  
> - Mélanger des chaînes d’outils 32 bits et 64 bits peut entraîner des erreurs de lien ; gardez toujours `-Ax64` cohérent.  
> - Si vous voyez des erreurs “MSB3073”, cela signifie généralement qu’une étape post‑build (comme la copie de ressources) a échoué — inspectez la sortie pour plus d’indices.

---

## Étape 5 – Nettoyer et relancer (Itérer sur un `cmake build x64`)

En cours de développement, vous aurez souvent besoin de reconstruire à partir de zéro. La façon la plus propre est de supprimer le dossier de build et de recommencer :

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Astuce :**  
> Ajouter `-DCMAKE_BUILD_TYPE=Release` à la commande du générateur est optionnel pour les générateurs multi‑config comme Visual Studio, mais cela peut être pratique lorsque vous passez à un générateur mono‑config tel que Ninja.

---

## Étape 6 – Étendre le script (Scénarios avancés `cmake generate visual studio`)

Et si votre projet se trouve dans un sous‑dossier, ou si vous devez passer des définitions personnalisées ? CMake le permet avec les arguments `-D` :

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Le solution VS générée aura alors la macro `MyFeature_ENABLED` définie, et la cible d’installation placera les fichiers sous `/opt/myapp`. Cela montre la flexibilité de **how to use CMake** au‑delà du flux de base en trois étapes.

---

## Résultat attendu

Lorsque vous exécutez le script complet du début à la fin, le terminal devrait afficher quelque chose comme :

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

En cas de problème, CMake émettra des messages d’erreur indiquant la ligne fautive dans `CMakeLists.txt` ou les composants SDK manquants — parfait pour un débogage rapide.

---

## Conclusion

Nous avons couvert tout ce qu’il faut pour réaliser un **cmake build x64** : définir le répertoire source, invoquer l’étape **cmake generate visual studio**, compiler le **build vs project** résultant, et vérifier la sortie. Le script est compact, portable et prêt à être intégré dans des pipelines CI ou des flux de travail locaux.

Ensuite, vous pourriez explorer :

- Ajouter l’exécution de tests unitaires avec `ctest`.  
- Passer au générateur Ninja pour des builds incrémentaux plus rapides (`-G Ninja`).  
- Utiliser les presets CMake (`CMakePresets.json`) pour stocker les indicateurs que nous venons de taper.

N’hésitez pas à expérimenter, à casser des choses, puis à reconstruire — c’est la façon la plus rapide d’apprendre à **how to use CMake** efficacement. Bonnes constructions !


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}