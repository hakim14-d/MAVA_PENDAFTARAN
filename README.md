# MAVA Pendaftaran

Sistem pendaftaran pasukan bola tampar dalam talian untuk **mana-mana kejohanan**: borang pasukan (Borang O-2), gambar pasport, tarikh tutup dan denda lewat, papan pemuka urus setia dan PDF. Satu sistem untuk banyak kejohanan.

**Laman:** https://hakim14-d.github.io/MAVA_PENDAFTARAN/

## Siapa guna apa

| Peranan | Log masuk | Tugas |
|---|---|---|
| **Super Admin** | Pilih *Super Admin* + PIN | Cipta & padam kejohanan, urus semua PIN (urus setia & pasukan) bagi semua kejohanan |
| **Urus Setia** | Pilih kejohanan → *Urus Setia Kejohanan* + PIN | Urus satu kejohanan: tetapan, terbit & kongsi, PIN pasukan, semak borang, denda, PDF |
| **Pengurus Pasukan** | Pilih kejohanan → nama pasukan + PIN | Isi borang pasukan, muat naik gambar, hantar, muat turun PDF |

## Aliran kerja

1. **Super Admin** cipta kejohanan dan berikan PIN kepada urus setia.
2. **Urus Setia** lengkapkan tetapan (tarikh, tempat, tarikh & masa tutup, denda lewat), jana PIN pasukan di *Urus PIN*, kemudian **Terbitkan**.
3. Kongsi pautan kejohanan (`…/#e-<id>`) bersama PIN setiap pasukan; mesej sedia untuk WhatsApp disediakan.
4. **Pengurus Pasukan** isi dan hantar borang. Borang yang dihantar dikunci; urus setia boleh membuka semula.
5. Selepas tarikh tutup: terima pendaftaran lewat dengan **peringatan denda**, atau tutup pendaftaran (ikut tetapan).

## Ciri

- Banyak kejohanan serentak; status Draf → Diterbitkan → Ditutup
- Tarikh & masa tutup (waktu Malaysia), kiraan hari dan jam masa nyata
- Denda lewat: amaun, arahan bayaran, status dibayar / belum dibayar
- Borang pasukan Lelaki & Perempuan: hingga 20 pemain, posisi, kapten (C), libero (L), 6 pegawai, warna 2 uniform
- Semakan automatik: No. KP, tarikh lahir daripada No. KP, kelayakan umur, nombor baju & No. KP berulang
- Gambar saiz pasport 35 × 45 mm (dipotong automatik)
- PDF: borang pasukan + lampiran gambar, semua borang dalam satu fail, senarai induk
- Bendera negeri, mod cerah & gelap, sesuai untuk telefon

## Teknikal

- Satu fail `index.html` di GitHub Pages; data dalam **Supabase** (jadual berawalan `kj_`)
- Semua akses melalui fungsi pangkalan data yang menyemak PIN; PIN disimpan sebagai hash bcrypt
- Had 8 cubaan PIN salah setiap 15 minit
- Kunci Supabase dalam `index.html` ialah kunci awam (anon); tiada PIN disimpan dalam repo ini

© 2026 ZAINDRA
