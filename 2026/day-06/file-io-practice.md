# Day 06 – File I/O Practice

## 🔹 File Creation

### Command:
touch notes.txt

### Observation:
Created an empty file named notes.txt

---

## 🔹 Writing to File

### Command:
echo "Line 1: Learning Linux" > notes.txt

### Observation:
Created file and added first line (overwrite mode)

---

### Command:
echo "Line 2: Practicing file operations" >> notes.txt

### Observation:
Appended second line to file

---

### Command:
echo "Line 3: Using tee command" | tee -a notes.txt

### Observation:
Line added and displayed on terminal using tee

---

## 🔹 Reading File

### Command:
cat notes.txt

### Observation:
Displayed full file content

---

### Command:
head -n 2 notes.txt

### Observation:
Displayed first 2 lines of file

---

### Command:
tail -n 2 notes.txt

### Observation:
Displayed last 2 lines of file

---

## 🔹 Final File Content

[(paste output of cat notes.txt here)](notes.txt)

---

## 🔹 Key Learnings

- `>` overwrites file
- `>>` appends to file
- `tee -a` writes and displays output
- `cat`, `head`, `tail` help read files efficiently