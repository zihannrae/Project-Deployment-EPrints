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
30. `make install`
31. `ls`
32. `cd bin`
33. `ls`
34. `cd /opt/`
35. `ls`
36. `cd eprints3/bin`
37. `ls`
38. `sudo /opt/eprints3/bin/epadmin help`
39. `id eprints`
40. `sudo -u eprints`
41. `sudo useradd -d /opt/eprints3 -s /bin/bash eprints`
42. `sudo -u eprints /opt/eprints3/bin/epadmin help`
43. `sudo -u eprints /opt/eprints3/bin/epadmin create zero (mengisi archive id, hostname, alias, dll)`
44. `sudo systemctl restart apache2`
45. `sudo a2ensite eprints`
46. `sudo systemctl reload apache2`
47. `apachectl -t`
48. `sudo a2enmod cgi`
49. `sudo a2enmod perl`
50. `sudo systemctl restart apache2`
51. `sudo a2ensite eprints`
52. `sudo systemctl reload apache2`
53. `grep ScriptAlias /opt/eprints3/archives/*/cfg/apache.conf`
54. `cd archives`
55. `ls`
56. `cd repoutama`
57. `ls`
58. `cd cfg`
59. `ls`
60. `sudo -u eprints /opt/eprints3/bin/generate_apacheconf repoutama > /tmp/repoutama_apache.conf`
61. `sudo cp /tmp/repoutama_apache.conf /etc/apache2/sites-available/eprints.conf`
62. `sudo a2ensite eprints`
63. `sudo a2enmod cgi`
64. `sudo a2enmod perl`
65. `sudo systemctl restart apache2`
66. `sudo apachectl -t`
67. `sudo gedit /etc/apache2/sites-available/eprints.conf`
68. `sudo apachectl -t`
69. `sudo -u eprints /opt/eprints3/bin/generate_apacheconf repoutama >/tmp/repoutama_apache.conf`
70. `cat /tmp/repoutama_apache.conf`
71. `sudo a2dissite eprints`
72. `sudo rm /etc/apache2/sites-available/eprints.conf 2>/dev/null`
73. `sudo rm /etc/apache2/sites-enabled/eprints.conf 2>/dev/null`
74. `sudo -u eprints /opt/eprints3/bin/generate_apacheconf --system --replace`
75. `cat /tmp/repoutama_apache.conf`
76. `sudo gedit /etc/apache2/apache2.conf`
77. `sudo a2enmod cgi`
78. `sudo a2enmod perl`
79. `sudo systemctl restart apache2`
80. `sudo systemctl status apache2`
81. `sudo gedit /etc/hosts/`
82. `grep -i ServerName /opt/eprints3/cfg/apache/*.conf`
83. `ping repoutama.local -c 2`
84. `sudo apachectl -S`
85. `grep -R "opt/eprints3/cfg/apache.conf" /etc/apache2/apache2.conf`
86. `ls /opt/eprints3/cfg/apache/`
87. `curl -v http://repoutama.local/cgi/users/login`
88. `sudo a2ensite repoutama.conf`
89. `sudo a2dissite 000-default.conf`
90. `sudo systemctl restart apache2`
91. `apache2ctl -S`
92. `sudo a2dissite myrepo.conf`
93. `sudo rm /etc/apache2/sites-available/myrepo.conf`
94. `sudo rm /etc/apache2/sites-enabled/myrepo.conf`
95. `sudo rm /opt/eprints3/cfg/apache/myrepo.conf`
96. `sudo systemctl restart apache2`
97. `apache2ctl -S`
98. `curl -v http://repoutama.local/cgi/users/login`
99. `sudo chmod -R 755 /opt/eprints3/cgi`
100. `sudo chmod -R 755 /opt/eprints3/archives/repoutama/cgi`
101. `sudo chown -R eprints:www-data /opt/eprints3/cgi`
102. `sudo chown -R eprints:www-data /opt/eprints3/archives/repoutama/cgi`
103. `sudo systemctl restart apache2`
104. `curl -v http://repoutama.local/cgi/users/login`
105. `sudo tail -n 30 /var/log/apache2/error.log`
106. `sudo su - eprints`
107. `/opt/eprints3/bin/epadmin list_users repoutama`
108. `akses http:/repoutama.local/cgi/users/home` ![foto hasil](https://github.com/user-attachments/assets/0792b2e2-5e29-460e-876a-b9aa3a97ac67)
109. **Log in dengan username dan password yang dibuat**
110. **Langkah selesai.**
