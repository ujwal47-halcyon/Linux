# Bandit Level 12 — Compression Chain Investigation

## Work recorded

The level uses a hexadecimal dump of a file that must be reconstructed and unpacked through multiple compression formats.

### Commands used

```bash
cd /tmp
mktemp -d
cp data.txt <temporary-directory>
cd <temporary-directory>
xxd -r data.txt > data
file data
mv data data.gz
gzip -d data.gz
file data
```

### What the output showed

- `xxd -r` reconstructed the binary file from the hexadecimal dump.
- The first `file` check identified gzip-compressed data.
- After gzip decompression, the next `file` check identified bzip2-compressed data.
- The attempt to run `bzip -d` failed because the command name was incorrect. The utility is `bzip2`.

### Next step

Continue identifying each layer with `file` and use the matching decompression utility. Keep the working copy in the temporary directory.

Example for a bzip2 layer:

```bash
bzip2 -d data
file data
```

Repeat the inspect-and-decompress process for each layer until the final file type is identified.

## Security and evidence

- No Bandit password or flag is recorded in this note.
- The temporary directory identifier is blurred in the accompanying screenshot.
- Only upload the redacted screenshot to `proofs/`; keep the original private.

## Status

This note records the investigation shown in the screenshot. It does **not** claim that Bandit Level 12 is completed.
