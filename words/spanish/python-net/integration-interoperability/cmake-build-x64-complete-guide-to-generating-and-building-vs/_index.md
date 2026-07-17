---
category: general
date: 2026-07-16
description: El tutorial “cmake build x64” muestra cómo usar CMake para generar una
  solución de Visual Studio 2022 y compilar un proyecto VS en un host de 64 bits.
  Incluye los pasos para establecer el directorio de origen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: es
lastmod: 2026-07-16
og_description: 'Construcción cmake x64 explicada: aprende cómo establecer el directorio
  de origen, generar una solución de Visual Studio 2022 y compilar un proyecto VS
  en un host de 64 bits.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: Compilación cmake x64 – Guía paso a paso para generar y compilar soluciones
  de VS 2022
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
title: Compilación cmake x64 – Guía completa para generar y compilar proyectos VS 2022
url: /es/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Guía completa para generar y compilar proyectos VS 2022

¿Alguna vez te has preguntado **cómo usar CMake** para producir una solución de Visual Studio de 64 bits sin volverte loco? No estás solo. En este tutorial recorreremos un flujo de trabajo **cmake build x64** que establece el directorio de origen, ejecuta el generador para Visual Studio 2022 y finalmente compila el proyecto VS, todo con unos pocos comandos Bash limpios.

Al final de la guía tendrás un script reproducible que podrás colocar en cualquier repositorio, además de una comprensión sólida de los conceptos subyacentes para que puedas ajustarlo a tus propias necesidades.

---

## Lo que aprenderás

- **Set source directory** correctamente para que CMake sepa dónde está tu `CMakeLists.txt`.  
- **cmake generate visual studio** – invoca el generador de Visual Studio 2022 con los indicadores correctos de host y arquitectura.  
- Realiza un **cmake build x64** de la solución generada, opcionalmente seleccionando la configuración Release.  
- Comprende los problemas comunes al intentar **build vs project** en una máquina de 64 bits.  

No se requiere experiencia previa con CMake; solo una terminal y una instalación reciente de Visual Studio.

## Requisitos

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | Soporta los indicadores `-Thost=` y `-Ax64` usados para compilaciones de 64 bits. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | El generador `Visual Studio 17 2022` apunta a esta versión. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | El script a continuación usa sintaxis Bash para mayor claridad. |
| Source tree containing a valid `CMakeLists.txt` | CMake no puede generar una solución sin él. |

Si falta alguno de estos, instálalo primero—CMake desde <https://cmake.org/download/> y VS 2022 desde el instalador de Microsoft.

## Paso 1 – Establecer los directorios de origen y compilación (`set source directory`)

Antes de invocar CMake necesitas indicarle **dónde** buscar los archivos del proyecto. Codificar rutas de forma rígida hace que el script sea frágil, así que usaremos variables de entorno que podrás ajustar por proyecto.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Por qué es importante:**  
> CMake trata el *directorio de origen* (`SRC_DIR`) como la raíz del proyecto. El *directorio de compilación* (`BUILD_DIR`) es donde viven todos los archivos intermedios, cachés y el `.sln` final. Mantenerlos separados evita contaminar tu árbol de código fuente y hace que la limpieza sea trivial (`rm -rf "$BUILD_DIR"`).

Puedes reemplazar `YOUR_DIRECTORY` por cualquier ruta absoluta o relativa; solo asegúrate de que la carpeta contenga un `CMakeLists.txt`.

## Paso 2 – Generar una solución Visual Studio 2022 (`cmake generate visual studio`)

Ahora le pedimos a CMake que genere una solución VS 2022 que apunte a **x64**. Los indicadores clave son:

- `-G "Visual Studio 17 2022"` – selecciona el generador VS 2022.  
- `-Thost=x64` – indica a CMake que el *host* (el IDE) se ejecuta como proceso de 64 bits.  
- `-Ax64` – fuerza que el proyecto generado se compile para la arquitectura x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **¿Qué ocurre tras bambalinas?**  
> CMake lee `CMakeLists.txt` desde `$SRC_DIR`, resuelve todas las llamadas a `add_executable()` y `add_library()`, luego crea un archivo `.sln` y un conjunto de archivos `.vcxproj` dentro de `$BUILD_DIR`. Esos archivos de proyecto están ahora listos para abrirse en Visual Studio o compilarse desde la línea de comandos.

