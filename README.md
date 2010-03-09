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

