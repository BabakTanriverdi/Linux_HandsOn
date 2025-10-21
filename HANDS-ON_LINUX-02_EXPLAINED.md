# 🧠 Hands-on Linux-02 : Managing Files in Linux (Extended – Explained Version)

## 🎯 Purpose
Bu uygulamalı laboratuvar çalışmasının amacı, Linux’ta dosya yönetimini komutlarla öğrenmek ve her komutun ne yaptığını anlayarak pekiştirmektir.

---

## Part 1 - Creating and Editing Files

### 📁 1.1 mkdir — Yeni klasör oluşturur
Bir klasör (dizin) oluşturmak için kullanılır.
**Örnek:**

```bash
mkdir linux-practice
cd linux-practice
```

---

### 📝 1.2 cat > filename — Dosya oluşturup içine yazı yazar
Girilen metni dosyaya kaydeder, çıkmak için Ctrl + D kullanılır.
**Örnek:**

```bash
cat > notes.txt
Linux is powerful.
Linux is flexible.
Linux is secure.
Learning Linux is fun.
Always practice more!
```

---

### 👀 1.3 cat filename — Dosya içeriğini ekranda gösterir
**Örnek:**

```bash
cat notes.txt
```

---

### ➕ 1.4 echo "..." >> filename — Dosyaya satır ekler
`>>` mevcut dosyanın sonuna ekleme yapar.
**Örnek:**

```bash
echo "Linux is open-source." >> notes.txt
```

---

### 🔢 1.5 wc — Dosyadaki satır, kelime ve karakter sayısını gösterir
**Örnek:**

```bash
wc notes.txt
```

---

### 🔝 1.6 head -n — Dosyanın ilk n satırını gösterir
**Örnek:**

```bash
head -3 notes.txt
```

---

### 🔚 1.7 tail -n — Dosyanın son n satırını gösterir
**Örnek:**

```bash
tail -n 2 notes.txt
```

---

### 🔢 1.8 cat -n — Dosyayı satır numaralarıyla birlikte gösterir
**Örnek:**

```bash
cat -n notes.txt
```

---

## Part 2 - Viewing and Comparing Files

### 📄 2.1 echo — Hızlıca içerik oluşturur
Basit metinleri bir dosyaya yazmak için kullanılır.
**Örnek:**

```bash
echo "Linux is great for servers." > server.txt
echo "Linux is excellent for developers." > dev.txt
```

---

### 📚 2.2 cat file1 file2 — Birden fazla dosyanın içeriğini birleştirip gösterir
**Örnek:**

```bash
cat server.txt dev.txt
```

---

### 🔀 2.3 cat > newfile veya cat file1 file2 > newfile — Dosyaları birleştirip yeni bir dosyaya yazar
**Örnek:**

```bash
cat server.txt dev.txt > combined.txt
```

---

### ⚖️ 2.4 diff — İki dosyayı satır satır karşılaştırır
Aradaki farkları ekranda gösterir.
**Örnek:**

```bash
diff server.txt dev.txt
```

---

### 🔤 2.5 sort — Dosya içeriğini alfabetik olarak sıralar
**Örnek:**

```bash
sort notes.txt > sorted.txt
```

---

### 🚫 2.6 uniq — Tekrarlanan satırları çıkarır
Genellikle sort komutuyla birlikte kullanılır.
**Örnek:**

```bash
sort notes.txt | uniq
```

---

## Part 3 - Searching Files

### 🔍 3.1 grep — Dosya içinde kelime veya desen arar

#### 📘 Örnek dosya oluşturma:
```bash
cat > search.txt
Linux is an open-source operating system.
Many developers love Linux.
Linux distributions include Ubuntu, Fedora, and Debian.
Open-source software encourages collaboration.
```

#### a) Basit arama
“Linux” kelimesini içeren satırları bulur.
```bash
grep "Linux" search.txt
```

#### b) Büyük/küçük harf farkını önemsemeden arama
```bash
grep -i "linux" search.txt
```

#### c) Eşleşmeyen satırları gösterme
```bash
grep -v "open" search.txt
```

#### d) Satır numaralarıyla birlikte gösterme
```bash
grep -n "Linux" search.txt
```

#### e) Eşleşmeden sonra 3 satırı gösterme
```bash
grep -A3 "Linux" search.txt
```

#### f) Eşleşmeden önce 2 satırı gösterme
```bash
grep -B2 "open-source" search.txt
```

---

### 🧭 3.2 find — Belirli ölçütlere göre dosya arar

#### a) Geçerli dizindeki tüm .txt dosyalarını bulur
```bash
find . -type f -name "*.txt"
```

#### b) 1 KB’dan büyük dosyaları bulur
```bash
find . -type f -size +1k
```

#### c) Son 1 gün içinde değişen dosyaları bulur
```bash
find . -mtime -1
```

#### d) Boş dosyaları bulur
```bash
find . -type f -empty
```

#### e) Boş .log dosyalarını siler (onay isteyerek)
```bash
find . -type f -name "*.log" -exec rm -i {} \;
```

---

## Part 4 - File Ownership and Permissions

### 👑 4.1 ls -l — Dosya sahipliği ve izinlerini gösterir
Her dosyanın sahibi, grubu ve izinleri hakkında bilgi verir.
**Örnek:**

```bash
echo "Restricted content" > access.txt
ls -l access.txt
```

---

### 🧍 4.2 chown — Dosyanın sahibini değiştirir
**Örnek:**

```bash
sudo chown root access.txt
```

---

### 👥 4.3 chgrp — Dosyanın grup sahipliğini değiştirir
**Örnek:**

```bash
sudo chgrp root access.txt
```

---

### 🔐 4.4 chmod — Dosya izinlerini değiştirir
Örnek: 600, yalnızca sahibine okuma ve yazma izni verir.
**Örnek:**

```bash
chmod 600 access.txt
```

---

### 🔎 4.5 Değişiklikleri kontrol et
```bash
ls -l access.txt
```

---

✅ Öğrenilenler
- Dosya oluşturma, görüntüleme, birleştirme
- Farkları ve aramaları yönetme (diff, grep, find)
- Sahiplik ve izinleri değiştirme (chown, chmod, chgrp)
