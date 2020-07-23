---
layout: post
published: true
title: LAOSARENA-2020
date: '2020-06-04'
image: /img/LaosArenaPenyisihan/Friendship.jpg
---
Another CTF writeup. Thanks to my team @PenghuniPapanBawah for finishing @ **#6**.

## WEB-uns0lveable[60pts]

Diberikan sebuah alamat web http://chall4.182410102083.repl.run/ dengan tampilan seperti berikut:

![1](/img/LaosArenaPenyisihan/uns0lveable.png)



Web  tersebut  meminta  sebuah inputan nilai  antara  1~1500  dengan  kesempatan  10  kali kemudian   akan   dibandingkan   dengan   nilai   random untuk mendapatkan   flag. 

Jika diperhatikan dengan baik, webitu menggunakan repl.it sehingga pada bagian url bisa kita tambahkan /__repl menjadi: 
http://chall4.182410102083.repl.run/__repl

selanjutnya kita akan diredirect ke halaman https://repl.it/@182410102083/chall4 dan bisa melihat sourcode program

![2](/img/LaosArenaPenyisihan/uns0lveable2.png)
FLAG : `LAOS_ARENA{fr33_s3rv1c3_4r3_n0t_s4f3}`



## WEB -flippity floppity[54 pts]

Diberikan  sebuah  alamat  web http://chall1.reach.my.id/ jika  kita  buka  menampilkan deretan string terbalik(reverse).

![3](/img/LaosArenaPenyisihan/reverse1.png)



Copy semua string yang ditampilkan kemudian reverse menggunakan text reverse online Agar bisa kita baca dengan mudah

![4](/img/LaosArenaPenyisihan/reverse2.png)


Pada bagian yang bercetak biru mengartikan bahwa untuk mendapatkan flag yang diencode base64 harus melakukan request dengan 
```
user agent: LAOS_ARENA_USER
referer: https://laos.ilkom.unej.ac.id
```
Maka  tinggal  kita  buka  inspector kemudian  menuju  ke  bagian  network  untuk mengedit request.

![5](/img/LaosArenaPenyisihan/reverse3.png)



Setelah kita ubah request kita kirimkan kembali dan kita bisa melihat response yang diberikan berupa base64 yang harus kita decode dulu untuk mendapat flag.

![6](/img/LaosArenaPenyisihan/reverse4.png)



Pergi ke web base64decoder dan didapat hasil flagnya.

![7](/img/LaosArenaPenyisihan/reverse5.png)
FLAG : `LAOS_ARENA{pUy3ng_m4s?}`



## FORENSIK-ez document forensix[50 pts]

Diberikan sebuah fileextensi .odt yang mana bisa kita langsung buka. Setelah dicek satu persatu filenya diperoleh flag pada content.xml

![8](/img/LaosArenaPenyisihan/ez_doc.png)
FLAG: `LAOS_ARENA{n0_d0c5_4r3_s4f3`



## KRIPTOGRAFI – Menu Buka Puasa[76 pts]

Diberikan  sebuah  pesan  yang  telah  dienkripsi,  yang harus  dilakukan  adalah mendekripsi  pesan  tersebut  agar  dapat  dibaca. Kami mencoba  untuk  melakukansubtitution crackpada  web  cryptoclub.org dan  pesan  dapat  terbaca  bersama flagnya.

![9](/img/LaosArenaPenyisihan/menu buka puasa.png)
FLAG: `LAOS_ARENA{SUBTITUTION_BASIC}`



## KRIPTOGRAFI - Ciphernya Hog Rider[56 pts]

Diberikan  sebuah  file  gambar  yang  berisi  sebuah  cipher,  karena  judulnya  hog  a.k.a nunggang babi maka ini berarti merupakan pigpen cipher. Gunakan tool decoder online untuk menerjemahkannyadan dapatkan flagnya.

![10](/img/LaosArenaPenyisihan/HOG_RIDER.png)
FLAG : `LAOS_ARENA{PPENCIPHR}`



## STEGANOGRAFY -Cloak and Dagger[50 pts]

Diberikan sebuah  file  gambar  png  yang  jika  kita buka langsung  tidak  nampak apapun. Kami  mencoba  menggunakan  tools  stegsolve  online  dan  menghilangkan transparancynya sehingga nampak flagnya.

![11](/img/LaosArenaPenyisihan/cloak dagger.png)
FLAG: `LAOS_ARENA{ALPH4_BIKIN_KAMU_H1LANG}`



## STEGANOGRAFI - stega-intro-graphy[50 pts]

Diberikan  file  laos-arena.zip  kemudiansetelah  di  unzip  muncul  file  gambar  dan  file flag3.zip.  Kitalakukan  unzip untuk  file  flag3.zip  dan  muncul  file  flag2.zip  hingga  pada akhirnya muncul gambar flag.png

![12](/img/LaosArenaPenyisihan/stegano-graphy.png)



Lakukan perintah strings diikuti perintah grep LAOS untuk menemukan flag. Dan berhasil :v

FLAG : `LAOS_ARENA{3a5y_p34zy_l3m0n_squu33z3}`



## REVERSE - PHP Geek[81 pts]

Diberikan file berektensi txt, setelah dibuka muncul deretanangka decimal. Tinggal kita ubah menggunakan perintah chr() pada python dan muncul flagnya.


![13](/img/LaosArenaPenyisihan/php_geek.png)
FLAG: `LAOS_ARENA{y0u_4r3_PHP_g33ks}`

Great!
