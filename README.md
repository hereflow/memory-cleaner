# Memory Scanner and Cleaner

This C# code provides a memory scanner and cleaner utility that allows you to search for specific strings in the memory of running processes and replace them with desired values. It utilizes various Windows API functions to interact with process memory.

## Features

- Scans the memory of running processes to find specific strings.
- Supports both ASCII and Unicode string searching.
- Can search for strings in both standalone processes and Windows services.
- Allows customization of search parameters such as the search term, pre/postfix length, delay, and output mode.

## How It Works

1. The code defines various interop declarations to access the required Windows API functions and structures for process memory handling.
2. The `GetProcessByName` function retrieves a running process by its name or, if not found, checks for a corresponding Windows service.
3. The `memScanString` function performs the actual memory scanning. It opens the target process, retrieves system information, and iterates through the process's memory regions.
4. For each readable and committed memory region, the function reads the memory content, converts it to ASCII and Unicode strings, and searches for the specified search term.
5. If a match is found, the memory address and surrounding content are stored in the `targetStrings` dictionary.
6. The `ReplaceStringInProcessMemory` function replaces the matched strings in the process memory with a specified replacement value.
7. The `Main` method iterates over a dictionary of process names and associated search strings.
   - For each process, it calls the memory scanning and replacement functions.
   - If the process is not found, it attempts to locate the corresponding Windows service and associated process ID, then performs the same operations.

## Usage

To use this code, follow these steps:

1. Compile the code using a C# compiler or an IDE that supports C#.
2. Run the compiled executable, which will scan and clean the memory of the specified processes or services.
3. Customize the process names and search strings in the `processToSearchStrings` dictionary to suit your needs.
4. Adjust the search parameters, such as the `prepostfix`, `delay`, and `mode` properties in the `CliArgs` class, to configure the scanning behavior.
5. Modify the replacement logic in the `ReplaceStringInProcessMemory` function if you want to change how the matching strings are replaced in memory.

**Note:** This code is designed for educational and experimental purposes. Please ensure you have the necessary permissions and legal rights before attempting to modify process memory.
