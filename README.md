# <h1 align="center">Binder Tool</h1>

<p align="center">
  <strong>A Windows GUI application for bundling multiple executables into a single deployable package</strong>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#building-from-source">Build</a> •
  <a href="#usage">Usage</a> •
  <a href="#how-it-works">How It Works</a> •
  <a href="#requirements">Requirements</a> •
  <a href="#license">License</a>
</p>

---

## Overview

**Binder Tool** is a Windows Forms application designed to bundle two executable files into a single output executable. Inspired by the concept of nesting layers, this tool embeds multiple programs inside one package and executes them sequentially when launched.

This tool is particularly useful for:

* Software distribution requiring multiple components
* Creating unified installers from separate executables
* Bundling auxiliary utilities with main applications
* Simplifying deployment of multi-executable solutions


## Features

| Feature                       | Description                                         |
| ----------------------------- | --------------------------------------------------- |
| **Dual Executable Bundling**  | Combine two `.exe` files into a single output file  |
| **Sequential Execution**      | Automatically run bundled executables in order      |
| **Custom Icon Support**       | Apply a custom `.ico` to the final executable       |
| **Visual Studio Integration** | Uses VS build tools for stable compilation          |
| **Simple GUI Interface**      | Easy-to-use Windows Forms UI                        |
| **Automatic VS Detection**    | Includes `vswhere.exe` for locating Visual Studio   |
| **Clean Execution**           | Temporary extracted files are removed after running |

---

## Requirements

### System Requirements

* **OS:** Windows 10/11
* **Runtime:** .NET Framework 4.0+
* **IDE:** Visual Studio 2022

  * .NET desktop development workload required

### Dependencies

The tool automatically extracts and uses:

* `vswhere.exe` – Visual Studio installation locator


## Building from Source

### Prerequisites

* Install Visual Studio 2022 with:

  * .NET desktop development workload
  * C# support

* Download the project as a ZIP file

### Build Steps

1. Open `src/*.sln` in Visual Studio
2. Choose build configuration: **Debug** or **Release**
3. Build using `Ctrl + Shift + B`
4. Output will be in `bin/Debug/` or `bin/Release/`

---

## Usage

1. **Start the Application**
   Run `*.exe` located in the build output.

2. **Select Custom Icon (Optional)**
   Choose a `.ico` file to assign as the output executable's icon.

3. **Select First Executable**
   Choose the program that should run **first**.

4. **Select Second Executable**
   Choose the program that should run **second**.

5. **Generate the Bundle**
   The tool will:

   * Copy selected executables to the build directory
   * Compile the embedded resources using Visual Studio
   * Display the final bundled file named appropriately

### Example Workflow

```
Input:
├── FirstApp.exe
├── SecondApp.exe
└── CustomIcon.ico

Output:
└── FinalBundle.exe

Execution flow:
1. Extract and run FirstApp.exe
2. Extract and run SecondApp.exe
3. Remove temporary extracted files
```

---

## Technical Details

### 1. Visual Studio Detection

```csharp
vswhere.exe -prerelease -latest -property installationPath
```

### 2. File Embedding

* Selected executables are placed inside a `Resources/` folder
* They are compiled as embedded resources in the output executable

### 3. Runtime Extraction

```csharp
string path = Path.GetTempPath() + "Patch1.exe";
```

### 4. Sequential Execution

* First executable executes with a timeout
* Second executable runs afterwards
* Both are deleted when execution finishes


## Disclaimer

This tool is intended for **educational and legitimate bundling purposes only**.
The authors are not responsible for any misuse.

---

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to your fork
5. Open a Pull Request

## License

Released under the **MIT License**.


<p align="center">
  Made with ❤️ by the community
</p>

<p align="center">
  ⭐ Feel free to star the project if you find it helpful!
</p>
