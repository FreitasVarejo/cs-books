# LPIC-1 Sybex Guide Chapter 01: Exploring Linux Command-Line Tools

May 27 2026

### 1. You are writing a deployment script and need to redirect the standard output of `setup.sh` to a file named `success.log`. However, you want to completely discard any standard error messages so they do not clutter the console or the log file. Which command accomplishes this?

A) `./setup.sh &> success.log /dev/null`
B) `./setup.sh 1> success.log 2>&1 /dev/null`
C) `./setup.sh > success.log | 2> /dev/null`
D) `./setup.sh > success.log 2> /dev/null`

D)
I remerber that `2>` redirect the STDERR, but im not shure if `>` redirect both, or why dont use `|` instead

### 2. You are inspecting a legacy system log where columns are separated by an unpredictable number of spaces. You need to extract exactly the 3rd column from `data.txt`. Which pipeline correctly normalizes the spacing and extracts the column?

A) `cat data.txt | split -d" " -f3`
B) `cat data.txt | grep -s ' ' | cut -f3`
C) `cat data.txt | tr -s ' ' | cut -d' ' -f3`
D) `cat data.txt | cut -d" " -f3`

B)
I dont remember what tr was suposed to do and also how cut works

### 3. A file named `domains.txt` contains thousands of domain names, one per line. You only want to filter and display the domains that end with either `.org` or `.com`. Using extended regular expressions, which command correctly performs this task?

A) `grep ".org$|.com$" domains.txt`
B) `egrep ".org$|.com$" domains.txt`
C) `sed -e '.org$|.com$' domains.txt`
D) `egrep ".*org$ & .*com$" domains.txt`

A) Im confident it is egrep, because the regex is right and normal grep wont support extended regex

### 4. You need to parse a hardware inventory file named `inventory.txt`. You want to print _only_ the lines that begin with `SERVER:` and, on those specific lines, substitute the very first occurrence of a hyphen (`-`) with a colon (`:`). Which `sed` command sequence achieves this?

A) `sed -n '/^SERVER:/p' inventory.txt | sed 's/-/:/'`
B) `sed -e '/^SERVER:/ s/-/:/g' inventory.txt`
C) `sed -n '/^SERVER:/p' inventory.txt | sed 's/-/:/g'`
D) `grep "SERVER:" inventory.txt | tr '-' ':'`

I dont remember anything about sed, i wont awnser

### 5. You have written several custom administrative scripts and placed them in `/opt/custom/scripts`. You want to be able to execute them by name from any location in your current shell session, and ensure this path is inherited by any child subshells. Which command handles this correctly?

A) `env $PATH:/opt/custom/scripts`
B) `PATH=$PATH:/opt/custom/scripts`
C) `export PATH=/opt/custom/scripts:$PATH`
D) `set PATH=/opt/custom/scripts`

B) Because the export command is the only way listed that child subshells will inherit.

### 6. You have generated a text file, `images.txt`, containing a long list of image filenames. You want to pass each filename as an argument to the `convert` utility to resize them to 25%, placing the output in a directory named `small/`. Which command utilizes `xargs` correctly to achieve this?

A) `cat images.txt > xargs convert IMG -resize 25% small/IMG`
B) `xargs < images.txt | convert -resize 25% small/`
C) `cat images.txt | exec convert {} -resize 25% small/{}`
D) `xargs -I IMG convert IMG -resize 25% small/IMG < images.txt`

I dont remember anything about xargs, i wont awnser

### 7. While editing a critical configuration file using the `vi` text editor, you realize you need to duplicate an entire line of configuration and paste it immediately below your cursor's current position. While in normal mode, which keystroke sequence will perform this action?

A) Type `:copy` and then `:paste`
B) Press `d`, move the cursor down, and press `i`
C) Press `yy`, move the cursor down, and press `p`
D) Press `cc`, move the cursor down, and press `v`

C)
Im shure

### 8. Within a bash script, you want to capture the output of the command `date +%Y-%m-%d` and store it inside a shell variable named `TODAY`. Utilizing modern command substitution syntax, which line is correct?

A) `TODAY=${date +%Y-%m-%d}`
B) `TODAY="date +%Y-%m-%d"`
C) `$TODAY=date +%Y-%m-%d`
D) `TODAY=$(date +%Y-%m-%d)`

A)
I think it needs `${}` because it is going to take the STDOUT of a command

### 9. You are auditing a file named `active_users.txt` that contains a list of usernames. Due to a bug in the logging system, many usernames are scattered and duplicated throughout the file. You need to output the exact numeric count of _unique_ usernames. Which chained command sequence correctly accomplishes this?

A) `uniq active_users.txt | sort | wc -c`
B) `cat active_users.txt | wc -l | uniq`
C) `sort active_users.txt | uniq | wc -l`
D) `grep -u active_users.txt | wc -l`

I dont remember what wc and uniq do

### 10. You need to dynamically append a multi-line block of configuration text into `config.txt` directly from within a shell script without using a separate text file. Which mechanism uses a Here Document to correctly feed the standard input?

