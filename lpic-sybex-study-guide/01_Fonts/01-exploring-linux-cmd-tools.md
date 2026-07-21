# Chapter 1: Exploring Linux Command-Line Tools

## 1.01 Introduction to the Command Line

## 1.05 Using Streams, Redirections and Pipes

### Redirecting Input and Output

- Linux treats every object as a file, including the input and output of a process.
- `File Descriptor`: An INTEGER that classifies **open files** belonging to an active process.
  - **STDIN (0):** Standard Input. Points to the input of a shell (typically the keyboard).
  - **STDOUT (1):** Standard Output. Points to the successful output of a command (by default, points to `/dev/tty`, the monitor).
  - **STDERR (2):** Standard Error. Channel where the shell sends messages identified as errors (also defaults to `/dev/tty`).

#### Commonly Used Redirection Operators

|  Channel   |  Operators   | Description                                            |
| :--------: | :----------: | :----------------------------------------------------- |
| **STDIN**  |  `<` , `<>`  | Redirects input from a file into a command.            |
| **STDOUT** |  `>` , `>>`  | `>` overwrites the file. `>>` appends to the file.     |
| **STDERR** | `2>` , `2>>` | Redirects only errors. `2>` overwrites, `2>>` appends. |
|  **BOTH**  | `&>` , `&>>` | Redirects both STDOUT and STDERR to the same file.     |

- `Pipe Operator (|):` Connects the **STDOUT** of the first command directly into the **STDIN** of the second command.

---

### Using sed (Stream Editor)

**Syntax:** `sed [OPTIONS] [SCRIPT]… [FILENAME]`

- **Substitute strings:** Changes occurrences of string `a` to string `b`.
  - `s/old/new/` replaces only the _first_ occurrence in a line.
  - `s/old/new/g` (global flag) replaces _all_ occurrences in a line.

```sh
$ echo "I love cake and more cake." | sed 's/cake/donuts/'
I love donuts and more cake.

$ echo "I love cake and more cake." | sed 's/cake/donuts/g'
I love donuts and more donuts.
Delete lines from a file: Uses the /PATTERN/d script.
$ cat cake.txt
Christine likes chocolate cake.
Rich likes lemon cake.
Tim only likes yellow cake.
Samantha does not like cake.

$ sed '/Christine/d' cake.txt
Rich likes lemon cake.
Tim only likes yellow cake.
Samantha does not like cake.
Using multiple scripts: Use the -e flag to chain instructions separated by ;.
$ sed -e 's/cake/donuts/ ; s/like/love/' cake.txt
Christine loves chocolate donuts.
Rich loves lemon donuts.
Tim only loves yellow donuts.
Samantha does not love donuts.
```
