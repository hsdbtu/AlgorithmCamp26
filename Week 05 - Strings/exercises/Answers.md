## **Başlangıç**

- **1. SORU**
Kullanıcıdan bir kelime alan ve bu kelimeyi ekrana yazdıran bir C programı yazınız.
(Örn: Girdi → Merhaba, Çıktı → Merhaba)
```c
#include <stdio.h>

int main() {
    char kelime[100];
    
    printf("Bir kelime girin: ");
    scanf("%s", kelime);
    
    printf("%s\n", kelime);
    
    return 0;
}
```

- **2. SORU**  
Kullanıcıdan bir kelime alıp, kelimenin ilk ve son karakterlerini ekrana yazdıran bir program yazınız.
(Örnek: kalem → ilk: k, son: m)
```c
#include <stdio.h>
#include <string.h>

int main() {
    char kelime[100];
    int uzunluk;
    
    printf("Bir kelime girin: ");
    scanf("%s", kelime);
    
    uzunluk = strlen(kelime);
    
    printf("ilk: %c, son: %c\n", kelime[0], kelime[uzunluk-1]);
    
    return 0;
}
```


## **Orta**

- **1. SORU**  
Kullanıcıdan bir metin alan ve bu metnin içinde kaç tane 'a' harfi geçtiğini bulan bir C programı yazınız.
```c
#include <stdio.h>

int main() {
    char metin[200];
    int sayac = 0;
    int i;
    
    printf("Bir metin girin: ");
    getchar(); // Buffer temizleme
    fgets(metin, sizeof(metin), stdin);
    
    for(i = 0; metin[i] != '\0'; i++) {
        if(metin[i] == 'a' || metin[i] == 'A') {
            sayac++;
        }
    }
    
    printf("Metinde %d tane 'a' harfi var.\n", sayac);
    
    return 0;
}
```

- **2. SORU**  
Kullanıcıdan bir kelime alın ve strlen kullanmadan, kendi yazdığınız döngü ile kelimenin uzunluğunu ekrana yazdırın.
```c

#include <stdio.h>

int main() {
    char kelime[100];
    int uzunluk = 0;
    
    printf("Bir kelime girin: ");
    scanf("%s", kelime);
    
    while(kelime[uzunluk] != '\0') {
        uzunluk++;
    }
    
    printf("Kelimenin uzunlugu: %d\n", uzunluk);
    
    return 0;
}
```


## **Zor (Advanced)**

- **1. SORU**  
Kullanıcıdan bir kelime alın ve bu kelimenin tersini ekrana yazdıran bir C programı yazınız.
(Örnek: kitap → patik)
```c
#include <stdio.h>

int main() {
    char kelime[100];
    char ters[100];
    int uzunluk = 0;
    int i;
    
    printf("Bir kelime girin: ");
    scanf("%s", kelime);
    
    while(kelime[uzunluk] != '\0') {
        uzunluk++;
    }

    for(i = 0; i < uzunluk; i++) {
        ters[i] = kelime[uzunluk - 1 - i];
    }
    
    ters[uzunluk] = '\0';
    
    printf("%s\n", ters);
    
    return 0;
}
```