# Linux Command Notes — Bandit Levels 0–9

A short reference from the first ten OverTheWire Bandit levels. No passwords or challenge credentials are included.

## File and directory inspection

```bash
ls -la
file <filename>
find . -type f
```

- `ls -la` lists ordinary and hidden files with details.
- `file` identifies the type of a file.
- `find` searches recursively through directories.

## Handling unusual filenames

Use `--` to mark the end of command options when a filename begins with a hyphen:

```bash
cat -- -file07
```

## Searching and filtering text

```bash
grep "pattern" filename
strings data.txt
strings data.txt | grep "="
```

- `grep` selects lines matching a pattern.
- `strings` extracts readable text from binary or mixed-content files.

## Sorting and finding unique lines

```bash
sort data.txt | uniq -u
```

Sort the input first because `uniq` compares adjacent lines. The `-u` option prints lines that occur exactly once.

## Searching by ownership and size

```bash
find / -user <username> -group <groupname> -size 33c 2>/dev/null
```

- `-user` and `-group` filter by ownership.
- `-size 33c` matches files exactly 33 bytes in size.
- `2>/dev/null` hides permission-denied and other error messages.

## Security note

Do not store Bandit passwords, SSH credentials, tokens, or unredacted challenge output in this repository. Keep proof screenshots redacted before committing.
