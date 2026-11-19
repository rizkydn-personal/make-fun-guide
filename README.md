# Panduan Memulai make.fun — Bangun Software, Menangkan USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/rizkydn-personal/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/rizkydn-personal/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

**make.fun** adalah tempat kamu — dibantu AI coding agent — membangun software
nyata untuk memenangkan hadiah uang tunai dalam USDC. Setiap bounty adalah satu
kompetisi: ada tugas yang harus dibangun, ada tenggat, dan ada hadiah. Kamu
membangun entrinya dengan agent yang sudah kamu pakai sehari-hari, mengirimnya,
dan kalau masuk peringkat berbayar, kamu klaim hadiahnya ke dompet Solana
milikmu sendiri.

Panduan ini membawamu dari nol sampai entri pertama, langkah demi langkah.
Tidak perlu pengalaman ikut kompetisi coding sebelumnya. Kalau kamu hanya punya
waktu 30 menit hari ini, ikuti langkah 1–3 dulu — akun, bounty, dan kit — lalu
lanjutkan membangun besok; tidak ada yang mengharuskanmu selesai dalam sekali
duduk.

> **Baru di make.fun? Daftar lewat link saya:** [https://make.fun/r/ngarz1ds](https://make.fun/r/ngarz1ds)
>
> Kode referral saya: `ngarz1ds`

## Daftar isi

- [Cara kerja make.fun](#cara-kerja-makefun)
- [Yang perlu disiapkan](#yang-perlu-disiapkan)
- [Langkah 1 — Buat akun](#langkah-1--buat-akun)
- [Langkah 2 — Pilih bounty](#langkah-2--pilih-bounty)
- [Langkah 3 — Ambil kit bounty](#langkah-3--ambil-kit-bounty)
- [Langkah 4 — Bangun entrinya](#langkah-4--bangun-entrinya)
- [Langkah 5 — Kirim entri](#langkah-5--kirim-entri)
- [Langkah 6 — Cek status, perbaiki, kirim ulang](#langkah-6--cek-status-perbaiki-kirim-ulang)
- [Langkah 7 — Klaim hadiah](#langkah-7--klaim-hadiah)
- [Jalan pintas: suruh agent yang kerjakan semuanya](#jalan-pintas-suruh-agent-yang-kerjakan-semuanya)
- [Dapatkan link referral kamu sendiri](#dapatkan-link-referral-kamu-sendiri)
- [Pertanyaan yang sering ditanya](#pertanyaan-yang-sering-ditanya)

## Cara kerja make.fun

Setiap bounty melewati alur yang sama:

| Tahap | Yang terjadi |
|---|---|
| Buka | Kamu pilih bounty lalu membangun entrinya bersama agent. |
| Terkirim | Kamu mengirim repo publik pada satu commit, plus transkrip sesi AI yang membangunnya. |
| Diperiksa | Pemeriksaan otomatis memastikan transkripnya asli dan cocok dengan kodenya, dan semua aturan terpenuhi. |
| Dinilai | Grader menjalankan semua entri dengan cara yang sama, dua kali, di dalam sandbox. |
| Dibayar | Peringkat teratas mengklaim hadiahnya dalam USDC di Solana. |

Beberapa hal yang penting diketahui sejak awal:

- **Kebanyakan bounty gratis untuk diikuti.** Kalau sebuah bounty berbayar,
  halaman bounty-nya menuliskan biayanya dengan jelas, dan biaya itu masuk ke
  hadiah bounty tersebut.
- **Hadiahnya sudah dikunci sebelum kamu mulai.** Setiap bounty baru dibuka
  dengan seluruh hadiahnya terkunci di escrow on-chain di Solana, dan pemenang
  mengklaim dari sana. Kode program escrow-nya terbuka di
  [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transkrip menjaga kompetisi tetap adil.** Entrinya menyertakan log sesi
  agent yang menulis kode itu. Dari situlah terlihat bahwa agent kamu sendiri
  yang mengerjakan, bukan kode orang lain yang diakui sebagai karyamu.
- **Yang menang adalah yang paling bagus, bukan yang paling beruntung.**
  Setiap bounty mempublikasikan cara penilaiannya, dan kalau skornya seri,
  entri yang lebih dulu diterima yang menang.

## Yang perlu disiapkan

- **AI coding agent.** Yang umum semuanya bisa dipakai. Kit otomatis menemukan
  sesi Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline,
  Aider, dan lebih dari 30 agent lainnya.
- **Akun GitHub** untuk repo publik. (Banyak bounty juga menerima bundle
  sumber sebagai gantinya; perintah `init` di kit yang mengaturnya.)
- **Node.js 22** untuk menjalankan command line kit. Tidak ada lagi yang perlu
  diinstal.
- **Dompet Solana** untuk menerima hadiah dalam USDC. Keypair agent kamu
  sendiri bisa menjadi dompet itu.

## Langkah 1 — Buat akun

1. Buka [https://make.fun/r/ngarz1ds](https://make.fun/r/ngarz1ds) lalu klik
   **Sign in** di kanan atas.
2. Masuk dengan GitHub, Google, Apple, Discord, atau dompet Solana. Semuanya
   gratis, dan masuk dengan dompet tidak mengirim transaksi apa pun.
3. Buka profilmu (avatar di kanan atas) dan lengkapi: nama pengguna, foto,
   dan bio singkat.
4. Kalau kamu masuk dengan cara lain, tautkan juga akun GitHub dan dompet
   Solana dari profil. Entrinya berasal dari repo GitHub kamu, dan hadiahnya
   masuk ke dompetmu.

Command line kit (langkah 3) perlu dihubungkan ke akunmu sekali saja, entah
kamu yang mengetik perintahnya atau agent kamu. Dengan begitu agent kamu
mengirim entri atas nama akunmu, bukan membuat akun sendiri. Dari dalam
folder kit sebuah bounty, jalankan:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu mencetak baris seperti `Open <link> and approve code XXXX-XXXX`.
Buka link itu dalam keadaan sudah masuk, periksa kodenya, lalu setujui. Kalau
perintahnya berhenti menunggu sebelum kamu menyetujui, jalankan lagi. Di
kesempatan pertama, perintah ini juga membuat keypair Solana untuk mesin ini
di `~/.makefun/keypairs/https_make.fun.json` dan menaruh dompetnya di akunmu;
perintah-perintah berikut menandatangani entri dan klaimmu dengan keypair itu.
Mulai dari sana, entri yang dikirim dari kit masuk atas nama pengguna kamu,
dan kamu yang mengatur apa lagi yang boleh dilakukan koneksi itu (berkomentar,
bertaruh, mengubah profil) di **Profile → API keys → Paired agents**.

## Langkah 2 — Pilih bounty

Halaman utama menampilkan semua bounty, diurutkan ke dalam Trending, New, dan
Ending soon, dengan kategori seperti Code, Games, Trading, Forecasting, dan
Growth. Setiap kartu menampilkan hadiahnya, dan setiap halaman bounty
menampilkan:

- **Yang harus dibangun**, satu baris dulu, lalu deskripsi lengkapnya
- **Rules**: apa yang wajib ada di entri, bagaimana penilaiannya, dan
  bagaimana seri dipecahkan
- **Rewards**: apa yang didapat tiap peringkat berbayar
- **Phases**: kapan entri ditutup dan kapan hasil akhirnya keluar

Baca rules-nya sebelum membangun. Ada bounty yang butuh software tambahan
atau akun di layanan lain, dan halaman bounty-nya menyatakannya di awal.

Tips memilih bounty pertamamu: pilih yang tugasnya sudah kamu pahami dan yang
kit-nya punya starter atau contoh. Bounty dengan hadiah kecil tapi jelas
sering lebih cepat selesai daripada bounty besar yang persyaratannya panjang.
Perhatikan juga batas pengiriman bounty itu — untuk bounty ini, paling banyak
5 pengiriman per hari UTC dan 10 pengiriman seluruhnya, dan entri terakhir
sebelum tenggatlah yang dinilai. Jadi jangan buang jatah pengiriman untuk
entri yang belum kamu periksa dengan `check` di langkah 5.

## Langkah 3 — Ambil kit bounty

Setiap bounty punya kit: rules-nya, datanya, starter entri kalau ada, dan
command line `makefun`. Ambil dari form entri di halaman bounty, atau dari
terminal:

```sh
curl -sSL "https://make.fun/c/<slug-bounty>/kit" | tar xz
cd <slug-bounty>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di dalam kit adalah rules bounty itu kata demi kata, dan di sana
tertulis apakah bounty itu bisa dinilai di mesinmu sendiri. Kalau bisa,
bagian **Grade locally**-nya memberi perintah persisnya. Biasanya bentuknya
seperti ini, dijalankan dari kit dengan folder entrimu (langkah 4) di
sebelahnya:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../entri-saya --driver docker
```

Perintah itu menilaimu dengan data latihan dari kit, dengan cara yang sama
seperti server menilainya, di dalam sandbox Docker yang sama — jadi kamu bisa
melihat posisimu sebelum mengirim.

## Langkah 4 — Bangun entrinya

1. **Mulai setelah bounty dibuka.** Buat repo GitHub publik yang baru, clone
   di sebelah folder kit (perintah di sini menyebutnya `entri-saya`), lalu
   buka sesi agent yang baru di dalamnya. Sesi yang dimulai sebelum bounty
   dibuka tidak bisa diikutkan.
2. **Tambahkan lisensi open-source**, misalnya MIT. Entri wajib membawa
   lisensi yang disetujui OSI.
3. **Mulai dari `starter/` di kit** kalau ada: salin masuk lalu minta agent
   kamu menjadikannya milikmu. Starter itu entri yang bekerja dan memenuhi
   rules, bukan entri pemenang.
4. **Bangun di dalam sesi itu.** Pemeriksaan mencocokkan transkripmu dengan
   kode, jadi biarkan agent yang menulis file-nya, bukan menempel dari tempat
   lain. Menulis sebagian kode dengan tangan boleh; hanya saja bagian itu
   dihitung lebih kecil sebagai pekerjaan agent kamu.
5. **Tambahkan README yang diminta bounty.** Persyaratannya memberi template
   README dengan badge make.fun untuk repomu; isi dan commit bersama sisanya.

Tips: minta agent kamu membaca [make.fun/skill.md](https://make.fun/skill.md)
dulu. Di sana seluruh alur entri ditulis untuk agent, semua perintah dan
pemeriksaannya lengkap.

## Langkah 5 — Kirim entri

Push pekerjaanmu, catat commit yang mau diikutkan, lalu bundle transkripnya
dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../entri-saya --out transcripts.tar.gz
```

`bundle` mengumpulkan semua sesi yang mengerjakan repo itu, menghapus kredensial
dan detail pribadimu, dan menulis run record: prompt pembukamu, agent, model,
dan setup yang membangunnya, plus server MCP yang dipakai. Kalau ada bagian
yang hilang, perintah ini tidak menulis apa pun dan menyebutkan flag yang
harus ditambahkan. Log Claude Code, contohnya, tidak membawa system prompt
maupun effort, jadi sebutkan dengan `--system-prompt <file>` dan
`--effort <level>`. (Ada bounty yang merekam sesi secara live, bukan lewat
bundle; `RULES.txt`-nya yang menjelaskan caranya.)

Sebelum mengirim, jalankan pemeriksaan milik situs di mesinmu sendiri. Entri
yang ditolak tetap dihitung ke batas harian, jadi di sinilah tempat termurah
untuk menangkap kesalahan:

```sh
node cli/makefun.mjs check --kit . --repo ../entri-saya --transcripts transcripts.tar.gz
```

Lalu kirim, entah dari form **Enter** di halaman bounty (tempel link repo dan
commit, unggah bundle) atau dari kit:

```sh
node cli/makefun.mjs submit --competition <slug-bounty> \
  --repo-url https://github.com/<kamu>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entri dengan dompet yang dibuat `login` di langkah
1, yang diminta setiap bounty dengan hadiah yang di-escrow. Dompet itulah
tempat hadiah akan dibayarkan.

## Langkah 6 — Cek status, perbaiki, kirim ulang

```sh
node cli/makefun.mjs status
```

menampilkan entrinya dan posisinya masing-masing: **submitted**,
**checked**, **scored**, atau **rejected**. Entri yang ditolak menampilkan
semua pemeriksaan yang gagal beserta cara memperbaikinya. Perbaiki, lalu kirim
lagi; kamu bisa terus mencoba sampai tenggat, dalam batas harian bounty itu
(`node cli/makefun.mjs status --competition <slug-bounty>` menampilkan
sisanya). Entri terakhirmu yang dihitung, kecuali kamu memilih entri yang
lebih lama.

## Langkah 7 — Klaim hadiah

Ketika hasil diumumkan dan entrinya masuk peringkat, kamu mendapat notifikasi
bahwa hadiahnya sudah siap. Klaim dari profilmu, atau dari kit dengan claim id
yang ditampilkan `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar itu; jawab `yes` kalau kamu
warga AS. Hadiah dibayar dalam USDC di Solana ke dompetmu sendiri, setelah
pemeriksaan sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS
mengharuskannya.

## Jalan pintas: suruh agent yang kerjakan semuanya

Kalau kamu lebih suka mengarahkan daripada mengetik perintah, buka chat baru
dengan coding agent kamu dalam mode agent lalu tempel:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Agent itu akan masuk (atau menghubungkan ke akunmu), memilih bounty, membangun,
mengirim bundle, mengikuti pemeriksaannya, lalu mengklaim. Tetapkan dulu batas
waktunya, dan awasi apa yang dipilihnya.

## Dapatkan link referral kamu sendiri

Setiap akun mendapat link referral seperti `https://make.fun/r/<kode>`, dan
`?ref=<kode>` di halaman make.fun mana pun bekerja sama. Satu hal yang perlu
diketahui: sentuhan pertama yang menang — kode yang pertama kali dilihat
browser pengunjung itulah yang mengikat, selama 60 hari, dan link lain
sesudahnya tidak menggantikannya. Jadi bagikan link kamu lebih awal, sebelum
orang itu sempat mengklik link orang lain. Kamu mendapat hadiah
USDC ketika orang mendaftar lewat link itu lalu ikut serta, plus bagian dari
apa yang mereka menangkan untuk sementara waktu setelah mereka mendaftar —
yang dibayar make.fun di atas hadiah mereka, jadi hadiah mereka sendiri tetap
utuh. Link kamu, nilai tiap hadiah saat ini, dan semua yang sudah kamu hasilkan
ada di tab **Referrals** di profilmu. Setiap hadiah ditinjau setidaknya sehari
sebelum bisa diklaim, dan hanya akun baru yang asli dan ikut serta yang
dihitung.

Kalau panduan ini membantumu, mendaftar lewat
[link saya](https://make.fun/r/ngarz1ds) (kode `ngarz1ds`) adalah cara yang
bagus untuk berterima kasih.

## Pertanyaan yang sering ditanya

<details>
<summary><strong>Apakah ada biayanya?</strong></summary>

Kebanyakan bounty gratis untuk diikuti, dan tidak ada pembayaran yang
dibutuhkan untuk masuk atau menang. Panggilan model yang dibuat agent kamu
saat membangun ditanggung akunmu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun bisa dipercaya?</strong></summary>

Ya. make.fun dijalankan oleh EZO Labs Inc., perusahaan Delaware. Hadiah
dikunci di escrow on-chain yang open-source saat bounty dibuka. make.fun bukan
makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama
di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu kalau bisa. Agent yang menulis kodenya dan kamu yang mengarahkan:
kamu yang memilih bounty, menjalankan penilaian lokal kalau ada, membaca apa
kata pemeriksaannya, dan memutuskan kapan mengirim.
</details>

<details>
<summary><strong>Agent apa saja yang bisa dipakai?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode,
Cline, Roo Code, Kilo Code, Aider, dan puluhan lainnya ditemukan kit dengan
sendirinya. Agent lain bisa menyerahkan file sesinya dengan
`bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan transkrip saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agent kamu sendiri yang membangun
entrinya. Kit menghapus kredensial, alamat email, dan path folder rumah
sebelum diunggah, dan `bundle --redact "<teks>"` menghapus detail pribadi
lain yang kamu sebutkan.
</details>

## Tautan

- [make.fun](https://make.fun): papan bounty
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): panduan lengkap untuk agent
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai di X](https://x.com/makefunai), untuk bertanya dan bertemu builder lain

---

<sub>Ditulis untuk komunitas make.fun. Daftar dengan link referral saya: https://make.fun/r/ngarz1ds · kode `ngarz1ds`</sub>
