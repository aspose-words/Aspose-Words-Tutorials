---
category: general
date: 2026-07-16
description: cmake build x64 tutorial shows how to use CMake to generate a Visual
  Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
  directory steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: en
lastmod: 2026-07-16
og_description: 'cmake build x64 explained: learn how to set source directory, generate
  a Visual Studio 2022 solution, and compile a VS project on a 64‑bit host.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Step‑by‑Step Guide to Generate & Build VS 2022 Solutions
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
title: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
url: /python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects

Ever wondered **how to use CMake** to produce a 64‑bit Visual Studio solution without pulling your hair out? You're not alone. In this tutorial we’ll walk through a **cmake build x64** workflow that sets the source directory, runs the generator for Visual Studio 2022, and finally builds the VS project—all with a few clean Bash commands.

By the end of the guide you’ll have a reproducible script that you can drop into any repository, plus a solid grasp of the underlying concepts so you can tweak it for your own needs.

---

## What You’ll Learn

- **Set source directory** correctly so CMake knows where your `CMakeLists.txt` lives.  
- **cmake generate visual studio** – invoke the Visual Studio 2022 generator with the right host and architecture flags.  
- Perform a **cmake build x64** of the generated solution, optionally selecting the Release configuration.  
- Understand common pitfalls when you try to **build vs project** on a 64‑bit machine.  

No prior CMake wizardry required; just a terminal and a recent Visual Studio installation.

---

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | Supports the `-Thost=` and `-Ax64` flags used for 64‑bit builds. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | The generator `Visual Studio 17 2022` points to this version. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | The script below uses Bash syntax for clarity. |
| Source tree containing a valid `CMakeLists.txt` | CMake cannot generate a solution without it. |

If any of these are missing, install them first—CMake from <https://cmake.org/download/> and VS 2022 from the Microsoft installer.

---

## Step 1 – Set the Source and Build Directories (`set source directory`)

Before you call CMake you need to tell it **where** to look for the project files. Hard‑coding paths makes the script brittle, so we’ll use environment variables that you can adjust per‑project.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Why this matters:**  
> CMake treats the *source directory* (`SRC_DIR`) as the root of the project. The *build directory* (`BUILD_DIR`) is where all intermediate files, caches, and the final `.sln` live. Keeping them separate avoids polluting your source tree and makes clean‑up trivial (`rm -rf "$BUILD_DIR"`).

You can replace `YOUR_DIRECTORY` with any absolute or relative path; just make sure the folder contains a `CMakeLists.txt`.

---

## Step 2 – Generate a Visual Studio 2022 Solution (`cmake generate visual studio`)

Now we ask CMake to spit out a VS 2022 solution that targets **x64**. The key flags are:

- `-G "Visual Studio 17 2022"` – selects the VS 2022 generator.  
- `-Thost=x64` – tells CMake the *host* (the IDE) runs as a 64‑bit process.  
- `-Ax64` – forces the generated project to build for the x64 architecture.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **What happens under the hood?**  
> CMake reads `CMakeLists.txt` from `$SRC_DIR`, resolves all `add_executable()` and `add_library()` calls, then creates a `.sln` file and a set of `.vcxproj` files inside `$BUILD_DIR`. Those project files are now ready to be opened in Visual Studio or built from the command line.

If you run the command and see a long list of configuration messages ending with `-- Configuring done` and `-- Generating done`, you’ve successfully performed a **cmake generate visual studio** step.

---

## Step 3 – Build the Generated Solution (`cmake build x64`)

With the solution in place, the next logical step is to compile it. CMake can drive the build for you, delegating to MSBuild behind the scenes.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Why use `--config Release`?**  
> Visual Studio projects support multiple configurations (Debug, Release, RelWithDebInfo, etc.). Specifying `Release` ensures the binaries are optimized for production and that the resulting `.exe` or `.dll` lives under `Release/` inside the build tree.

If you prefer a Debug build, replace `Release` with `Debug`. The command works the same way, proving that **how to use CMake** for different configurations is just a matter of swapping this flag.

---

## Step 4 – Verify the Build (`build vs project` sanity check)

A successful compilation should leave you with an executable or library. Let’s confirm it exists:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Common pitfalls:**  
> - Forgetting to run the generator step after changing `CMakeLists.txt` will cause this check to fail.  
> - Mixing 32‑bit and 64‑bit toolchains can lead to linker errors; always keep `-Ax64` consistent.  
> - If you see “MSB3073” errors, it usually means a post‑build step (like copying resources) failed—inspect the output for clues.

---

## Step 5 – Clean Up and Re‑run (Iterating on a `cmake build x64`)

During development you’ll often need to rebuild from scratch. The cleanest way is to delete the build folder and start over:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tip:**  
> Adding `-DCMAKE_BUILD_TYPE=Release` to the generator command is optional for multi‑config generators like Visual Studio, but it can be handy when you switch to a single‑config generator such as Ninja.

---

## Step 6 – Extending the Script (Advanced `cmake generate visual studio` scenarios)

What if your project lives in a sub‑directory, or you need to pass custom definitions? CMake lets you do that with `-D` arguments:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Now the generated VS solution will have the `MyFeature_ENABLED` macro defined, and the install target will place files under `/opt/myapp`. This demonstrates the flexibility of **how to use CMake** beyond the basic three‑step flow.

---

## Expected Output

When you run the full script from start to finish, the terminal should display something like:

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

If anything goes wrong, CMake will emit error messages that point to the offending line in `CMakeLists.txt` or to missing SDK components—perfect for quick debugging.

---

## Conclusion

We’ve covered everything you need to perform a **cmake build x64**: setting the source directory, invoking the **cmake generate visual studio** step, compiling the resulting **build vs project**, and verifying the output. The script is compact, portable, and ready for integration into CI pipelines or local development workflows.

Next, you might explore:

- Adding unit‑test execution with `ctest`.  
- Switching to the Ninja generator for faster incremental builds (`-G Ninja`).  
- Using CMake presets (`CMakePresets.json`) to store the flags we just typed.

Feel free to experiment, break things, and then rebuild—after all, that’s the fastest way to learn how to use CMake effectively. Happy building!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}