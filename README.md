# Akıllı Şehir Aydınlatma Sistemi




# Aksiyonlar (Action Space)

Akıllı aydınlatma sistemimizin "Aksiyon Uzayı" (Action Space), yapay zekanın çevresel durumlara göre her adımda seçebileceği üç temel komuttan oluşmaktadır. İlk seçenek olan 0 değeri (Kapalı / Off), lamba sistemini tamamen kapatır ve bu sayede sistemin enerji tüketimini sıfıra indirir. İkinci seçenek olan 1 değeri (%50 Parlaklık / Mid), lambayı yarı güçte çalıştırarak hem gereksiz enerji harcamasını önleyen hem de ortamı yeterince aydınlatan dengeli ve optimum bir çözüm sunar. Son seçenek olan 2 değeri (%100 Parlaklık / Max) ise lambayı tam güçte açarak ortamda maksimum güvenlik sağlar; ancak bu durum sistemin en yüksek enerjiyi tüketmesine neden olur. Yapay zeka, içinde bulunduğu saate ve hareketliliğe bakarak bu üç eylemden en uygun olanına karar verir.

<img width="523" height="252" alt="image" src="https://github.com/user-attachments/assets/f813dbb2-4a23-4ae3-b3ea-9a05772f32b0" />




# Ödül Sistemi (Reward Function)
Akıllı aydınlatma sistemimiz, her adımda aldığı kararın doğruluğunu üç temel kritere göre hesaplanan bir "ödül" puanıyla değerlendirir. İlk olarak, seçilen parlaklık seviyesine göre sisteme bir enerji cezası uygulanır; lamba kapalıysa ceza verilmezken, %50 parlaklıkta -1, tam güçte ise -2 puan düşülür. İkinci aşamada ortamdaki hareket ve mevcut ışık seviyesine bakılarak bir güvenlik veya tasarruf primi hesaplanır; örneğin, zifiri karanlıkta hareket varken lambayı kapalı tutmak sistem için kritik bir hata sayılarak -10 gibi büyük bir ceza getirirken, kimse yokken sistemi tamamen kapatmak +3 puanlık bir tasarruf ödülü kazandırır. Son olarak, sistem o anki zaman dilimine bakar ve eğer saat gece ise, ek gece bonusları devreye girer; gece hareket varken güvenliği sağlamak için lambayı tam güç açmak ek +3 puan, gece kimse yokken sistemi tamamen kapatmak ise ek +2 puan kazandırır. Yapay zeka, öğrenme sürecinde (Q-Tablosu güncellemelerinde) her adımın sonunda bu üç faktörün enerji cezası, güvenlik primi ve gece bonusu toplamını alarak, gelecekteki kararlarını maksimize etmeye çalışır.

Formül: Toplam Ödül = Enerji Cezası + Güvenlik Primi + Gece Bonusu

<img width="401" height="431" alt="image" src="https://github.com/user-attachments/assets/b7cb5f33-0af9-4184-b394-ef6768f79a05" />



