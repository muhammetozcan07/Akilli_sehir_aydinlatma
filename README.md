# Akıllı Şehir Aydınlatma Sistemi

"Geleceğin sürdürülebilir şehirleri için tasarladığımız Akıllı Şehir Aydınlatma Sistemi çalışmamızda, enerji verimliliği ile yaya güvenliği arasındaki mükemmel dengeyi otonom olarak kurabilen yapay zeka tabanlı bir model geliştirdik. Pekiştirmeli Öğrenme (Q-Learning) algoritmaları kullanılarak eğitilen bu sistem; günün saatini, doğal ışık seviyesini ve sensörlerden gelen anlık hareket verilerini eşzamanlı olarak analiz ederek sokak lambalarının parlaklık seviyesini (Kapalı, %50 veya %100) dinamik bir şekilde belirlemektedir. Tasarladığımız özelleştirilmiş ödül-ceza mekanizması sayesinde modelimiz sadece hareket sensörlerine körü körüne tepki veren basit bir yapı olmaktan çıkmış; gece karanlığında hareket algılandığında güvenliği maksimuma çıkaran, gündüz vakti veya sokak boşken ise sıfır israf prensibiyle hareket ederek enerji tüketimini minimize eden optimum aydınlatma politikasını başarıyla öğrenmiştir."

# Aksiyonlar (Action Space)

Akıllı aydınlatma sistemimizin "Aksiyon Uzayı" (Action Space), yapay zekanın çevresel durumlara göre her adımda seçebileceği üç temel komuttan oluşmaktadır. İlk seçenek olan 0 değeri (Kapalı / Off), lamba sistemini tamamen kapatır ve bu sayede sistemin enerji tüketimini sıfıra indirir. İkinci seçenek olan 1 değeri (%50 Parlaklık / Mid), lambayı yarı güçte çalıştırarak hem gereksiz enerji harcamasını önleyen hem de ortamı yeterince aydınlatan dengeli ve optimum bir çözüm sunar. Son seçenek olan 2 değeri (%100 Parlaklık / Max) ise lambayı tam güçte açarak ortamda maksimum güvenlik sağlar; ancak bu durum sistemin en yüksek enerjiyi tüketmesine neden olur. Yapay zeka, içinde bulunduğu saate ve hareketliliğe bakarak bu üç eylemden en uygun olanına karar verir.

<img width="523" height="252" alt="image" src="https://github.com/user-attachments/assets/f813dbb2-4a23-4ae3-b3ea-9a05772f32b0" />




# Ödül Sistemi (Reward Function)
Akıllı aydınlatma sistemimiz, her adımda aldığı kararın doğruluğunu üç temel kritere göre hesaplanan bir "ödül" puanıyla değerlendirir. İlk olarak, seçilen parlaklık seviyesine göre sisteme bir enerji cezası uygulanır; lamba kapalıysa ceza verilmezken, %50 parlaklıkta -1, tam güçte ise -2 puan düşülür. İkinci aşamada ortamdaki hareket ve mevcut ışık seviyesine bakılarak bir güvenlik veya tasarruf primi hesaplanır; örneğin, zifiri karanlıkta hareket varken lambayı kapalı tutmak sistem için kritik bir hata sayılarak -10 gibi büyük bir ceza getirirken, kimse yokken sistemi tamamen kapatmak +3 puanlık bir tasarruf ödülü kazandırır. Son olarak, sistem o anki zaman dilimine bakar ve eğer saat gece ise, ek gece bonusları devreye girer; gece hareket varken güvenliği sağlamak için lambayı tam güç açmak ek +3 puan, gece kimse yokken sistemi tamamen kapatmak ise ek +2 puan kazandırır. Yapay zeka, öğrenme sürecinde (Q-Tablosu güncellemelerinde) her adımın sonunda bu üç faktörün enerji cezası, güvenlik primi ve gece bonusu toplamını alarak, gelecekteki kararlarını maksimize etmeye çalışır.

Formül: Toplam Ödül = Enerji Cezası + Güvenlik Primi + Gece Bonusu

<img width="401" height="431" alt="image" src="https://github.com/user-attachments/assets/b7cb5f33-0af9-4184-b394-ef6768f79a05" />


# Eğitim Sonuçları

Yapay zekanın eğitim sürecine ait grafik ve simülasyon çıktıları, modelin ortamı mükemmel bir şekilde çözdüğünü ve hedeflenen davranışları başarıyla öğrendiğini göstermektedir. Öğrenme eğrisi incelendiğinde; modelin ilk 250 turda (keşif aşaması) rastgele kararlar alarak çevreyi tanımaya çalıştığı ve hatalarından eksi puanlar aldığı, ardından 750. tura kadar doğru hamleleri hızla kavrayarak performansını dik bir ivmeyle artırdığı görülmektedir. 750. turdan eğitim sonuna kadar ise ortalama ödülün 300 puan bandında sabitlenmesi, yapay zekanın "ustalık" aşamasına geçerek alabileceği en yüksek puanları getiren optimum stratejiyi ezberlediğini kanıtlar. 
Canlı testin 10. adımındaki sonuç da bu başarıyı somutlaştırmaktadır; sistem, ortamda bir insan hareketi algılamasına rağmen öğle vakti ve güneşli bir hava olduğu için ışıkları açmayı reddetmiş (Kapalı/OFF tutmuş) ve gereksiz enerji tüketiminin önüne geçerek tasarruf ödülü (+2 puan) kazanmıştır. Bu durum, modelin sadece sensör tetiklenmelerine körü körüne tepki vermediğini; zaman, ışık ve hareket verilerini aynı potada eriterek enerji verimliliğini ve güvenliği aynı anda sağlayan bilinçli bir akıllı şehir asistanına dönüştüğünü özetlemektedir.

<img width="623" height="157" alt="image" src="https://github.com/user-attachments/assets/a7f34f8d-7a07-4b84-82ba-f1cfb1e5ca94" />


<img width="862" height="472" alt="image" src="https://github.com/user-attachments/assets/6a853fb1-b094-4a67-bf52-d7f7d1d3befc" />