A) `cat << EOF >> config.txt`
B) `cat <<< EOF >> config.txt`
C) `cat >> EOF > config.txt`
D) `cat < EOF >> config.txt`

I dont know

---

## Answer Key & Explanations

**1. Correct Answer: D** (`./setup.sh > success.log 2> /dev/null`)

- **Explanation:** The `>` symbol (or `1>`) redirects standard output (stdout) to `success.log`. The `2>` symbol specifically targets standard error (stderr) and redirects it to the null device (`/dev/null`), effectively discarding it. Option A is incorrect because `&>` redirects _both_ stdout and stderr to `success.log`, making the `/dev/null` argument invalid. Option B uses improper syntax for this goal. Option C incorrectly places a pipe before standard error redirection.

**2. Correct Answer: C** (`cat data.txt | tr -s ' ' | cut -d' ' -f3`)

- **Explanation:** The `cut` command alone strictly treats every single delimiter character as a new field. If there are consecutive spaces, `cut -d' '` will read empty fields between them. Using the `tr -s ' '` command "squeezes" multiple occurrences of the space character into a single space, aiding in formatting the output so `cut` can accurately target the 3rd field (`-f3`). Options A and B use the wrong utility for splitting text columns, and Option D fails because `cut` cannot natively squeeze repeated delimiters.

**3. Correct Answer: B** (`egrep ".org$|.com$" domains.txt`)

- **Explanation:** The `egrep` command evaluates Extended Regular Expressions (ERE), which allows the use of the `|` (alternation/OR) operator without needing to escape it. The `$` anchor specifically matches the end of the line. Option A uses standard `grep` which requires escaping the pipe (`\|`) to act as an alternation in Basic Regular Expressions (BRE). Options C and D use incorrect tools or invalid regex syntaxes.

**4. Correct Answer: A** (`sed -n '/^SERVER:/p' inventory.txt | sed 's/-/:/'`)

- **Explanation:** This chains two `sed` commands. The first uses `-n` (suppress automatic printing) and `/^SERVER:/p` to print _only_ the lines matching the `SERVER:` pattern anchored to the beginning (`^`). The second `sed` performs a substitution (`s/-/:/`). Because it lacks the global flag (`g`), it accurately replaces only the _first_ occurrence of `-`. Option C is incorrect because the `g` flag replaces _all_ instances. Option D uses `tr` which translates characters unconditionally across the whole matched line. Option B affects the first matched line but prints the entire file.

**5. Correct Answer: C** (`export PATH=/opt/custom/scripts:$PATH`)

- **Explanation:** The `export` command ensures that the environment variable `PATH` is made available to any child processes (subshells) spawned from the current shell session. Defining it without `export` (Option B) only makes it a local shell variable. `env` and `set` are not used in the syntax shown in Options A and D to declare and export paths.

**6. Correct Answer: D** (`xargs -I IMG convert IMG -resize 25% small/IMG < images.txt`)

- **Explanation:** `xargs` builds and executes command lines from standard input. The `-I` flag allows you to define a placeholder string (in this case, `IMG`) which is subsequently replaced by the names read from standard input (`< images.txt`). Option A has broken redirection syntax. Option B sends standard input to `xargs` but then attempts to pipe it directly to `convert`, which expects file arguments. Option C uses `exec` improperly.

**7. Correct Answer: C** (Press `yy`, move the cursor down, and press `p`)

- **Explanation:** In `vi` normal mode, `yy` is the command to "yank" (copy) the current line into the buffer. The `p` command "puts" (pastes) the contents of the buffer below the cursor's current line. Option B (`d` and `i`) deletes content and enters insert mode. Options A and D reference non-existent or graphical-style commands that do not apply to standard `vi`.

**8. Correct Answer: D** (`TODAY=$(date +%Y-%m-%d)`)

- **Explanation:** Modern Bash utilizes the `$()` syntax for command substitution, which executes the inner command and replaces the statement with the command's standard output. Option A uses `${}` which is for parameter/variable expansion, not command substitution. Option B treats the command as a literal string. Option C incorrectly prefixes the variable name with `$` during assignment.

**9. Correct Answer: C** (`sort active_users.txt | uniq | wc -l`)

- **Explanation:** The `uniq` command filters adjacent matching lines; therefore, the input _must_ be sorted first so all duplicates are grouped together. Once piped through `sort` and then `uniq`, the output is a clean list of unique usernames. Finally, `wc -l` counts the number of lines. Option A pipes unsorted text into `uniq`, which will fail to remove duplicates that are not adjacent, and uses `-c` (byte count) instead of `-l` (line count). Option B counts lines before removing duplicates.

**10. Correct Answer: A** (`cat << EOF >> config.txt`)

- **Explanation:** The `<<` operator signifies a Here Document, which tells the shell to read standard input until it encounters the specified delimiter (in this case, `EOF`). The `>>` operator then appends that combined output to `config.txt`. Option B uses `<<<` which is a Here String (used for single strings, not block input). Options C and D use incorrect, invalid redirection syntax.
