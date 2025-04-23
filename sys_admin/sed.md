### Ah yes, the mighty `sed`! In **Red Hat Linux (or any Linux really)**, `sed` is a **stream editor**—a powerful tool for processing and transforming text in files or input streams.

Here’s a handy cheat sheet of common `sed` uses:

---

## 🔧 **Basic Syntax**

```bash
sed [options] 'command' file
```

Or:

```bash
echo "some text" | sed 'command'
```

---

## 📝 **Common `sed` Commands**

| What you want to do                | Command Example                                      |
|------------------------------------|------------------------------------------------------|
| **Substitute**                     | `sed 's/old/new/' file.txt`                          |
| Replace globally on line           | `sed 's/old/new/g' file.txt`                         |
| Case-insensitive replace           | `sed 's/old/new/Ig' file.txt`                        |
| Replace only line 3                | `sed '3s/old/new/' file.txt`                         |
| Replace between line 3 and 5       | `sed '3,5s/old/new/' file.txt`                       |
| Replace in-place (edit file)       | `sed -i 's/old/new/g' file.txt`                      |
| Delete a specific line (e.g., 2nd) | `sed '2d' file.txt`                                  |
| Delete blank lines                 | `sed '/^$/d' file.txt`                               |
| Insert line before match           | `sed '/pattern/i\new line here' file.txt`            |
| Append line after match            | `sed '/pattern/a\another new line' file.txt`         |
| Print only matching lines          | `sed -n '/pattern/p' file.txt`                       |

---

## ✨ **Examples**

### 1. Replace "foo" with "bar" in a file:
```bash
sed 's/foo/bar/' file.txt
```

### 2. Edit a file in place (no backup):
```bash
sed -i 's/foo/bar/g' file.txt
```

### 3. Edit in place **with backup**:
```bash
sed -i.bak 's/foo/bar/g' file.txt
```
Creates a backup called `file.txt.bak`.

---

## 🧠 Bonus Tips

- `-n` suppresses default output—use with `p` to print only matches.
- Use double quotes if using shell variables inside the `sed` command:
  ```bash
  name="Alice"
  sed "s/USER/$name/" file.txt
  ```

---
