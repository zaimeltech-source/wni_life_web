# wni_life_web

Situs statis WNI Life (kebijakan privasi + `app-ads.txt`) yang dipublikasikan lewat GitHub Pages:
<https://zaimeltech-source.github.io/wni_life_web/>

Deploy otomatis oleh `.github/workflows/static.yml` setiap push ke `main` (seluruh isi repo diunggah
sebagai artifact, jadi file baru di root langsung ikut terbit).

## app-ads.txt (verifikasi AdMob)

Isi `app-ads.txt`:

```
google.com, pub-1627966208675321, DIRECT, f08c47fec0942fa0
```

**Penting:** AdMob hanya mencari `app-ads.txt` di **root domain** dari "Developer website" yang tertulis
di listing Play Store — bukan di sub-path. Untuk project page GitHub Pages, host-nya
`zaimeltech-source.github.io`, sehingga file di repo ini terbit di
`https://zaimeltech-source.github.io/wni_life_web/app-ads.txt` dan **tidak** akan ditemukan crawler.

Supaya terverifikasi, salah satu dari ini harus dilakukan:

1. **User site GitHub Pages** — buat repo `zaimeltech-source.github.io`, isi `app-ads.txt` yang sama di
   root-nya (boleh sekalian redirect/isi halaman privasi), lalu pasang
   `https://zaimeltech-source.github.io/` sebagai Developer website di Play Console.
2. **Domain sendiri** — pasang `CNAME` (mis. `wnilife.zaimeltech.com`) di repo ini lewat
   Settings → Pages → Custom domain, arahkan DNS ke GitHub Pages, lalu taruh `app-ads.txt` di root
   domain tersebut. Developer website di Play Console memakai domain itu.

Setelah itu cek <https://<domain>/app-ads.txt> harus menampilkan satu baris di atas, lalu tunggu crawl
AdMob (bisa sampai 24 jam) dan lihat status di AdMob → Apps → app-ads.txt.
