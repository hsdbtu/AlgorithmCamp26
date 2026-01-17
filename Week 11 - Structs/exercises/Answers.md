## **Başlangıç**

### **1. SORU**

Bir `struct Ogrenci` tanımlayınız.
Struct aşağıdaki alanları içermelidir:

* `int no`
* `float ort`

Kullanıcıdan bilgileri alıp ekrana yazdıran programı yazınız.

Çözüm:

```c
#include <stdio.h>

struct Ogrenci {
    int no;
    float ort;
};

int main() {
    struct Ogrenci o;

    scanf("%d", &o.no);
    scanf("%f", &o.ort);

    printf("No: %d\nOrtalama: %.2f\n", o.no, o.ort);

    return 0;
}
```

---

## **Orta**

### **1. SORU**

Bir `struct Kitap` tanımlayınız:

* Kitap adı (`char dizi`)
* Sayfa sayısı
* Fiyat

Struct değişkenini **fonksiyon parametresi** olarak gönderip bilgileri yazdırınız.

Çözüm:

```c
#include <stdio.h>

struct Kitap {
    char ad[30];
    int sayfa;
    float fiyat;
};

void yazdir(struct Kitap k) {
    printf("%s %d %.2f\n", k.ad, k.sayfa, k.fiyat);
}

int main() {
    struct Kitap k;

    scanf("%s", k.ad);
    scanf("%d", &k.sayfa);
    scanf("%f", &k.fiyat);

    yazdir(k);

    return 0;
}
```

---

### **2. SORU**

5 elemanlı bir `struct Ogrenci` dizisi oluşturunuz.
Her öğrencinin numarasını ve ortalamasını kullanıcıdan alıp ekrana yazdırınız.

Çözüm:

```c
#include <stdio.h>

struct Ogrenci {
    int no;
    float ort;
};

int main() {
    struct Ogrenci ogr[5];

    for(int i = 0; i < 5; i++) {
        scanf("%d %f", &ogr[i].no, &ogr[i].ort);
    }

    for(int i = 0; i < 5; i++) {
        printf("%d %.2f\n", ogr[i].no, ogr[i].ort);
    }

    return 0;
}
```

---

## **Zor**

### **1. SORU**

Dinamik bellek kullanarak:

* `n` elemanlı bir `struct Ogrenci` dizisi oluşturunuz
* Ortalamaların genel ortalamasını hesaplayınız

📌 `malloc` kullanılmalıdır.

Çözüm:

```c
#include <stdio.h>
#include <stdlib.h>

struct Ogrenci {
    int no;
    float ort;
};

int main() {
    int n;
    float toplam = 0;

    scanf("%d", &n);

    struct Ogrenci *ogr = (struct Ogrenci*)malloc(n * sizeof(struct Ogrenci));

    for(int i = 0; i < n; i++) {
        scanf("%d %f", &ogr[i].no, &ogr[i].ort);
        toplam += ogr[i].ort;
    }

    printf("Genel Ortalama: %.2f\n", toplam / n);

    free(ogr);
    return 0;
}
```

---

### **2. SORU (Advanced)**

Bir `struct Node` tanımlayınız:

* `int data`
* `struct Node *next`

Bu struct kullanılarak **tek yönlü bağlı listenin ilk düğümünü**
dinamik olarak oluşturunuz ve ekrana yazdırınız.

Çözüm:

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

int main() {
    struct Node *head = (struct Node*)malloc(sizeof(struct Node));

    head->data = 10;
    head->next = NULL;

    printf("Data: %d\n", head->data);

    free(head);
    return 0;
}
```
