# **4. Hafta – Diziler (Arrays)**
## 0. Dizi (Array) Nedir?

Dizi, aynı türde birden fazla veriyi tek bir değişken adı altında saklamamızı sağlayan yapılardır.
Bir dizi, aslında yan yana dizilmiş birçok kutudan oluşan bir yapıdır.

Her elemanın bir indeksi (index) vardır ve C dilinde indeksler 0’dan başlar.

### Örnek:
```c
int sayilar[5] = {10, 20, 30, 40, 50};
```

###  Açıklama:
  - int → Dizinin eleman türü
  - sayilar → Dizi adı
  - [5] → Dizinin boyutu (toplam eleman sayısı)
  - {10, 20, 30, 40, 50} → Dizi elemanları

💡 Not: Dizi boyutu sabittir ve tanımlandıktan sonra değiştirilemez.

---

## 1. Dizi Elemanlarına Erişim

Bir dizi elemanına ulaşmak için dizinin adı ve indeks numarası kullanılır.
### Örnek:
```c
printf("%d", sayilar[0]);  // 10
printf("%d", sayilar[3]);  // 40
```

### Eleman Değiştirme:
```c
sayilar[2] = 999;   // 30 yerine 999 gelir
```

---

## 2. Kullanıcıdan Diziye Veri Alma

Genellikle kullanıcıdan birden fazla değer alıp diziye kaydetmek için döngüler kullanılır.

### Örnek: 5 Elemanlı bir dizi doldurma
```c
int sayilar[5];

for (int i = 0; i < 5; i++) {
    printf("%d. sayiyi girin: ", i + 1);
    scanf("%d", &sayilar[i]);
}
```

---

## 3. Dizi Elemanlarını Yazdırma
```c
for (int i = 0; i < 5; i++) {
    printf("%d ", sayilar[i]);
}
```

---

## 4. Örnek – Dizideki En Büyük Sayıyı Bulma
```c
int sayilar[5] = {12, 45, 3, 22, 18};
int max = sayilar[0];

for (int i = 1; i < 5; i++) {
    if (sayilar[i] > max) {
        max = sayilar[i];
    }
}

printf("En buyuk sayi: %d\n", max);
```

---

## 5. Örnek – Ortalama Hesaplama
```c
int notlar[5];
int toplam = 0;

for (int i = 0; i < 5; i++) {
    printf("%d. notu girin: ", i + 1);
    scanf("%d", &notlar[i]);
    toplam += notlar[i];
}

float ort = toplam / 5.0;
printf("Ortalama: %.2f\n", ort);
```

---

## 6. Çözerken Eğlenebileceğiniz Kaynaklar
  - GeeksForGeeks – [C Arrays](https://www.geeksforgeeks.org/c/c-arrays/)
  - W3Schools – [C Arrays](https://www.w3schools.com/c/c_arrays.php)
  - YouTube – [C Arrays Explained](https://www.youtube.com/watch?v=eE9MnoS0lc0)

---

## 7. Ödev
  - exercises klasörüne bakın.