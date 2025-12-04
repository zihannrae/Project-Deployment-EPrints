# **Dokumentasi Project Instalasi Eprints**

Berikut adalah dokumentasi untuk project instalasi EPrints: 

**Buka terminal, dan ketikkan command berikut :** 

  #### Lakukan Update sistem 
      `apt update && apt upgrade -y`

  #### Install *dependency* yang dibutuhkan EPrints 
     `sudo apt-get install build-essential libarchive-tar-perl libwww-perl libxml-parser-perl libcrypt-ssleay-perl libapache2-mod-perl2 libdbd-mysql-perl mysql-server` 

  #### Unduh versi EPrints dari halaman resmi EPrints
        Lakukan pengunduhan melalui laman <https://files.eprints.org/>
        
  #### Ekstrak versi EPrints yang telah diunduh ke dalam direktori /opt
      `sudo tar -xzf '/home/user/Downloads/eprints-x.x.x.tar.gz'` 

  #### Ubah direktori ke folder EPrints yang telah diekstrak 
      `cd /opt/eprints-x.x.x` 

  #### Pastikan EPrints telah berada di direktori
      *Command* berikut berfungi untuk menampilkan isi direktori
     `ls /opt`
     `ls ~Downloads`

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

  #### Lakukan isntalasi *dependency* yang dibutuhkan
      `sudo apt install libncurses-dev`
       `apt install perl libselinux1 apache2 libapache2-mod-perl2 libxml-libxml-perl \ ``libunicode-string-perl libterm-readkey-perl libmime-lite-perl libmime-types-perl libdigest-sha-perl \` 
       `sudo apt install libunicode-string-perl sudo apt install libterm-readkey-perl sudo apt install libmime-lite-perl sudo apt install libdigest-sha-perl \ sudo apt install libdbd-mysql-perl libxml-parser-perl libxml2-dev libxml-twig-perl libarchive-any-perl libjson-perl`
       `sudo apt install liblwp-protocol-https-perl libtext-unidecode-perl lynx wget ghostscript poppler-utils antiword elinks` `sudo apt install texlive-base texlive-binaries psutils imagemagick adduser tar gzip unzip libsearch-xapian-perl`
       `sudo apt install libtex-encode-perl libio-string-perl python3-html2text make libexpat1-dev libxslt1-dev` 

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
72. `sudo a2dissite eprints`
73. `sudo rm /etc/apache2/sites-available/eprints.conf 2>/dev/null`
74. `sudo rm /etc/apache2/sites-enabled/eprints.conf 2>/dev/null`
75. `sudo -u eprints /opt/eprints3/bin/generate_apacheconf --system --replace`
76. `cat /tmp/repoutama_apache.conf`
77. `sudo gedit /etc/apache2/apache2.conf`
78. `sudo a2enmod cgi`
79. `sudo a2enmod perl`
80. `sudo systemctl restart apache2`
81. `sudo systemctl status apache2`
82. `sudo gedit /etc/hosts/`
83. `grep -i ServerName /opt/eprints3/cfg/apache/*.conf`
84. `ping repoutama.local -c 2`
85. `sudo apachectl -S`
86. `grep -R "opt/eprints3/cfg/apache.conf" /etc/apache2/apache2.conf`
87. `ls /opt/eprints3/cfg/apache/`
88. `curl -v http://repoutama.local/cgi/users/login`
89. `sudo a2ensite repoutama.conf`
90. `sudo a2dissite 000-default.conf`
91. `sudo systemctl restart apache2`
92. `apache2ctl -S`
93. `sudo a2dissite myrepo.conf`
94. `sudo rm /etc/apache2/sites-available/myrepo.conf`
95. `sudo rm /etc/apache2/sites-enabled/myrepo.conf`
96. `sudo rm /opt/eprints3/cfg/apache/myrepo.conf`
97. `sudo systemctl restart apache2`
98. `apache2ctl -S`
99. `curl -v http://repoutama.local/cgi/users/login`
100. `sudo chmod -R 755 /opt/eprints3/cgi`
101. `sudo chmod -R 755 /opt/eprints3/archives/repoutama/cgi`
102. `sudo chown -R eprints:www-data /opt/eprints3/cgi`
103. `sudo chown -R eprints:www-data /opt/eprints3/archives/repoutama/cgi`
104. `sudo systemctl restart apache2`
105. `curl -v http://repoutama.local/cgi/users/login`
106. `sudo tail -n 30 /var/log/apache2/error.log`
107. `sudo su - eprints`
108. `/opt/eprints3/bin/epadmin list_users repoutama`
109. `akses http:/repoutama.local/cgi/users/home` ![foto hasil](https://github.com/user-attachments/assets/0792b2e2-5e29-460e-876a-b9aa3a97ac67)
110. **Log in dengan username dan password yang dibuat**
111. **Langkah selesai.**
