---
layout: post
published: true
title: LAOSARENA-2020
date: '2020-06-04'
image: /img/LaosArenaPenyisihan/l.png
---
Another CTF writeup. Thanks to my team @PenghuniPapanBawah for finishing @ **#6**.

## WEB-uns0lveable[60pts]

Diberikan sebuah alamat web http://chall4.182410102083.repl.run/dengan tampilan seperti berikut:
![1](/img/LaosArenaPenyisihan/uns0lveable.png)



Web  tersebut  meminta  sebuah inputan nilai  antara  1~1500  dengan  kesempatan  10  kali kemudian   akan   dibandingkan   dengan   nilai   random untuk mendapatkan   flag. 

Jika diperhatikan dengan baik, webitu menggunakan repl.it sehingga pada bagian url bisa kita tambahkan /__repl menjadi :http://chall4.182410102083.repl.run/__repl

selanjutnya kita akan diredirect ke halaman https://repl.it/@182410102083/chall4dan bisa melihat sourcode program
![2](/img/LaosArenaPenyisihan/uns0lveable2.png)

FLAG : LAOS_ARENA{fr33_s3rv1c3_4r3_n0t_s4f3}



## WEB -flippity floppity[54 pts]

Diberikan  sebuah  alamat  web http://chall1.reach.my.id/jika  kita  buka  menampilkan deretan string terbalik(reverse).
![3](/img/LaosArenaPenyisihan/reverse1.png)


Copy semua string yang ditampilkan kemudian reverse menggunakan text reverse online Agar bisa kita baca dengan mudah
![4](/img/LaosArenaPenyisihan/reverse2.png)

```bash
Pada bagian yang bercetak biru mengartikan bahwa untuk mendapatkan flag yang diencode base64 harus melakukan request dengan 
user agent: LAOS_ARENA_USER
referer: https://laos.ilkom.unej.ac.id
Maka  tinggal  kita  buka  inspector kemudia  menuju  ke  bagian  network  untuk mengedit request.
```
![5](/img/LaosArenaPenyisihan/reverse3.png)



Setelah kita ubah request kita kirimkan kembali dan kita bisa melihat response yang diberikan berupa base64 yang harus kita decode dulu untuk mendpat flag.
![6](/img/LaosArenaPenyisihan/reverse4.png)



Pergi ke web base64decoderdan didapat hasil flagnya.
![7](/img/LaosArenaPenyisihan/reverse5.png)



FLAG : LAOS_ARENA{pUy3ng_m4s?}




```
Identity:email:jarred.a.mclovin@gmail.com
Identity:email:alexthroe376@gmail.com
```

These were the emails available and grepping to one of the email lead us to this mail.

