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
