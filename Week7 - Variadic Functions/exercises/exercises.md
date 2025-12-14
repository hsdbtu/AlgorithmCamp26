## **Başlangıç**

### **1. SORU**
Kendisine gönderilen adet kadar int sayının toplamını hesaplayan
esnek argümanlı bir fonksiyon yazınız.

**Fonksiyon prototipi:**
```c
int toplam(int adet, ...);
```

**Örnek kullanım:**
```c
toplam(3, 5, 10, 15); // 30
```

### **2. SORU**  
Kendisine gönderilen sayıların ortalamasını döndüren esnek argümanlı bir fonksiyon yazınız.

**Fonksiyon prototipi:**
```c
double ortalama(int adet, ...);
```
📌 Bölme işlemi sırasında double tür dönüşümüne dikkat ediniz.


## **Orta**

### **1. SORU**  
Kendisine gönderilen sayılar arasındaki en büyük (max) ve
en küçük (min) değeri bulan iki ayrı esnek argümanlı fonksiyon yazınız.

**Fonksiyon prototipleri:**
```c
int maxBul(int adet, ...);
int minBul(int adet, ...);
```c

**Örnek:**
```c
maxBul(5, 3, 7, 2, 9, 4); // 9
minBul(5, 3, 7, 2, 9, 4); // 2
```

### **2. SORU**  
İlk parametre olarak bir karakter türü alan (`'i'` → int, `'f'` → double)
ve bu türe göre **tek bir değeri** ekrana yazdıran esnek argümanlı bir fonksiyon yazınız.

**Fonksiyon prototipi:**
```c
void yazdir(char tur, ...);
```

**Örnek kullanım:**
```c
yazdir('i', 10);     // Int: 10
yazdir('f', 3.14);   // Float: 3.14
```

📌 `va_arg` kullanırken doğru türü seçtiğinizden emin olunuz.


## **Zor (Advanced)**

### **1. SORU**  
Basit bir **log fonksiyonu** yazınız.
Fonksiyon, ilk parametre olarak bir **format string**, devamında esnek argümanlar almalıdır.

**Fonksiyon prototipi:**
```c
void logla(const char *format, ...);
```

**Örnek kullanım:**
```c
logla("Sayi: %d, Metin: %s", 10, "Deneme");
```

📌 İpucu:
- `printf` benzeri çalışması beklenmektedir
- `stdarg.h` zorunludur