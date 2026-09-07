# Yapılacaklar — yokbi/the-algorithm

## Kod işi: **YOK**

Bu, `twitter/the-algorithm` projesinin değiştirilmemiş bir fork'udur. Size ait
tek satır kod olmadığı için düzeltilecek hata, yazılacak test veya kapatılacak
açık da yoktur.

Ayrıca bu kod **derlenemez ve çalıştırılamaz** — Twitter'ın iç derleme sistemi
ve kapalı kaynak bağımlılıkları yayınlanmadı (bkz. `DEPO-DURUMU.md` §4).
Yani "çalışır hâle getirme" diye bir yapılacak madde de yazılamaz; bu, eksik bir
iş değil, upstream'in bilinçli yayın kapsamıdır.

---

## T1 🟢 Fork'un ne işe yaradığına karar verin

**Sorun:** Fork alınmış, üzerine hiç çalışılmamış. Depo listenizde kendi
projelerinizin arasında duruyor ve "bu benim projem mi?" sorusunu doğuruyor.

**Seçenek A — Silin (önerilen).**
Kaybolacak hiçbir şey yok — kendi commit'iniz yok, üstelik upstream depo
GitHub'da hâlâ duruyor. İncelemek istediğinizde oradan okuyabilirsiniz.

> GitHub → depo → **Settings** → *Danger Zone* → **Delete this repository**

**Seçenek B — Bırakın.** Zararı yok. Bu turda eklenen `DEPO-DURUMU.md`
sayesinde deponun ne olduğu artık ilk bakışta anlaşılıyor — asıl sorun
(belirsizlik) çözülmüş oluyor.

**Seçenek C — İnceleme notları için kullanın.** Algoritmayı okuyup öğrenmek
istiyorsanız fork'u tutup kendi notlarınızı bir `NOTLAR.md` dosyasında biriktirmek
anlamlı bir kullanım olur. O zaman fork "boş" olmaktan çıkar.

---

## T2 🟢 Depoyu incelemenin pratik yolu

**Sorun:** Depo onlarca servisin kaynağını içeriyor; tam klonlama yavaş.

**Öneriler:**

```bash
# Sığ klon — geçmiş çekilmez, çok daha hızlı
git clone --depth 1 https://github.com/yokbi/the-algorithm
```

Ya da hiç klonlamadan GitHub'ın kod arama arayüzünü kullanın.

**Nereden başlamalı:**

1. `README.md` — bileşen tablosu ve genel akış
2. `docs/system-diagram.png` — servislerin birbirine nasıl bağlandığı
3. `home-mixer/` — akışın kurgulandığı yer; okumaya buradan başlamak en verimli
4. `src/scala/com/twitter/simclusters_v2/README.md` — öneri sinyallerinin temeli

---

## Not: upstream kodu denetlenmedi

Bu denetim **sizin işinizi** kapsıyor. Twitter'ın kendi kaynak kodundaki olası
hatalar veya açıklar incelenmedi — o kod 2023'ten beri güncellenmiyor ve zaten
çalıştırılamaz durumda.
