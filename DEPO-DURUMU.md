# Depo Durumu — yokbi/the-algorithm

> **Kök `README.md`'ye dokunulmadı.** O dosya Twitter'ın resmî README'sidir.
> Bu dosya, **bu fork'un durumunu** anlatır.

**Denetim tarihi:** 2026-09-07 · **Varsayılan dal:** `main`

---

## 1. Tek cümleyle

Bu, Twitter'ın 2023'te açık kaynak yaptığı **öneri algoritmasının**
([`twitter/the-algorithm`](https://github.com/twitter/the-algorithm))
**değiştirilmemiş bir fork'udur.** İçinde size ait tek satır kod yoktur.

---

## 2. Ölçüm — "değiştirilmemiş" iddiasının kanıtı

```
$ git log --all --format='%an|%ae|%s' | grep -icE 'yokbi|ozkaya|claude'
0
```

Depodaki **hiçbir commit** size ait değil. Tüm commit'ler `twitter-team` ve
Twitter mühendislerine ait.

En son commit tarihi: **2023-04-04**. Yani upstream projenin kendisi de
üç yılı aşkın süredir güncellenmiyor — bu fork geride kalmış değil, **upstream
durmuş** durumda.

---

## 3. Depoda ne var

Twitter Ana Sayfa akışını (Home Timeline) üreten servis ve işlerin kaynak kodu.
Başlıca bileşenler:

| Tür | Bileşen | İşlevi |
|---|---|---|
| Özellik | `simclusters_v2` | Topluluk tespiti ve seyrek gömme (embedding) |
| | `trust_and_safety_models` | NSFW / kötüye kullanım tespiti modelleri |
| | `graph-feature-service` | İki kullanıcı arasındaki grafik özellikleri |
| Aday kaynağı | `src/java/com/twitter/search` (Earlybird) | Ağ-içi tweet arama ve sıralama (~%50 aday) |
| | `cr-mixer` | Ağ-dışı tweet adaylarını toplayan koordinasyon katmanı |
| | `follow-recommendations-service` | Takip önerileri |
| Sıralama | `timelines` (light ranker) | Earlybird için hafif sıralayıcı |
| Sunum | `home-mixer`, `product-mixer`, `visibilitylib` | Akışın kurgulanması ve görünürlük kuralları |
| Altyapı | `navi`, `twml`, `ann`, `recos-injector` | Model sunumu, ML kütüphanesi, yaklaşık komşu arama |

Dil dağılımı ağırlıklı olarak **Scala** ve **Java**, kısmen Python ve Rust.

---

## 4. Çalıştırma — dürüst cevap: pratikte çalıştırılamaz

**Bu depo için `run-*.sh` betiği eklenmedi.** Sebebi diğer depolardan farklı ve
önemli: bu kod **çalıştırılabilir bir uygulama değildir.**

Neden:

- **Bazel/Pants derleme yapılandırması eksik.** Depoda kök `WORKSPACE` veya
  `BUILD` dosyası yok — Twitter iç derleme sistemine bağımlıydı ve o
  yayınlanmadı.
- **İç bağımlılıklar yayınlanmadı.** Kod, Twitter'ın kapalı kaynak kütüphaneleri
  (Finagle iç sürümleri, Manhattan, Strato…) olmadan derlenmez.
- **Veri yok.** Algoritma, Twitter'ın canlı grafiği ve model ağırlıkları olmadan
  anlamlı bir çıktı üretmez; bunların hiçbiri depoda yok.
- **Ölçek.** Onlarca dağıtık servisin birlikte çalışmasını gerektirir.

Bu depo **okumak ve incelemek** için yayınlandı, çalıştırmak için değil.
Twitter'ın kendi duyurusu da bunu böyle konumlandırdı.

Yarın sabah Intel Mac'te bu depoyu "çalıştırmayı" denerseniz zaman kaybedersiniz —
başlatılacak bir şey yok. Okumak isterseniz kökteki `README.md` ve
`docs/system-diagram.png` doğru başlangıç noktasıdır.

---

## 5. Dal envanteri

| Dal | Durum |
|---|---|
| `main` | Varsayılan. Upstream'in dalı, değiştirilmemiş. |
| `claude/repo-audit-docs-e1dail` | Bu doküman turu |

**Size ait iş içeren başka dal yoktur.** Upstream'in de tek dalı var.

---

## 6. Bulgular

### 🟢 T1 — Boş fork
Fork alınmış, hiç çalışılmamış. Muhtemelen kaynak koda göz atmak için alındı.
→ `YAPILACAKLAR-DEPO.md` T1

### 🟢 T2 — Depo boyutu
Onlarca servisin kaynak kodu; klonlaması yavaş. İncelemek istiyorsanız
GitHub'ın web arayüzü veya `--depth 1` daha pratik. → T2

**Kod hatası, güvenlik açığı veya eksik iş bulgusu yoktur** — burada size ait kod
yok. Upstream'in kodunu denetlemek bu turun kapsamı dışındadır.

---

## 7. Yarınki test için

**Burada test edilecek bir şey yok** — ne kendi işiniz var, ne de kod
çalıştırılabilir durumda (§4). Vaktinizi kendi projelerinize ayırın.

---

Kalan işler: [`YAPILACAKLAR-DEPO.md`](YAPILACAKLAR-DEPO.md)
