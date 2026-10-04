# HexEncoder-Java

Small Java CLI utility that reads a single line from standard input and:

- encodes text bytes to uppercase, space-separated hex pairs (default mode), or
- converts hex pairs to a continuous binary bit string (decode mode).

## Current features

- **Encode mode (default):** converts input text to hex (`%02X ` formatting).
- **Decode mode (`arg != 0`):** converts space-separated hex pairs to binary bits.
- Reads from **stdin** and writes to **stdout**.

## Technology stack

- Java (single-file source under `src/com/skwangles/Main.java`)
- No build tool wrapper (no Maven/Gradle files currently in this repository)

## Repository structure

```text
.
├── README.md
└── src/com/skwangles/Main.java
```

## Prerequisites

- JDK 14+ (the source uses switch expressions)

## Build and run

From the repository root:

```bash
javac src/com/skwangles/Main.java
```

### Encode text to hex (default)

```bash
echo "ABC" | java -cp src com.skwangles.Main
# Output: 41 42 43
```

### Convert hex pairs to binary bits

```bash
echo "41 42 43" | java -cp src com.skwangles.Main 1
# Output includes:
# -41 42 43-
# 010000010100001001000011
```

## Testing

There is no automated test suite in the current repository. Use the build/run commands above as a manual smoke test after changes.

## Configuration and behavior notes

- Input is read with `Scanner.nextLine()`, so the program expects one line on stdin.
- Decode mode is enabled when at least one argument is provided and the first argument is not `"0"`.
- Invalid decode characters map to `"...."` in binary output.
- Exceptions in `main` are currently swallowed (no error output).

## Project status / limitations

- Minimal CLI utility with no packaging, release workflow, or automated tests in-repo.
- Decoder outputs raw binary bit strings, not decoded text bytes.

## Attribution

If you like what I do, consider buying me a coffee:  
https://www.buymeacoffee.com/skwangles
