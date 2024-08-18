# Note 
##### Sebelum memulai anda harus mempunyai rclone terinstall terlebih dahulu di device yang di gunakan
##### Tutorial jika anda menggunakan [WINDOWS](https://youtu.be/dTFt2DkOde4?si=E17zRc4BslGIWn3V) hanya sampai bagian install saja

# Cara Menjalankan Script?
##### 1. Unduh file installer.sh
```html
curl -O https://raw.githubusercontent.com/NiamSky/AutoBackupVps/main/installer.sh
```
##### 2. Buka file tersebut dan ganti "name" dengan nama pusat file backup Anda yang akan digunakan saat mentransfer file ke Google Drive
```java
// Nama Data Backup Anda, ganti ini 
name
//
```
##### 3. Simpan perubahan dan jalankan script:
```html
chmod +x ./autobackup.sh
./autobackup.sh
```
##### 4. Jika script berhasil dijalankan, akan muncul sebuah tautan yang meminta Anda untuk menghubungkan akun yang akan digunakan untuk backup file.
##### 5. Salin kode di Chrome Anda dan tempel ke VPS

# Cara Mengatur Backup Otomatis
1. Buat file backup.sh
2. Kemudian salin script ini dan tempel di file backup.sh
```html
date=$(date +%d-%m-%y)
zip -r namafile-$date.zip /root/directory/
rclone copy namafile-$date.zip name:
rm namafile-$date.zip
```
> Ganti "namafile" dengan nama file yang akan dibackup dan yang akan muncul di Google Drive <br>
> Ganti /root/directory/ dengan lokasi folder yang akan secara otomatis di-zip <br>
> Ganti "name" dengan nama yang Anda masukkan pada langkah ketiga (step ketiga)
### PERINGATAN!!! Jangan ganti apa yang tidak saya minta untuk diganti
3. Simpan file dan jalankan script:
```html
chmod +x ./backup.sh
```
```html
apt-get install cron
crontab -e
```
```html
1
```
> Kemudian tempelkan script ini di luar # atau di bagian bawah
```html
* 7 * * * bash /root/backup.sh
```
![gambar](https://gosigitgo.files.wordpress.com/2010/03/crontab-syntax.gif?w=510)

> * 7 * * * Berarti script akan dijalankan secara otomatis setiap jam 7 pagi, atau file akan ditransfer ke Google Drive setiap jam 7 pagi
4. Dan simpan file tersebut
> Jika Anda menggunakan editor dari VPS, tekan CTRL+X lalu Y untuk menyimpan perubahan

# Perintah Manual RCLONE
### Buat Folder
```html
rclone mkdir name:/namaFolder
```
> Ganti "name" dengan nama pusat file backup Anda pada langkah 3

### Salin File ke Google Drive
```html
rclone copy namafile.zip name:
```
> Ganti "name" dengan nama pusat file backup Anda pada langkah 3 <br>
> Ganti "namafile" dengan nama file yang ingin Anda salin ke Google Drive

### Unduh file dari Google Drive ke VPS Anda
```html
rclone copy name:/namafile.zip /root/
```
> Ganti "name" dengan nama pusat file backup Anda pada langkah 3 <br>
> Ganti "namafile" dengan nama file yang ingin Anda salin ke Google Drive <br>
> Ganti "root" dengan tempat Anda ingin meletakkan file unduhan

### Periksa file di Google Drive
```html
rclone ls name:
```
> Ganti "name" dengan nama pusat file backup Anda pada langkah 3

# Manual:
> Jika metode di atas tidak berhasil atau error, gunakan script manual.
```html
apt update && apt upgrade
```
```html
curl -O https://downloads.rclone.org/rclone-current-linux-amd64.zip
```
```html
unzip rclone-current-linux-amd64.zip
```
```html
cd rclone-*-linux-amd64
```
```html
cp rclone /usr/bin/
```
```html
chown root:root /usr/bin/rclone
```
```html
chmod 755 /usr/bin/rclone
```
```html
cd
```
```html
rclone config
```
```html
n
```
```html
enter.
```
#### Ganti "name" dengan nama pusat file backup Anda.
```html
name
```
```html
drive
```
```html
enter.
```
```html
enter.
```
```html
1
```
```html
enter.
```
```html
enter.
```
```html
n
```
- Kemudian jika script berhasil dijalankan, akan muncul sebuah tautan yang meminta Anda untuk menghubungkan akun yang akan digunakan untuk backup file.
- Salin kode di Chrome Anda dan tempel ke VPS
