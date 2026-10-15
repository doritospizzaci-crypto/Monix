# Monixs — Yeni Nesil Sosyal Ağ

Monixs; Instagram, Discord ve oyunlaştırılmış sosyal ağların güçlü yanlarını bir araya getiren, özgün özelliklere sahip modern bir sosyal platformdur.

## Aşama 1 — Temel Altyapı (Tamamlandı)

Bu sürüm şunları içerir:

- React + TypeScript + Vite proje iskeleti
- Tailwind CSS 4 tasarım sistemi (mor / cyan vurgular, koyu-açık tema)
- Supabase Auth ile e-posta kayıt / giriş
- Profil sistemi (kullanıcı adı, görünen ad, biyografi, gizlilik)
- Responsive layout (mobil alt navigasyon + masaüstü yan menü)
- Row Level Security (RLS) politikaları
- Onboarding ekranı

**Henüz tamamlanmamış (sonraki aşamalar):**
- Gönderi / fotoğraf yükleme (Aşama 2)
- Gerçek zamanlı mesajlaşma (Aşama 3)
- Topluluklar & bildirimler (Aşama 4)
- Canlı Dünya, günlük görevler, mini oyunlar (Aşama 5)
- Sesli / görüntülü görüşme (Aşama 6)

## Kurulum

### 1. Bağımlılıklar

```bash
npm install
```

### 2. Supabase Projesi

1. [supabase.com](https://supabase.com) üzerinden ücretsiz hesap aç.
2. Yeni proje oluştur.
3. Project Settings → API bölümünden:
   - `Project URL`
   - `anon public` key
   değerlerini kopyala.
4. `.env.example` dosyasını `.env` olarak kopyala ve değerleri yapıştır:

```bash
cp .env.example .env
```

```
VITE_SUPABASE_URL=https://xxxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOi...
```

### 3. Veritabanı Şeması

Supabase Dashboard → SQL Editor'e git ve `supabase/migrations/001_initial_schema.sql` içeriğini çalıştır.

Bu script:
- `profiles`, `user_settings`, `follows` tablolarını oluşturur
- RLS politikalarını aktif eder
- Yeni kullanıcı kaydında otomatik profil oluşturan trigger ekler

### 4. Çalıştır

```bash
npm run dev
```

Tarayıcıda `http://localhost:5173` adresini aç.

## Ücretsiz Supabase Limitleri (dürüst bilgi)

- 500 MB veritabanı
- 1 GB dosya depolama
- 2 GB bant genişliği / ay
- 50.000 aylık aktif kullanıcı (Auth)
- Realtime bağlantı limiti var

Bu limitler kişisel / erken aşama için yeterlidir. Büyüdükçe ücretli plana geçmen gerekir. Service Role Key'i **asla** frontend koduna koyma.

## Güvenlik Notları

- Tüm hassas işlemler RLS ile korunuyor.
- Kullanıcı sadece kendi profilini güncelleyebilir.
- Anon key istemci tarafında güvenlidir çünkü RLS kuralları veriyi korur.
- E-posta doğrulama Supabase ayarlarından açılabilir (Authentication → Providers → Email).

## Dosya Yapısı

```
src/
  components/     # Layout, LoadingScreen, AuthLayout
  contexts/       # AuthContext
  lib/            # supabase client
  pages/          # Login, Register, Home, Profile, Settings, Onboarding
  types/          # Database types
supabase/
  migrations/     # SQL migration dosyaları
```

## Sonraki Adım

Aşama 2: Gönderi sistemi, fotoğraf yükleme (Supabase Storage), takip, beğeni ve yorum.

Bismillah, beraber güzel bir şey çıkarıyoruz.
