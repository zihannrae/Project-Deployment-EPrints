# **Dokumentasi Project Instalasi Eprints**

Berikut adalah dokumentasi untuk project instalasi EPrints: 

**Buka terminal, dan ketikkan command berikut :** 

  #### Lakukan Update sistem 
      apt update && apt upgrade -y

  #### Install *dependency* yang dibutuhkan EPrints 
     sudo apt update && sudo apt install -y build-essential libarchive-tar-perl libwww-perl libxml-parser-perl libcrypt-ssleay-perl libapache2-mod-perl2 libdbd-mysql-perl mysql-server libncurses-dev perl libselinux1 apache2 libxml-libxml-perl libunicode-string-perl libterm-readkey-perl libmime-lite-perl libmime-types-perl libdigest-sha-perl libxml2-dev libxml-twig-perl libarchive-any-perl libjson-perl liblwp-protocol-https-perl libtext-unidecode-perl lynx wget ghostscript poppler-utils antiword elinks texlive-base texlive-binaries psutils imagemagick adduser tar gzip unzip libtex-encode-perl libio-string-perl python3-html2text make libexpat1-dev libxslt1-dev 

  #### Unduh versi EPrints dari halaman resmi EPrints
        Lakukan pengunduhan melalui laman <https://files.eprints.org/>
        
  #### Ekstrak versi EPrints yang telah diunduh ke dalam direktori /opt
      sudo tar -xzf '/home/user/Downloads/eprints-x.x.x.tar.gz' 

  #### Ubah direktori ke folder EPrints yang telah diekstrak 
      cd /opt/eprints-x.x.x 

  #### Pastikan EPrints telah berada di direktori
      *Command* berikut berfungi untuk menampilkan isi direktori
     ls /opt
     ls ~Downloads

  #### Pindah ke direktori downloads dan ekstrak file EPrints
      `cd ~/Downloads tar -xzf eprints-x.x.x.tar.gz`

  #### Tampilkan daftar file dan folder yang ada di dalam direktori Downloads milik user
      `ls ~/Downloads`

  #### Pindahkan folder instalasi EPrints dari ~/Downloads ke direktori /opt/ menggunakan hak akses administrator (sudo).
      `sudo mv ~/Downloads/eprints-x.x.x /opt/`

  #### Masuk ke direktori instalasi EPrints versi 3.4.5 yang berada di dalam /opt/.
      `cd /opt/eprints-3.4.5`
      
  #### Jalankan script konfigurasi awal dari paket EPrints sebelum instalasi dilakukan.
       `sudo ./configure`  

  #### Menambahkan user EPrints
      `adduser eprints` 

  #### Lihat konfigurasi yang aktif 
      `ls /etc/apache2/sites-available/`  

  #### Aktifkan konfigurasi virtual host Apache
      `sudo a2ensite eprints.conf` 

  #### Reload Apache
      `sudo systemctl reload apache2` 

  #### Menginstall aplikasi gedit, text editor GUI bawaan GNOME, menggunakan manajer paket APT.
      gedit memiliki fungsi yang sama dengan sudo nano, namun lebih fleksibel untuk edit virtual host.
       `sudo apt install gedit`

  #### Buka file konfigurasi virtual host Apache untuk EPrints menggunakan editor teks GUI gedit dengan hak administrator.
      `sudo gedit /etc/apache2/sites-available/eprints.conf`

  ##### Restart Apache
     `sudo systemctl restart apache2`

  ####  Masuk ke direktori instalasi EPrints versi 3.4.5 yang berada di dalam /opt/.
      `cd /opt/eprints-3.4.5/`

  #### Tampilkan daftar file dan folder yang ada di direktori saat ini dan jalankan script konfigurasi yang berada di direktori saat ini.
       `ls`
       `./configure`

  #### Masuk ke direktori bin yang berada di dalam folder eprints3.
       cd eprints3/bin

  #### Jalankan tool epadmin milik EPrints untuk menampilkan daftar perintah (help) untuk menampilkan informasi mengenai user EPrints
      sudo /opt/eprints3/bin/epadmin help
      id eprints

  #### Jalankan perintah sebagai user eprints (berpindah user), tapi hanya jika diikuti perintah lain.
      sudo -u eprints

  #### Buat user baru bernama eprints dengan home directory di /opt/eprints3 dan shell /bin/bash untuk menjalankan aplikasi EPrints secara aman.
      sudo useradd -d /opt/eprints3 -s /bin/bash eprints

  #### Tampilkan daftar lengkap perintah (command) dan opsi yang tersedia dalam tool epadmin pada EPrints.
        sudo -u eprints /opt/eprints3/bin/epadmin help`

  #### Buat repository EPrints baru yang bersifat zero dan isi apa yang dibutuhkan di wizard
        sudo -u eprints /opt/eprints3/bin/epadmin create zero 

  #### Restart Apache
        sudo systemctl restart apache2`

  #### Aktifkan (enable) file konfigurasi virtual host Apache bernama eprints.conf.
        sudo a2ensite eprints

  #### Reload apache dan cek apakah konfigurasi Apache valid atau ada error.
        sudo systemctl reload apache2`
        apachectl -t`

  #### Aktifkan modul cgi, perl, eprints pada apache lalu restart apache
        sudo a2enmod cgi`
        sudo a2enmod perl`
        sudo systemctl restart apache2`
        sudo a2ensite eprints`
        sudo systemctl reload apache2`

  #### cari baris yang mengandung kata ScriptAlias di file apache.conf untuk semua repository EPrints yang ada di folder archives.
        grep ScriptAlias /opt/eprints3/archives/*/cfg/apache.conf

  #### buat (generate) file konfigurasi Apache untuk repository EPrints bernama repoutama, lalu menyimpannya ke file sementara /tmp/repoutama_apache.conf.
        sudo -u eprints /opt/eprints3/bin/generate_apacheconf repoutama > /tmp/repoutama_apache.conf

  #### salin file konfigurasi Apache yang baru di-generate ke lokasi konfigurasi Apache sebagai eprints.conf.
        sudo cp /tmp/repoutama_apache.conf /etc/apache2/sites-available/eprints.conf

  #### Aktifkan modul cgi, perl, eprints pada apache lalu restart apache
        sudo a2ensite eprints`
        sudo a2enmod cgi`
        sudo a2enmod perl`
        sudo systemctl restart apache2`

  #### Periksa syntax seluruh konfigurasi Apache
        sudo apachectl -t

  #### Buka file konfigurasi Apache bernama eprints.conf dengan editor teks gedit menggunakan hak akses root dan periksa syntax seluruh konfigurasi Apache
        sudo gedit /etc/apache2/sites-available/eprints.conf
        sudo apachectl -t

  #### Generate file konfigurasi Apache untuk repository EPrints bernama repoutama, lalu menyimpannya ke file /tmp/repoutama_apache.conf. dan tampilkan isi file /tmp/repoutama_apache.conf ke layar (terminal).
        sudo -u eprints /opt/eprints3/bin/generate_apacheconf repoutama >/tmp/repoutama_apache.conf
        cat /tmp/repoutama_apache.conf

  #### Nonaktifkan (disable) konfigurasi virtual host Apache bernama eprints.conf.
        sudo a2dissite eprints

  #### Hapus file konfigurasi Apache eprints.conf dan file symlink virtual host EPrints yang aktif di Apache
        sudo rm /etc/apache2/sites-available/eprints.conf 2>/dev/null
        sudo rm /etc/apache2/sites-enabled/eprints.conf 2>/dev/null
        
  ### Buat ulang (“regenerate”) konfigurasi Apache global EPrints, lalu timpa (replace) file konfigurasi sistem yang digunakan oleh Apache.
        sudo -u eprints /opt/eprints3/bin/generate_apacheconf --system --replace

  #### Buka file konfigurasi utama Apache (apache2.conf) menggunakan editor teks Gedit dengan hak akses root.
        sudo gedit /etc/apache2/apache2.conf

  #### Aktifkan modul cgi dan perl pada apache, restart apache, dan cek status
        sudo a2enmod cgi
        sudo a2enmod perl
        sudo systemctl restart apache2
        sudo systemctl status apache2

  #### buka dan edit file /etc/hosts menggunakan editor Gedit dengan hak akses root.
        sudo gedit /etc/hosts/

  #### Mengecek apakah konfigurasi ServerName sudah benar.
        grep -i ServerName /opt/eprints3/cfg/apache/*.conf

  #### Tes apakah hostname repoutama.local dapat di-resolve dan merespon jaringan
        ping repoutama.local -c 2

  #### Cek informasi konfigurasi virtual host Apache
        sudo apachectl -S

  #### Kirim permintaan HTTP secara detail (verbose) ke URL EPrints, aktifkan virtual host, nonaktifkan virtual host, restart apache
        curl -v http://repoutama.local/cgi/users/login
        sudo a2ensite repoutama.conf
        sudo a2dissite 000-default.conf
        sudo systemctl restart apache2
    
  #### Kirim permintaan HTTP secara detail (verbose) ke URL EPrints
        curl -v http://repoutama.local/cgi/users/login`

  #### Ubah hak akses (permissions) seluruh file dan folder di /opt/eprints3/cgi, dan di direktori CGI repository agar dapat dieksekusi oleh Apache.        
        sudo chmod -R 755 /opt/eprints3/cgi
        sudo chmod -R 755 /opt/eprints3/archives/repoutama/cgi

  #### Ubah kepemilikan (owner dan group) dari semua file dan folder di /opt/eprints3/cgi dan di direktori CGI repository, lalu restart apache
        sudo chown -R eprints:www-data /opt/eprints3/cgi
        sudo chown -R eprints:www-data /opt/eprints3/archives/repoutama/cgi
        sudo systemctl restart apache2

  #### Kirim permintaan HTTP secara detail (verbose) ke URL EPrints
        curl -v http://repoutama.local/cgi/users/login

  #### Pindah menjadi user eprints dan 
        sudo su - eprints

  #### Akses laman eprints yang sudah selesai
        akses http:/repoutama.local/cgi/users/home`
  ![foto hasil](https://github.com/user-attachments/assets/0792b2e2-5e29-460e-876a-b9aa3a97ac67)
  
  ### Log in dengan username dan password yang dibuat
        Instalasi selesai
