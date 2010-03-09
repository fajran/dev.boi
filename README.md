dev.blankonlinux.or.id
======================

Panduan
-------

1. Siapkan [buildout](http://pypi.python.org/pypi/zc.buildout)

        $ python bootstrap.py

2. Jalankan buildout

        $ ./bin/buildout

3. Buat proyek

        $ ./bin/trac-admin /path/ke/proyek/

4. Konfigurasi. Cek bagian konfigurasi di bawah untuk informasi lebih lanjut.

        $ vi /path/ke/proyek/conf/trac.ini

5. Jalankan Trac

        $ ./bin/tracd -s -p 8080 /path/ke/proyek/

Konfigurasi
-----------

Konfigurasi tambahan

    [wiki]
    repository_dir = /path/ke/repository/bzr/
    repository_type = bzr 

    [components]
    tracbzr.* = enabled
    trac.web.auth.* = disabled
    authopenid.* = enabled
    includemacro.* = enabled
    tractoc.* = enabled
    redirect.* = enabled
    irclogs.irclogsplugin = enabled
    
    [irclogs]
    indexer = builtin:///var/www/trac/indexer/irclogs.idx?cache=true
    path = /home/irgsh/irc/log/ChannelLogger
    prefix = #blankon

Menambah Modul Baru
-------------------

1. Cek apakah modul ada di [toko keju](http://pypi.python.org/pypi)
2. Kalau ada, sunting `buildout.cfg` dan tambahkan nama paket modul dalam daftar `eggs`
3. Kalau tidak ada, baca panduan dibawah.
4. Jalankan buildout lagi sebelum menjalankan Trac.

        $ ./bin/buildout

### Jika paket modul tidak ada di PyPI

1. Unduh kode sumber

        $ svn co http://trac-hacks.org/svn/irclogsplugin/0.11 irclogs

2. Buat paket distribusi

        $ cd irclogs
        $ python setup.py sdist

3. Letakkan berkas distribusi ke sebuah server yang bisa diakses via http

        $ scp dist/irclogs-0.2.tar.gz server:/path/ke/pypi/

4. Tambahkan repositori paket dalam `buildout.cfg`

        find-links = http://repo.paket/pypi/

5. Tambahkan nama paket ke dalam daftar `eggs`

