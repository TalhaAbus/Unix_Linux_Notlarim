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
- 

















































