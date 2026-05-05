# Akıllı Şehir Aydınlatma Sistemi





# Ödül Sistemi (Reward Function)
Akıllı aydınlatma sistemimiz, her adımda aldığı kararın doğruluğunu üç temel kritere göre hesaplanan bir "ödül" puanıyla değerlendirir. İlk olarak, seçilen parlaklık seviyesine göre sisteme bir enerji cezası uygulanır; lamba kapalıysa ceza verilmezken, %50 parlaklıkta -1, tam güçte ise -2 puan düşülür. İkinci aşamada ortamdaki hareket ve mevcut ışık seviyesine bakılarak bir güvenlik veya tasarruf primi hesaplanır; örneğin, zifiri karanlıkta hareket varken lambayı kapalı tutmak sistem için kritik bir hata sayılarak -10 gibi büyük bir ceza getirirken, kimse yokken sistemi tamamen kapatmak +3 puanlık bir tasarruf ödülü kazandırır. Son olarak, sistem o anki zaman dilimine bakar ve eğer saat gece ise, ek gece bonusları devreye girer; gece hareket varken güvenliği sağlamak için lambayı tam güç açmak ek +3 puan, gece kimse yokken sistemi tamamen kapatmak ise ek +2 puan kazandırır. Yapay zeka, öğrenme sürecinde (Q-Tablosu güncellemelerinde) her adımın sonunda bu üç faktörün enerji cezası, güvenlik primi ve gece bonusu toplamını alarak, gelecekteki kararlarını maksimize etmeye çalışır.

Formül: Toplam Ödül = Enerji Cezası + Güvenlik Primi + Gece Bonusu

<img width="401" height="431" alt="image" src="https://github.com/user-attachments/assets/b7cb5f33-0af9-4184-b394-ef6768f79a05" />



