### **Başlangıç**

1.Ekrana kendi adınızı ve soyadınızı yazdırın.

```c
#include <stdio.h>

int main() {
printf("Mitski Miyawaki");
return 0;
}

```

2.Kullanıcıdan iki sayı alıp toplamını ekrana yazdırın.

```c
#include <stdio.h>

int main() {
int a,b;
printf("Lutfen iki tane sayi giriniz: ");
scanf("%d %d",\&a,\&b);
printf("Toplam: %d",a+b);
return 0;
}

```



### **Orta**

1.Kullanıcının yaşını alıp doğduğu yılı hesaplayan bir program yazın.

```c
#include <stdio.h>

int main() {
int dogumYili=0;
printf("Lutfen dogdunuz yili giriniz: ");
scanf("%d",\&dogumYili);
printf("Yasiniz: %d",2025-dogumYili);
return 0;
}

```



### **Zor (Advanced)**

1.Kullanıcıdan bir metin alıp uzunluğunu bulan program yazın.

```c
#include <stdio.h>

int main() {
char cumle\[1000];
printf("Lutfen bir cumle giriniz:");
gets(cumle);
int i=0;
while(cumle\[i] != '\\0')
i++;
printf("Girilen cumlenin uzunlugu: %d",i);
return 0;
}

```