```bash
To: jarred.a.mclovin@gmail.com
Content-Type: multipart/mixed; boundary="000000000000e6890d05a2e08d6f"
--000000000000e6890d05a2e08d6f
Content-Type: multipart/alternative; boundary="000000000000e6890c05a2e08d6d"
--000000000000e6890c05a2e08d6d
Content-Type: text/plain; charset="UTF-8"
Hi Jarred Mclovin,
We are glad you chose us for your CTF Flag needs, and hope you are happy
with our product!
Password: @uVmG4NMus
Sincerely,
ALEX THROE
alex@throe.com <axel@throe.com>
SGALF LLC
DO NO REPLY TO THIS EMAIL
--000000000000e6890c05a2e08d6d
Content-Type: text/html; charset="UTF-8"
Content-Transfer-Encoding: quoted-printable
<div dir=3D"ltr">Hi Jarred Mclovin,<br><br>We are glad you chose us for you=
r CTF Flag needs, and hope you are happy with our product!<div><br></div><d=
iv>Password:=C2=A0@uVmG4NMus<br><br>Sincerely,<br><br>ALEX THROE<br><a href=
=3D"mailto:axel@throe.com" target=3D"_blank">alex@throe.com</a><br>SGALF LL=
C<br><br><br>DO NO REPLY TO THIS EMAIL</div></div>
--000000000000e6890c05a2e08d6d--
--000000000000e6890d05a2e08d6f
Content-Type: application/zip; name="Mclovin.zip"
Content-Disposition: attachment; filename="Mclovin.zip"
Content-Transfer-Encoding: base64
Content-ID: <f_k8t5fbn30>
X-Attachment-Id: f_k8t5fbn30
UEsDBBQACQAIAPSGiFCgeQ8xU4MAAI2bAAARABwATG92aW5JbnZvaWNlLmRvY3hVVAkAA0w6jl63
Q45edXgLAAEE6AMAAAToAwAA5ISKblxOQNsWBnvQmA/Sqm8ph/3ekS3ylL5L55N9fT7tp8yoQrej
ejTqIJNLZernsfzuR4zpwwAWu3SDYKekpG93xkZb6zxPnGY5i/hw7glA0qVL1S2X8lpk6GNy/QqH
aOMd55xJ6mO1uqzD9wN71uilXeKWR8FVJiUDeN1XmsC0N2Hvh/hhWfqq97GLM0+j6ty2I4VmQVIQ
A3F5h4HS/Kp+epagEDHYjIJYqYY8nMM88TgjgapfOkJsdKW6oKuhS1FRrdjrZiwh8yb1zvFiYWUS
eaZ2JHp7/qYMVgigBbdNfd4AvIzKZecxDAGJq+9uPgW2spKHkp6XzXTTTkNL7Fml6GPdMG2UCjzx
bst09JZ0z6TmtikfbzQ0HiY72Gho4h++WemMtS/MxhHPB8zx49lexUEwMLTWalOYkFV7VBg2Kvdi

********************************snipped**************************************
```

It had a zip attachment and a password with (Password: @uVmG4NMus) . Decoding the base64 we got a zip (password protected). Extracting the zip gave a word file. Extracting the docx file gave a `vbaProject.bin` . Inspecting the macros with `olevba` .

