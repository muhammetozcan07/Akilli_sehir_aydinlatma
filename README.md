# Akıllı Şehir Aydınlatma Sistemi

Pekiştirmeli Öğrenme (Q-Learning) algoritmaları kullanılarak eğitilen bu sistem; günün saatini, doğal ışık seviyesini ve sensörlerden gelen anlık hareket verilerini eşzamanlı olarak analiz ederek sokak lambalarının parlaklık seviyesini (Kapalı, %50 veya %100) dinamik bir şekilde belirlemektedir. Tasarladığımız özelleştirilmiş ödül-ceza mekanizması sayesinde modelimiz sadece hareket sensörlerine körü körüne tepki veren basit bir yapı olmaktan çıkmış; gece karanlığında hareket algılandığında güvenliği maksimuma çıkaran, gündüz vakti veya sokak boşken ise sıfır israf prensibiyle hareket ederek enerji tüketimini minimize eden optimum aydınlatma politikasını başarıyla öğrenmiştir.

# Aksiyonlar (Action Space)

Akıllı aydınlatma sistemimizin "Aksiyon Uzayı" (Action Space), yapay zekanın çevresel durumlara göre her adımda seçebileceği üç temel komuttan oluşmaktadır. İlk seçenek olan 0 değeri (Kapalı / Off), lamba sistemini tamamen kapatır ve bu sayede sistemin enerji tüketimini sıfıra indirir. İkinci seçenek olan 1 değeri (%50 Parlaklık / Mid), lambayı yarı güçte çalıştırarak hem gereksiz enerji harcamasını önleyen hem de ortamı yeterince aydınlatan dengeli ve optimum bir çözüm sunar. Son seçenek olan 2 değeri (%100 Parlaklık / Max) ise lambayı tam güçte açarak ortamda maksimum güvenlik sağlar; ancak bu durum sistemin en yüksek enerjiyi tüketmesine neden olur. Yapay zeka, içinde bulunduğu saate ve hareketliliğe bakarak bu üç eylemden en uygun olanına karar verir.

<img width="523" height="252" alt="image" src="https://github.com/user-attachments/assets/f813dbb2-4a23-4ae3-b3ea-9a05772f32b0" />




# Ödül Sistemi (Reward Function)
Akıllı aydınlatma sistemimiz, her adımda aldığı kararın doğruluğunu üç temel kritere göre hesaplanan bir "ödül" puanıyla değerlendirir. İlk olarak, seçilen parlaklık seviyesine göre sisteme bir enerji cezası uygulanır; lamba kapalıysa ceza verilmezken, %50 parlaklıkta -1, tam güçte ise -2 puan düşülür. İkinci aşamada ortamdaki hareket ve mevcut ışık seviyesine bakılarak bir güvenlik veya tasarruf primi hesaplanır; örneğin, zifiri karanlıkta hareket varken lambayı kapalı tutmak sistem için kritik bir hata sayılarak -10 gibi büyük bir ceza getirirken, kimse yokken sistemi tamamen kapatmak +3 puanlık bir tasarruf ödülü kazandırır. Son olarak, sistem o anki zaman dilimine bakar ve eğer saat gece ise, ek gece bonusları devreye girer; gece hareket varken güvenliği sağlamak için lambayı tam güç açmak ek +3 puan, gece kimse yokken sistemi tamamen kapatmak ise ek +2 puan kazandırır. Yapay zeka, öğrenme sürecinde (Q-Tablosu güncellemelerinde) her adımın sonunda bu üç faktörün enerji cezası, güvenlik primi ve gece bonusu toplamını alarak, gelecekteki kararlarını maksimize etmeye çalışır.

Formül: Toplam Ödül = Enerji Cezası + Güvenlik Primi + Gece Bonusu

<img width="401" height="431" alt="image" src="https://github.com/user-attachments/assets/b7cb5f33-0af9-4184-b394-ef6768f79a05" />


# Matematiksel Gösterim

Sistemin öğrenme mekanizması, Pekiştirmeli Öğrenmenin temel taşı olan Bellman Denklemi kullanılarak modellenmiştir. Yapay zekanın her deneyimden sonra (Q-tablosunu) güncellemek için kullandığı matematiksel formül şu şekildedir:

<img width="582" height="72" alt="image" src="https://github.com/user-attachments/assets/b11eac2a-1b1e-474b-8f41-9d3856895bff" />

# Eğitim Sonuçları

Yapay zekanın eğitim sürecine ait grafik ve simülasyon çıktıları, modelin ortamı mükemmel bir şekilde çözdüğünü ve hedeflenen davranışları başarıyla öğrendiğini göstermektedir. Öğrenme eğrisi incelendiğinde; modelin ilk 250 turda (keşif aşaması) rastgele kararlar alarak çevreyi tanımaya çalıştığı ve hatalarından eksi puanlar aldığı, ardından 750. tura kadar doğru hamleleri hızla kavrayarak performansını dik bir ivmeyle artırdığı görülmektedir. 750. turdan eğitim sonuna kadar ise ortalama ödülün 300 puan bandında sabitlenmesi, yapay zekanın "ustalık" aşamasına geçerek alabileceği en yüksek puanları getiren optimum stratejiyi ezberlediğini kanıtlar. 

Canlı testin 10. adımındaki sonuç da bu başarıyı somutlaştırmaktadır. Sistem; Akşam vakti, Hafif Aydınlık bir ortamda hareket algılamasına rağmen, gereksiz enerji sarfiyatından kaçınarak lambayı tam kapasite yerine %50 güç (MID) seviyesinde çalıştırmayı tercih etmiştir ve ödülü (+2 puan) kazanmıştır.

<img width="625" height="147" alt="image" src="https://github.com/user-attachments/assets/1add7b24-2e2f-4ce9-9fd9-0037a89d1097" />




<img width="862" height="472" alt="image" src="https://github.com/user-attachments/assets/2bc2cd6a-2265-4bce-a4e2-03df3abd32c3" />


# Çalışma Videosu

https://github.com/user-attachments/assets/7de30c39-95a5-4eb1-84da-510e42c983fb





