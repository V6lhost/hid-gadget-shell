Not: Eğer cihazınıza bir zarar verirseniz sorumluluk kabul etmiyorum, her ne kadar basit bir işlem de olsa her şey sizin sorumluluğunuzda, bunu göz önünde bulundurarak talimatları uygulayın.
Not: Klavye dilini ingilizce olarak ayarlarsanız daha sağlıklı çalışacaktır.

Gereksinimler:
	Android cihaz
	Root
	3.19 veya daha yüksek Android kernel sürümü
	Kernel'de ConfigFS desteği
	Termux uygulaması (F-Droid üzerinden indirin)

Not: Termux için gereksinimleri şu komutu kopyalayarak indirebilirsiniz;
```
pkg install tsu libllvm
```

Eğer cihazınız gereksinimleri karşılıyor ise işlemlere başlayabiliriz. 
İlk olarak aşağıdaki link üzerinden USB Gadget Tool uygulamasını indiriyoruz. Bizim için cihazımızı bilgisayarımıza bir HID cihazı olarak tanımlayan uygulama bu.

[USB Gadget Tool](https://f-droid.org/repo/net.tjado.usbgadget_4.apk)

Uygulamayı indirdikten sonra uygulamaya girin ve Root yetkilerini onaylayın. Device info kısmına gelip aşağıdaki değerleri kontrol edin;

![preview](https://github.com/V6lhost/hid-gadget-shell/blob/master/kernelkontrol.png)
![preview](https://github.com/V6lhost/hid-gadget-shell/blob/master/configfskontrol.png)
![preview](https://github.com/V6lhost/hid-gadget-shell/blob/master/hidkontrol.png)
Root yetkileri onaylandıktan sonra sağ üst köşedeki '+' butonuna basarak klavye-mouse ekleyin.

![preview](https://github.com/V6lhost/hid-gadget-shell/blob/master/eklemebutonu.png)
Açılan pencerede "Mouse & Keyboard" seşeneğini seçin ardından "Gadgets" sekmesine dönün.

![preview](https://github.com/V6lhost/hid-gadget-shell/blob/master/keyboardsecimi.png)
HID Gadgetini sağ altındaki butona dokunarak aktifleştirin.

![preview](https://github.com/V6lhost/hid-gadget-shell/blob/master/hidaktiflestirme.png)
Not: Buradan HID Gadgetini etkinleştirdikten sonra MTP gibi diğer özellikleri kullanamazsınız. Tekrar eski haline döndürmek için en çok fonksiyona sahip olan gadgeti tekrar etkinleştirmeniz lazım.

Burada USB Gadget Tool ile işimiz bitti. Termux uygulamasını açıyoruz ve aşağıdaki komutu kullanarak Github üzerinden düzenleyerek rakamları eklediğim "hid" dosyasını indiriyoruz.

```
wget https://github.com/V6lhost/hid-gadget-shell/raw/master/hid
```

Ardından dosyayı termux'un /bin dizinine kopyalayıp çalıştırma yetkisi veriyoruz.

```
cp hid /data/data/com.termux/files/usr/bin
```
```
chmod +x /data/data/com.termux/files/usr/bin/hid
```

Eğer isterseniz kolaylık olması için root yetkilerini kullanarak şimdiden sistem dosyalarındaki /bin içerisine kopyalayabilirsiniz. Çünkü bu dosyayı çalıştırırken root yetkilerine sahip olmamız gerekecek.

Bu kadar. Şimdi cihazınızı bir bilgisayara bağlayarak test edebilirsiniz. Bilgisayarınıza bağladıktan sonra aşağıdaki kodu yazarak seçenekleri kullanabilirsiniz. 

Klavye için:
```
sudo hid /dev/hidg0 keyboard
```

Burada kullanabileceğiniz tuşların bir listesi bulunuyor. Ek olarak ingilizce harfleri(Türkçe karakterler çalışmıyor) direkt olarak yazarak gönderebilirsiniz. İki tuşa aynı anda basmak için ikisini yan yana arasında bir boşluk olacak şekilde yazın.

Fare için:
```
sudo hid /dev/hidg1 mouse
```

Fare imlecini kullanmak için `--b1 {dikey px sayısı} {yatay px sayısı}` şeklinde yazıp gönderin.