```bash
olevba 0.55.1 on Python 3.8.1 - http://decalage.info/python/oletools
===============================================================================
FILE: vbaProject.bin
Type: OLE
-------------------------------------------------------------------------------
VBA MACRO ThisDocument.cls 
in file: vbaProject.bin - OLE stream: 'VBA/ThisDocument'
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Const qeletzpyif = 2
Const jlouvjnmew = 1
Const hgsajszpkq = 0
Private Function jhihworeroqddxunrzx(eatnjvyp As String, snhnkbvor As Long) As String
Dim Tbl, vencfvgarczvufa As String, strTemp, lxpauxezygfacat As String, pwipsogiznsqxl As Long, hykiqmgwmibgmow As Byte
Const cvemyhmtgqsvwbnyzzha As String = "ABCDEFGHIJKLMNOPQRSTUVW" & "XYZ"
Const gqbrepcojoj As Byte = 26
Const wbuccvajxcjjha As Byte = 65 - 1
Const eazcwbvbjqofiqfia As Byte = 97 - 1
strTemp = eatnjvyp
If snhnkbvor < gqbrepcojoj And lngNumber > gqbrepcojoj * -1 Then
vencfvgarczvufa = cvemyhmtgqsvwbnyzzha & cvemyhmtgqsvwbnyzzha & cvemyhmtgqsvwbnyzzha & cvemyhmtgqsvwbnyzzha
Tbl = vencfvgarczvufa
For pwipsogiznsqxl = 1 To Len(strTemp)
If Mid(strTemp, pwipsogiznsqxl, jlouvjnmew) Like xitrlsvziikd("5b612d7a412d") & xitrlsvziikd("5a5d") Then
hykiqmgwmibgmow = Asc(Mid(strTemp, pwipsogiznsqxl, jlouvjnmew))
If Mid(strTemp, pwipsogiznsqxl, jlouvjnmew) = Mid(Tbl, hykiqmgwmibgmow - wbuccvajxcjjha, jlouvjnmew) Then
lxpauxezygfacat = lxpauxezygfacat & Mid(Tbl, hykiqmgwmibgmow - wbuccvajxcjjha + snhnkbvor, jlouvjnmew)
Else
lxpauxezygfacat = lxpauxezygfacat & LCase(Mid(Tbl, hykiqmgwmibgmow - eazcwbvbjqofiqfia + snhnkbvor, jlouvjnmew))
End If
Else
lxpauxezygfacat = lxpauxezygfacat & Mid(strTemp, pwipsogiznsqxl, jlouvjnmew)
End If
Next pwipsogiznsqxl
End If
jhihworeroqddxunrzx = lxpauxezygfacat
End Function
Private Sub bhzktzyjlmcapyvxl()
Dim dcdpcwemxccxonyfp As String
Dim mchyjruygvs As String
Dim ledflensmpxsfkn As String
Dim xynalbyflz As Integer
dcdpcwemxccxonyfp = xitrlsvziikd("206f68") & xitrlsvziikd("6365206b2f20646d63")
mchyjruygvs = xitrlsvziikd("7d2121216c6a336870335f3575316b66334a30785f714a306533655f345f4a6d7b2d") & xitrlsvziikd("584c5556454d")
mchyjruygvs = jhihworeroqddxunrzx(mchyjruygvs, 5)
xynalbyflz = Len(dcdpcwemxccxonyfp)
ledflensmpxsfkn = ""
For pos = xynalbyflz To 1 Step -1
Next_Char = Mid(dcdpcwemxccxonyfp, pos, jlouvjnmew)
ledflensmpxsfkn = ledflensmpxsfkn & Next_Char
Next pos
ledflensmpxsfkn = ledflensmpxsfkn & mchyjruygvs
retVal = Shell(ledflensmpxsfkn, hgsajszpkq)
End Sub
Sub Workbook_Open()
bhzktzyjlmcapyvxl
End Sub
Sub AutoOpen()
bhzktzyjlmcapyvxl
End Sub
Private Function xitrlsvziikd(ByVal ppxscssdlsvg As String) As String
Dim pwfoigdypupp As Long
For pwfoigdypupp = 1 To Len(ppxscssdlsvg) Step 2
xitrlsvziikd = xitrlsvziikd & Chr$(Val("&H" & Mid$(ppxscssdlsvg, pwfoigdypupp, 2)))
Next pwfoigdypupp
End Function

+----------+--------------------+---------------------------------------------+
|Type      |Keyword             |Description                                  |
+----------+--------------------+---------------------------------------------+
|AutoExec  |AutoOpen            |Runs when the Word document is opened        |
|AutoExec  |Workbook_Open       |Runs when the Excel Workbook is opened       |
|Suspicious|Shell               |May run an executable file or a system       |
|          |                    |command                                      |
|Suspicious|Chr                 |May attempt to obfuscate specific strings    |
|          |                    |(use option --deobf to deobfuscate)          |
|Suspicious|Hex Strings         |Hex-encoded strings were detected, may be    |
|          |                    |used to obfuscate strings (option --decode to|
|          |                    |see all)                                     |
|Hex String|[a-zA-              |5b612d7a412d                                 |
|Hex String|ce k/ dmc           |6365206b2f20646d63                           |
|Hex String|}!!!lj3hp3_5u1kf3J0x|7d2121216c6a336870335f3575316b66334a30785f714|
|          |_qJ0e3e_4_Jm{-      |a306533655f345f4a6d7b2d                      |
|Hex String|XLUVEM              |584c5556454d                                 |
+----------+--------------------+---------------------------------------------+

```

Found a flag like string `}!!!lj3hp3_5u1kf3J0x_qJ0e3e_4_Jm{-` but was reversed. Reversed it `-{mJ_4_e3e0Jq_x0J3fk1u5_3ph3jl!!!}` but now from the looks of encryption algorithm it looked like a caesar algo.

And yea it was caesar (18). So the complete flag became

`UMDCTF-{uR_4_m3m0Ry_f0R3ns1c5_3xp3rt!!!}`.

Kudos to admin for making a great challenge.

