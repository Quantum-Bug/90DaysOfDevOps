# Day 06 – Linux Fundamentals: Read and Write Text Files

## Objective
Practice basic file input/output operations using core Linux commands.  
This exercise focuses on creating a file, writing data, appending content, and reading files in different ways.

---

## File Used
- **File name:** `notes.txt`

---

## Step 1: Create an Empty File

```bash
touch notes.txt
```
Explanation:

- Creates an empty file if it does not exist
- Does nothing if the file already exists

## Step 2: Write First Line (Overwrite)
```bash
echo "Day 06: Linux file read and write practice" > notes.txt
```

Explanation:

- Writes text into notes.txt
- The > operator overwrites existing content

## Step 3: Append Second Line
```bash
echo "Practicing redirection using > and >>" >> notes.txt
```

Explanation:

- Appends a new line to the file
- Existing content remains unchanged

## Step 4: Write and Display Using tee
```bash 
echo "Using tee to write and display output" | tee -a notes.txt
```

Explanation:

- Displays output on the terminal
- Appends output to the file at the same time
- Commonly used in logging and scripts

## Step 5: Read Entire File
```bash 
cat notes.txt
```

Explanation:

- Displays the complete contents of the file

## Step 6: Read First Two Lines
```bash 
head -n 2 notes.txt
```

Explanation:

- Shows the first two lines of the file
- Useful for inspecting headers or config files

## Step 7: Read Last Two Lines
```bash 
tail -n 2 notes.txt
```

Explanation:

- Displays the last two lines of the file
- Frequently used to inspect logs

## Final File Content (notes.txt)
```bash 
Day 06: Linux file read and write practice
Practicing redirection using > and >>
Using tee to write and display output
```

## Key Learnings

- `touch` creates files

- `>` overwrites file content

- `>>` safely appends content

- `tee` writes and prints output simultaneously

- `cat`, `head`, and `tail` are essential for reading files