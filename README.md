![Famine PE Virus Banner](./.assets/banner.png)

A polymorphic parasitic virus targeting 64-bit Windows PE files, written from scratch in FASM assembly language. This project is intended for educational and research purposes only.

> **⚠️ Disclaimer**
>
> This software is provided for educational and research purposes only. The author is not responsible for any misuse or damage caused by this program. You are solely responsible for your actions. Do not use this software on systems you do not own or have explicit permission to test.

## Features

*   **Polymorphic Engine:** Mutates its own code with each infection to evade signature-based detection.
*   **Parasitic Infection:** Injects its code into host PE files without corrupting the original program's functionality.
*   **Win64 Target:** Specifically designed to infect 64-bit Windows executables.
*   **Hand-Crafted Assembly:** Written entirely in FASM for maximum control and a minimal footprint.
*   **No Dependencies:** The final payload runs without requiring any external libraries.

## How It Works

Famine operates by locating a suitable host executable and injecting its viral code. The infection process follows these general steps:

1.  **Host Selection:** The virus searches for a valid 64-bit PE file to infect.
2.  **Code Injection:** It creates a new section in the host file and writes its polymorphic payload into it.
3.  **Entry Point Obfuscation:** The host's original entry point is saved, and the PE header is modified to point to the start of the virus code.
4.  **Execution Flow:** When the infected application is run, the virus executes first. After completing its own tasks (such as further propagation), it restores the original program state and jumps to the original entry point, allowing the host application to run as normal.

## Prerequisites

To build the virus from the source code, you will need:

*   [**FASM (Flat Assembler)**](https://flatassembler.net/) installed and available in your system's PATH.
*   A `make` utility, typically available on Linux/macOS or through MinGW/WSL on Windows.

## Building

Clone the repository and use the provided `Makefile` to assemble the source code.

```sh
git clone https://github.com/jdecorte-be/famine-pe.git
cd famine-pe
make
```

This will generate the executable `famine.exe` in the root directory.

## Usage

To infect a file, run the compiled virus and provide the path to the target executable as a command-line argument.

**Syntax:**

```sh
./famine.exe <path_to_target_executable>
```

**Example:**

```sh
# This will attempt to infect 'victim.exe'
./famine.exe ./victim.exe
```

## License

This project is distributed under the terms of the license specified in the `LICENSE` file.
