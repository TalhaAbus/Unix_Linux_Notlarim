- Bir "Hello World!" kernel modülü yazalım.

1. Gerekli araçları kuralım.

```
sudo apt-get update
sudo apt-get install build-essential linux-headers-$(uname -r)
```

2. Kernel modülü kaynak dosyasını oluşturalım.
- hello_world.c adında bir dosya oluştur.

```CPP
#include <linux/module.h>       // Çekirdek modülü için temel kütüphaneler
#include <linux/kernel.h>       // KERN_INFO gibi makrolar için
#include <linux/init.h>         // __init ve __exit makroları için

MODULE_LICENSE("GPL");          // Modül lisansı
MODULE_AUTHOR("Your Name");     // Modül yazarı
MODULE_DESCRIPTION("A simple Hello World Kernel Module"); // Açıklama

static int __init hello_start(void)
{
    printk(KERN_INFO "Hello world\n");
    return 0;  // Başarılı yükleme
}

static void __exit hello_end(void)
{
    printk(KERN_INFO "Goodbye world\n");
}

module_init(hello_start);
module_exit(hello_end);
```























