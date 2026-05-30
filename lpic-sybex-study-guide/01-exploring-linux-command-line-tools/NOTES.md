# Chapter 1: Exploring Linux Command-Line Tools

## 1.05 Using Streams, Redirections and Pipes

### Redirecting Input and Output

- Linux treat every object as a file, including the output of process.

- `File Descriptor:` INTEGER that classifies open process that a father process opens
  - STDIN (0) : points at the input of a shell
    - Operators: {`<`, `<>`}
  - STDOUT(1) : points at the successful output of a shell (by default points at `/dev/tty`)
    - Operators: {`&>`, `&>>`, `>`, `>>`}
  - STDERR(2) : channel the successful output of a shell (also by default points at `/dev/tty`)
    - Operators: {`&>`, `&>>`, `2>`, `2>>`,}

- `Pipe Operator (|):` redirects STDOUT, STDIN and STDERR into the second comand

### Using sed

sed [OPTIONS] [SCRIPT]… [FILENAME]

- Changes all occurrences of string `a` to string `b`

```bash
$ echo "I love cake and more cake." | sed 's/cake/donuts/'
I love donuts and more cake.
$
$ echo "I love cake and more cake." | sed 's/cake/donuts/g'
I love donuts and more donuts.
$
```

- Delete file Text

```bash
$ cat cake.txt
Christine likes chocolate cake.
Rich likes lemon cake.
Tim only likes yellow cake.
Samantha does not like cake.
$ sed '/Christine/d' cake.txt
Rich likes lemon cake.
Tim only likes yellow cake.
Samantha does not like cake.
```

- Using multiple scripts (-e flag)

```bash
$ sed -e 's/cake/donuts/ ; s/like/love/' cake.txt
Christine loves chocolate donuts.
Rich loves lemon donuts.
Tim only loves yellow donuts.
Samantha does not love donuts.
```