Si ejecutas el comando y ves una larga lista de mensajes de configuración que terminan con `-- Configuring done` y `-- Generating done`, has realizado con éxito el paso **cmake generate visual studio**.

## Paso 3 – Compilar la solución generada (`cmake build x64`)

Con la solución en su lugar, el siguiente paso lógico es compilarla. CMake puede gestionar la compilación por ti, delegando en MSBuild tras bambalinas.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **¿Por qué usar `--config Release`?**  
> Los proyectos de Visual Studio admiten múltiples configuraciones (Debug, Release, RelWithDebInfo, etc.). Especificar `Release` garantiza que los binarios estén optimizados para producción y que el `.exe` o `.dll` resultante se encuentre bajo `Release/` dentro del árbol de compilación.

Si prefieres una compilación Debug, reemplaza `Release` por `Debug`. El comando funciona de la misma manera, demostrando que **cómo usar CMake** para diferentes configuraciones es solo cuestión de cambiar este indicador.

## Paso 4 – Verificar la compilación (`build vs project` sanity check)

Una compilación exitosa debería dejarte con un ejecutable o una biblioteca. Confirmemos que exista:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Problemas comunes:**  
> - Olvidar ejecutar el paso del generador después de cambiar `CMakeLists.txt` hará que esta verificación falle.  
> - Mezclar toolchains de 32 bits y 64 bits puede provocar errores de enlazado; siempre mantén `-Ax64` consistente.  
> - Si ves errores “MSB3073”, normalmente significa que falló un paso post‑compilación (como copiar recursos); inspecciona la salida para obtener pistas.

## Paso 5 – Limpiar y volver a ejecutar (Iterando sobre un `cmake build x64`)

Durante el desarrollo a menudo necesitarás recompilar desde cero. La forma más limpia es eliminar la carpeta de compilación y comenzar de nuevo:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Consejo:**  
> Añadir `-DCMAKE_BUILD_TYPE=Release` al comando del generador es opcional para generadores multi‑configuración como Visual Studio, pero puede ser útil cuando cambias a un generador de configuración única como Ninja.

## Paso 6 – Extender el script (Escenarios avanzados de `cmake generate visual studio`)

¿Qué pasa si tu proyecto está en un subdirectorio, o necesitas pasar definiciones personalizadas? CMake te permite hacerlo con argumentos `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Ahora la solución VS generada tendrá la macro `MyFeature_ENABLED` definida, y el objetivo de instalación colocará los archivos bajo `/opt/myapp`. Esto demuestra la flexibilidad de **cómo usar CMake** más allá del flujo básico de tres pasos.

## Salida esperada

Cuando ejecutes el script completo de principio a fin, la terminal debería mostrar algo como:

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

Si algo falla, CMake emitirá mensajes de error que apuntan a la línea problemática en `CMakeLists.txt` o a componentes SDK faltantes—perfecto para una depuración rápida.

## Conclusión

Hemos cubierto todo lo que necesitas para realizar un **cmake build x64**: establecer el directorio de origen, invocar el paso **cmake generate visual studio**, compilar el **build vs project** resultante y verificar la salida. El script es compacto, portátil y listo para integrarse en pipelines de CI o flujos de trabajo de desarrollo local.

A continuación, podrías explorar:

- Añadir la ejecución de pruebas unitarias con `ctest`.  
- Cambiar al generador Ninja para compilaciones incrementales más rápidas (`-G Ninja`).  
- Usar presets de CMake (`CMakePresets.json`) para almacenar los indicadores que acabamos de escribir.

Siéntete libre de experimentar, romper cosas y luego recompilar—después de todo, esa es la forma más rápida de aprender a usar CMake eficazmente. ¡Feliz compilación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Construir tabla](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Construir tabla con estilo](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Construir tabla con bordes](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}