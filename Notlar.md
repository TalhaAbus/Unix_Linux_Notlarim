- İşletim sistemleri kernel yapısına göre sınıflandırılabilir.

1. Monolithic: Bütünsel
2. Micro

**Monolithic Kernel:** Kernel'in kendisi büyük bir yer kaplıyor. Yani kernel modda çalışan ögelerin sayısı fazla demek.
**MikroKernel:** Minimal bir kernel modda çalışan parça var. Tüm driverlar user mode da çalışıyor.

![image](https://github.com/TalhaAbus/Unix_Linux_Notlarim/assets/75746171/7cb7b298-0229-4f67-8841-60b611f0aa9c)

- Windows sistemleri daha çok monolithic tarafına kayan sistemlerdir.

**Gerçek zamanlı işletim sistemleri (RTOS)**:
- Sizin bir işletim sisteminiz var, dış dünyada bir takım olaylar oluyoır. Mesela sıcaklık belli bir düzeye çıkar çıkmaz çok hızlı bir cevap gerekiyor. Gecikmeye tahammül yok. Bunu sağlayan sistemler gerçek zamanlı işletim sistemleridir.
- Gerçek zamanlı yapmak istersen bir işletim sisteminin performansı düşebilir. Bu yüzden her sistem gerçek zamanlı değildir.

**Neden diğer işletim sistemleri gerçek zamanlı değil?**
- Multi processing sistem, process leri zaman paylaşımlı olarak çalıştıroyor. Bir process çalışıyor, sonra duruyor ve kalan yer not alınıyor. Sonra başka process çalışıyor.

![image](https://github.com/TalhaAbus/Unix_Linux_Notlarim/assets/75746171/41a2f981-4220-4c28-8076-64c329971a06)

- Burada P3 processindeyken, P1'in ilgilendiği bir dışsal olay gerçekleşmişse P1 bunu sadece sıra P1'e gelmişse algılayabilir. O zaman böyle bir tasarım gerçek zamanlı olamaz.
- RTOS lar microkernel'a daha yakın

**Android nasıl bir işletim sistemi?**
- Linux kernel alınıp bazı modülleri atılmış. Bir mobil işletim sistemi haline getirilmiş. Temelinde linux kernel kullanılan inux türevi bir işletim sistemi.
**IOS**
- Iphone operating system. Genel olarak macOS kodları buraya devşirilmiş durumda.

**SOC kavramı**
- Bir mikroişlemciyi bir entegre devrenin içine koyuyoruz. ÇEvre birimleri, RAM, ROM da koyuyurouz. Bilgisayarın önemli bileşenlerini tek bir çipe yerleştiriyoruz.  Yerleştiremediklerimizi dışarıda bırakıyoruz. Buna system on chip deniyor. 

**Client ve server işletim sistemleri**
- Server sistemlerinin kernel yapılarında server programlarının çalışmasına daha uygun olacak biçimde farklılıklar yaratılabiliyor. 

**Neden linux sistemleri daha çok komut satırından kullanılıyor?**

- Serverlara uzaktan erişilebildiği için genellikle bir grafik rayüzü içermiyorlar. Grafik arayüzü sistemi yavaşlatmaması açısından install edilmityor.

**64 bit işletim sistemi ne demek?**
- 64 bit bir intel işlemci aynı zamanda 32 bit bir intel işlemci gibi de çalıkşabiliyor.
- 32 bit bir işletim sisteminde processor ün 32 bir olduğu varsayılarak işletim sistemi yazılıyor. İşletim sisteminin tüm kernel ı 32 bit bir işlemci varmış gibi yazılmış. Halbuki 64 bit bir işlemcinin tek hamlede 64 bit bir işlemi yapabilmesinden kaynaklanan avantajları var.
- Yani 32 bit bir kernel da her şey 32 bit işlemci olduğu varsayımıyla yazıldığı için  64 bit bir işletim sistemine göre daha yavaş çalışması beklenir. 
- 32 bit bir işletim sisteminde bu processorlerde 4 gb ram kullnaılabiliyor. 64 bit ise 16 hekzabyte kadar. 
- Yani 32 bit işletim sistemi, kernel içnde 32 bit processorler dikakte alınarak 32 bit işlemler yapacak şekilde, 32 bit C compiler ile compile edilmiş. Ve diğer 64 bit C compiler ile 64 bit işlemler yapabilecek şekilde compile edilmiş. Aynı zamanda 64 bit işeletim sistemleri 64 bi işlemcinin sağladığı birçok avantajları kullnaabilme yeteneğine de sahip. 
- Biz kodu 32 veya 64 bit olarak derleyebiliriz. 32 bit derleme yaparsak biz sanki 32 bit işlemci kullanıyormuşuz gibi bir makine dili üretiyor.

**POSIX katmanına neden gerek var?**
- Posix katmanı olmasaydı ya ben işletim sisteminin sistem fonksiyonlarını çağırmak zorunda kalırdım ya da standart C fonksiyonları ile idare etmek zorunda kalırdım. Standart C fonksiyonları yetersiz çünkü en büyük ortab bölem biçiminde. Sistem fonksiyonları da portable değil, her işletim sisteminin sistem fonksiyonları farklı olabiliyor.  O zaman UNİX türevi işletim sistemlerini temsil eden oradaki mantığa göre düzenlenmiş ayrı bir portable katmana ihtiyaç var. 
**Bir POSIX fonksiyonu çağırıldığında, her zaman bir sistem fonksiyonlarını mı çağırıyor?**
- Bazı POSIX fonksiyonları hiçbir sistem fonksiyonunu çağırmıyor. Bazısı ise doğrudan sistem fonksiyonlarını çağırıyor. Bazısı ise birden fazla sistem fonksiyonunu çağırıyor olabilir.

**C'de ben dosyayı fopen fonksiyonu ile açıyorum. Dosyayı gerçekten ben açmıyor muyum?**
- Dosya işlemleri, karmaşık kernel işlemlerini gerektiriyor. Dosya işlemlerinin hepsi user mode'da yapılamayacak, kernel tarafından yapılabilecek işlemler. Dosyalar en sonunda işletim sisteminin sistem fonksiyonu çağırılarak açılır.
- Mesela fopen kodlarında bir takım işlemlerden sonra "open" POSIX fonksiyonunun çapırıldığını göreceksiniz. Open POSIX fonksiyonunu kodlarına bakınca da hemen sysopen sistem fonksiyonunun çağırılıdğını göreceksiniz.

**İşletim sisteminin tüm faaliyetleri sistem fonksiyonları tarafından mı yürütülüyor?**
- Hayır, işletim sistemminin pek çok faaliyeti var. Sistem fonksiyonları sadece dış dünyadan işletim sistemine iş yaptırabilmek için  kullanılan bir arayüz. Yani işletim sistemi = sistem fonksiyonları demek değildir.
- Ve işletim sistemine bir iş yaptırılacaksa bunu yaptırabileceğimiz en düşük seviye sistem fonksqiyonlarını çağırmak olabilir.
- Eğer kernel mode'a geçmiyorsak, driver yazmıyorsak çalışılabilrcek en alt seviye sistem fonksiyonlarını çağırmaktır. Daha aşağıya geçtiğimiz an kendimizi kernel içinde buluruz. Yani kernel'a en çok yaklaştığımız yer sistem fonksiyonlarını çağırdığımız zamandır.

**Device Driverlar**
- Kernel içne eklenmiş kodlar olarak düşünülebilir. Nasıl bir bilgisayarın içine bir bilgisayar kartı alıp desktop bilgisayarkların genişleme yuvasına kart takılıyorsa, kernel'a kart takmanın yazılımsal karşılığı da driver. Dolayısıyla bir driver yazdığımız aman o artık kernel ile aynı ddüzeyde çalışıyor. 
- Sistem fonksiyonları da kernel içerisnideki fonksiyonları tetikliyor, driver fonksiyonlarını da çağıorabiliyor. Yapı olarak her iki yodlan da kernel içindeki kod çalışıyor. 

- Kernel içerisinde sadece interface oluşturan bu fonksiyonlar yok. Bunlar dış dünya ile interface oluşturan sistem fonksiyonları. Bunun yanında driver için interface oluşturan fonksiyonlar da var. Yani driver yazanların daha dip katmanlarda  kullanabileceği fonksiyon grubu da var. Bunlara export edilmiş kernel fonksiyonları deniliyor.

**GNU Komut satırı argümanları:**

- İşletim sistemi komut satırı argümanlarının toplaytıp main fonksiyonuna parametre olarak geçiyor. 

## Prosesler Arasında Altlık-Üstlük (Parent-Child) İlişkisi

**Process ID değeri nedir?**
- O process i sistemde teşhis etmek içiçn kullanılan unique tam sayısal bir değerdir.

**Process ID değerini programlamada kullanacak olsam hangi tam sayı türünün içerisine sığar?**
- Unix linux sitemlerinde sistemleri gerçekleştirenler türleri sürekli oalrak farklı aldıkları için, bunları portable arayüzü olan posix arayüzünde kullanılabilmesi için (yani kaynak kodda bir taşınabilirlik sağlaması için) bazı türler _t_ ile typedef edilmiş. 

**Process ID değeri programcı için en anlam ifade ediyor?**
- Sistem programcısı process ID değeri ile ilerideki konualr bağlamında bunun kullanmak zorunda kalıyor. Ama kernel için process ID değerinin ifade ettiği anlam, aslında process in bütün bilgilerinin saklı olduğu, process kontrol blok diye kavramlaştırdığımız linuxtaki task struct yapısı olarak gerçekleştirilen bu veri yapısınaa erişmek için bir anahtar olarak kullnaıyor kernel bunu.

## Processlerin kullanıcı ve grup ID leri
- User ve grup Id bir process in yetki derecesini belirlemekte kullanılıyor. 

1. Gerçek userID 
2. Efektif UserID

1. Gerçek GrupID
2. Efektif GrupID






































