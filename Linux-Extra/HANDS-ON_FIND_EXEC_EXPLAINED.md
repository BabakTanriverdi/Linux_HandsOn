# 🧠 Hands-on Linux-Extra : Using `find` Command with `-exec` (Explained)

## 🎯 Purpose
Bu laboratuvarın amacı, `find` komutunun `-exec` parametresi ile birlikte nasıl güçlü ve esnek şekilde kullanılabileceğini öğretmektir.  
Her örnek, hem açıklama hem de uygulama komutu içerir.

---

## 🔧 1️⃣ find + ls — Bulunan dosyaların detaylarını listele

### 📘 Komut:
```bash
find . -type f -name "*.txt" -exec ls -lh {} \;
```

### 🧩 Açıklama:
- `find .` → bulunduğun dizinden başla  
- `-type f` → sadece dosyaları ara  
- `-name "*.txt"` → .txt uzantılı dosyaları bul  
- `-exec ls -lh {} \;` → her bulduğu dosyayı ayrıntılı (`-l`) ve okunabilir boyutta (`-h`) listele  

### 💡 Sonuç:
Bulduğu her `.txt` dosyayı, boyut ve tarih bilgisiyle listeler.

---

## 🧹 2️⃣ find + rm — Dosyaları onaysız sil

### 📘 Komut:
```bash
find . -type f -name "*.bak" -exec rm -f {} \;
```

### 🧩 Açıklama:
- `.bak` → yedek dosyalarını temsil eder  
- `rm -f` → dosyaları **onay sormadan** siler  
- `{}` → her bulunan dosya  
- `\;` → komut sonu  

⚠️ **Uyarı:** Bu komut tehlikelidir — dikkat et, geri dönüşü yok.

---

## 🛡️ 3️⃣ find + chmod — Bulunan dosyaların izinlerini değiştir

### 📘 Komut:
```bash
find /var/www -type f -name "*.sh" -exec chmod 755 {} \;
```

### 🧩 Açıklama:
- `/var/www` → arama yapılacak dizin  
- `.sh` → tüm shell script dosyaları  
- `chmod 755` → sahibine yazma/çalıştırma, diğerlerine okuma/çalıştırma izni verir  

### 💡 Sonuç:
Web dizinindeki tüm script’ler çalıştırılabilir hale gelir.

---

## 🚚 4️⃣ find + mv — Bulunan dosyaları başka bir dizine taşı

### 📘 Komut:
```bash
find . -type f -name "*.log" -exec mv {} /tmp/logs/ \;
```

### 🧩 Açıklama:
- `mv` → dosya taşıma  
- `{}` → her bulunan dosya  
- `/tmp/logs/` → hedef dizin  

### 💡 Sonuç:
Bulunan tüm `.log` dosyaları `/tmp/logs/` dizinine taşınır.

---

## 📝 5️⃣ find + cp — Dosyaları başka bir yere kopyala

### 📘 Komut:
```bash
find . -type f -name "*.conf" -exec cp {} /backup/configs/ \;
```

### 🧩 Açıklama:
- `.conf` → yapılandırma (config) dosyalarını bulur  
- `cp` → dosyaları kopyalar  
- `/backup/configs/` → yedekleme klasörü  

### 💡 Sonuç:
Tüm `.conf` dosyaları güvenli bir şekilde yedeklenir.

---

## 🧠 6️⃣ find + grep — İçeriğinde belirli kelime geçen dosyaları bul

### 📘 Komut:
```bash
find . -type f -exec grep -l "password" {} \;
```

### 🧩 Açıklama:
- `grep -l` → içinde “password” geçen dosyaların sadece adını listeler  
- `{}` → her dosyayı tek tek kontrol eder  

### 💡 Sonuç:
“password” kelimesi geçen dosyaları tespit eder.  
Bu yöntem güvenlik kontrollerinde sıkça kullanılır 🔒

---

## 🧾 7️⃣ find + tar — Bulunan dosyaları arşivle

### 📘 Komut:
```bash
find . -type f -name "*.log" -print | tar -cvf logs.tar -T -
```

### 🧩 Açıklama:
- `find . -type f -name "*.log" -print` → tüm `.log` dosyalarının listesini üretir  
- `tar -cvf logs.tar -T -` → bu listeyi alıp `logs.tar` adında arşiv oluşturur  

### 💡 Sonuç:
Tüm log dosyaları tek bir `logs.tar` arşivinde toplanır.

---

## 🏁 Özet

| Amaç | Komut |
|------|--------|
| `.txt` dosyaları listele | `find . -type f -name "*.txt" -exec ls -lh {} \;` |
| `.bak` dosyalarını sil | `find . -type f -name "*.bak" -exec rm -f {} \;` |
| `.sh` script izinlerini değiştir | `find /var/www -type f -name "*.sh" -exec chmod 755 {} \;` |
| `.log` dosyalarını taşı | `find . -type f -name "*.log" -exec mv {} /tmp/logs/ \;` |
| `.conf` dosyalarını yedekle | `find . -type f -name "*.conf" -exec cp {} /backup/configs/ \;` |
| “password” içeren dosyaları bul | `find . -type f -exec grep -l "password" {} \;` |
| `.log` dosyalarını arşivle | `find . -type f -name "*.log" -print | tar -cvf logs.tar -T -` |

---

✅ **Öğrenilenler**
- `find` komutuyla farklı eylemler gerçekleştirme  
- `-exec` yapısının gücü ve esnekliği  
- Dosya yönetimi, güvenlik ve yedekleme işlemleri için pratik örnekler
