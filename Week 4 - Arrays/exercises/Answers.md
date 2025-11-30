## **Başlangıç**

- **1. SORU**
int sayilar[] = {10, 20, 30, 40, 50}; şeklinde tanımlanmış bir dizinin tüm elemanlarının toplamını bulan bir döngü nasıl kurulur?
```c
#include <stdio.h>

int main() {
    int sayilar[] = {10, 20, 30, 40, 50};
    int toplam = 0;

    for (int i = 0; i < 5; i++) {
        toplam += sayilar[i];
    }

    printf("Toplam: %d\n", toplam);

    return 0;
}
```

- **2. SORU**  
Bir karakter dizisi (string) içinde belirli bir harfin (örneğin 'e' harfinin) ilk olarak hangi indekste bulunduğunu bulan bir kod yazınız. Harf bulunamazsa -1 döndürsün.
```c
#include <stdio.h>

int main() {
    char metin[100];
    char aranan = 'e';
    int index = -1;

    printf("Bir metin girin: ");
    fgets(metin, sizeof(metin), stdin);

    for (int i = 0; metin[i] != '\0'; i++) {
        if (metin[i] == aranan) {
            index = i;
            break;
        }
    }

    printf("Ilk '%c' harfinin indeksi: %d\n", aranan, index);
    return 0;
}
```


## **Orta**

- **1. SORU**  
Bir cümledeki (karakter dizisi) kelime sayısını bulan bir C programı yazınız. (İpucu: Boşluk karakterlerini sayabilirsiniz.)
```c
#include <stdio.h>

int main() {
    char cumle[200];
    int kelimeSayisi = 0;

    printf("Bir cumle girin: ");
    fgets(cumle, sizeof(cumle), stdin);

    for (int i = 0; cumle[i] != '\0'; i++) {
        if (cumle[i] == ' ' && cumle[i+1] != ' ' && cumle[i+1] != '\n' && cumle[i+1] != '\0') {
            kelimeSayisi++;
        }
    }

    // Eğer ilk karakter boşluk değilse 1 kelime vardır
    if (cumle[0] != ' ' && cumle[0] != '\n') {
        kelimeSayisi++;
    }

    printf("Kelime sayisi: %d\n", kelimeSayisi);
    return 0;
}
```

- **2. SORU**  
Bir tam sayı dizisinin elemanlarının aritmetik ortalamasını hesaplayan bir C fonksiyonu tasarlayınız.
```c
#include <stdio.h>

float ortalama(int dizi[], int boyut) {
    int toplam = 0;

    for (int i = 0; i < boyut; i++) {
        toplam += dizi[i];
    }
    return (float)toplam / boyut;
}

int main() {
    int sayilar[] = {4, 10, 6, 20, 8};
    int boyut = sizeof(sayilar) / sizeof(sayilar[0]);

    printf("Ortalama: %.2f\n", ortalama(sayilar, boyut));
    return 0;
}
```


## **Zor (Advanced)**

- **1. SORU**  
Bir tam sayı dizisi içindeki en sık tekrar eden elemanı (modu) bulan bir C programı yazınız. Eğer birden fazla eleman aynı en yüksek tekrar sayısına sahipse herhangi birini bulması yeterlidir.
```c
#include <stdio.h>

int main() {
    int dizi[] = {4, 2, 4, 5, 2, 4, 3, 2};
    int boyut = sizeof(dizi) / sizeof(dizi[0]);

    int mod = dizi[0];
    int maxTekrar = 0;

    for (int i = 0; i < boyut; i++) {
        int sayac = 0;

        for (int j = 0; j < boyut; j++) {
            if (dizi[i] == dizi[j]) {
                sayac++;
            }
        }

        if (sayac > maxTekrar) {
            maxTekrar = sayac;
            mod = dizi[i];
        }
    }

    printf("Mod: %d (Tekrar sayisi: %d)\n", mod, maxTekrar);
    return 0;
}
```