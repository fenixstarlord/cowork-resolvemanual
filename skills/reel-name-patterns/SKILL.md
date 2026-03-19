---
name: reel-name-patterns
description: "Use this skill whenever the user asks about reel name extraction patterns, the Pattern field in DaVinci Resolve's Conform Options, how to extract reel names from file paths or filenames, the 'Assist using reel names' setting, pattern operators like %R %D ? *, or needs help constructing a reel name extraction pattern for a specific file naming convention."
---

# Reel Name Extraction Patterns

When answering questions about reel name patterns, cite: "See the Conform Options section in the DaVinci Resolve manual (Ch on Media Management / Conforming)."

## Where to Set the Pattern

Project Settings > General Options > Conform Options > turn on "Assist using reel names from the" > choose "Source clip file pathname" > enter your pattern in the **Pattern** field. Click **Test** to try it against a sample path before applying.

## How Patterns Work

Patterns are parsed **right to left**, starting from the filename and moving through each enclosing directory. The pattern describes the structure of the file path so DaVinci Resolve knows where the reel name lives.

## Pattern Operators

| Operator | Meaning |
|----------|---------|
| `?` | Matches exactly one character. Use multiple for fixed-length matches: `??` matches two characters, `????` matches four. |
| `*` | Matches any sequence of zero or more characters (wildcard). |
| `%R` | Marks where the reel name is. This is what gets extracted. Reel names can contain any character except `/`. |
| `%_R` | Same as `%R`, but strips underscores from the extracted reel name. Used for R3D filenames from Final Cut Pro 7 EDLs. |
| `%D` | Matches any single directory name or filename. When it's the last operator in a pattern, do not add a trailing `/`. |
| `/` | Directory separator. Used between operators to indicate path boundaries. |

## Examples from the Manual

### Example 1: Reel name is the parent folder

- **Pattern:** `*/%R/%D`
- **File path:** `/vol0/MyMovie/Scans/004B/Frame[1000-2000].dpx`
- **Extracted reel name:** `004B`

Reading right to left: `%D` matches the filename, `%R` captures the parent folder name as the reel, `*` matches everything before it.

### Example 2: Reel name in a prefixed folder

- **Pattern:** `*/Reel%R/%D` (or equivalently `*/????%R/%D`)
- **File path:** `/vol0/MyMovie/Scans/Reel1234/Frame[1000-2000].dpx`
- **Extracted reel name:** `1234`

The literal text `Reel` (or `????` for any 4 characters) is skipped, and `%R` captures only the portion after the prefix.

### Example 3: Reel name is the grandparent folder

- **Pattern:** `*/%R/%D/%D`
- **File path:** `/vol0/MyMovie/Scans/004B/134500-135000/Frame[1000-2000].dpx`
- **Extracted reel name:** `004B`

Two `%D` operators consume the filename and its immediate parent, so `%R` lands on the directory two levels up.

### Example 4: Reel name embedded in the filename

- **Pattern:** `*/Reel%R\_*`
- **File path:** `/vol0/MyMovie/Scans/Reel004B\_[1000-2000].dpx`
- **Extracted reel name:** `004B`

Reading right to left: `\_*` matches everything after the underscore (frame number + extension), `%R` captures the reel portion, and `Reel` matches the literal prefix.

## How to Build a Pattern for Any File

When a user gives you a filename or path and tells you what part should be the reel name, follow this process:

1. **Identify the reel name portion** in the path — what the user wants extracted.
2. **Determine where it lives** — in the filename itself, or in a folder name (and how many levels up).
3. **Work right to left** from the filename:
   - Use `%D` to consume entire directory names or filenames you want to skip.
   - Use `*` to match variable-length portions you don't care about (including the rest of the path to the left).
   - Use `?` to match a fixed number of characters you want to skip within a name.
   - Use literal text to match fixed prefixes or suffixes adjacent to the reel name.
   - Place `%R` exactly where the reel name is.
4. **Use `/` between path elements** (directories and filename).

### Quick-reference decision table

| Reel name location | Pattern template |
|---------------------|-----------------|
| Entire parent folder name | `*/%R/%D` |
| Parent folder with a prefix | `*/prefix%R/%D` |
| Grandparent folder | `*/%R/%D/%D` |
| Start of filename, before a delimiter | `*/%R<delimiter>*` |
| Middle of filename, between delimiters | `*/<prefix>%R<suffix>` |
| End of filename, after a delimiter | `*/<prefix>%R.<ext>` or `*/<prefix>%R` |

Replace `<delimiter>`, `<prefix>`, `<suffix>`, `<ext>` with the actual characters from the user's naming convention. Use `?` instead of literal text when the prefix is variable but fixed-length.

### Worked example: Camera-style filename

- **Filename:** `A001C003-S000.braw`
- **User wants reel name:** `A001C003`
- **Pattern:** `*/%R-*`
- **Why:** Reading right to left, `-*` matches `-S000.braw` (the dash and everything after), `%R` captures `A001C003`, and `*/` matches the rest of the path.

## Testing Your Pattern

1. In Project Settings > General Options > Conform Options, click the **Test** button next to the Pattern field.
2. Enter your pattern in the Pattern field of the dialog.
3. Paste a sample file path into the Sample Path field.
4. Click **Test** — the extracted reel name appears below.
5. If correct, click **Apply** to use the pattern. If not, adjust and test again.
