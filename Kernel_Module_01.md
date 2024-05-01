# Kernel Modülü nedir?

- **Kernel modülleri** işletim sisteminin çekirdeği olan linux kernel'ine dinamik olarak yüklenip çıkartılabilen parçalardır.
- İşletim sisteminin çekirdeğine isteğe bağlı olarak çalışma durumundayken yüklenip çıkartılabilir. Normalde işletim sisteminin çekirdeğinde bir değişikik yapabilmek için sistemi yeniden başlatmamız gerekiyor. Ancak kernel modülleri ile çekirdeğie kod parçaları eklenebilir veya çıkartılabilir böylece sistemi yeniden başlatmaya gerek kalmaz.
- Bilgisayarda donanım cihazlarıyla etkileşim halinde bulunmak için işletim sistemi çekirdeğinin parçası olarak çalışan yazılımlar gereklidir. Bu yazılımlara sürücüler denir.


**Basit Bir Kernel Modülü Yazmak**

**Kernel Modülü Kodu Yazma:**

Bir kernel modülü, genellikle iki temel fonksiyon içerir: **init_module** ve **cleanup_module**. Bunlar modül yüklendiğinde ve kaldırıldığında çağrılır.

**Örnek bir kernel modülü:**

```C
#include <linux/module.h>  // Bu, kernel modülü için temel kütüphanedir
#include <linux/kernel.h>  // KERN_INFO için gerekli

int init_module(void)
{
    printk(KERN_INFO "Merhaba, dünya!\n");
    return 0;  // Başarıyla yüklendi
}

void cleanup_module(void)
{
    printk(KERN_INFO "Hoşçakal, dünya!\n");
}

MODULE_LICENSE("GPL");
MODULE_AUTHOR("Senin Adın");
MODULE_DESCRIPTION("Basit bir örnek modül");

```

**Makefile Oluşturma:**
Kernel modülünüzü derlemek için bir Makefile oluşturmanız gerekiyor. Bu, derleme sürecini otomatikleştiren bir scripttir.

**Örnek bir Makefile:**


```
obj-m += modul_adi.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```
**Modülü Derleme ve Test Etme:**

- Terminalde make komutunu çalıştırarak modülünüzü derleyin.
- Derlenmiş modülü yüklemek için sudo insmod modul_adi.ko kullanın.
- Modülü kaldırmak için sudo rmmod modul_adi kullanın.
- dmesg komutu ile kernel loglarını kontrol ederek modülünüzün çıktılarını görebilirsiniz.
**Debugging ve Loglama:**
- printk fonksiyonu, modülünüzden çıktılar yazdırmak için kullanılır. KERN_INFO, KERN_ERROR gibi farklı log seviyeleri vardır.










