# SPDX-License-Identifier: LGPL-2.1+

util_sources = files('''
        log.c
        log.h
        util.c
        util.h
'''.split())

libcasync_headers = files('''
        cacache.h
        cachunk.h
        cachunker.h
        cachunkid.h
        cacommon.h
        cacompression.h
        cadecoder.h
        cadigest.h
        caencoder.h
        cafileroot.h
        caformat-util.h
        caformat.h
        camatch.h
        caindex.h
        calocation.h
        camakebst.h
        canametable.h
        canbd.h
        caorigin.h
        caprotocol-util.h
        caprotocol.h
        caremote.h
        caseed.h
        castore.h
        casync.h
        cautil.h
        chattr.h
        compressor.h
        def.h
        dirent-util.h
        fssize.h
        gc.h
        gcc-macro.h
        hash-funcs.h
        hashmap.h
        mempool.h
        notify.h
        parse-util.h
        quota-projid.h
        realloc-buffer.h
        reflink.h
        rm-rf.h
        set.h
        siphash24.h
'''.split())

install_headers(libcasync_headers, subdir: 'casync')

libshared_sources = files('''
        cacache.c
        cacache.h
        cachunk.c
        cachunk.h
        cachunker.c
        cachunker.h
        cachunkid.c
        cachunkid.h
        cacommon.h
        cacompression.c
        cacompression.h
        cadecoder.c
        cadecoder.h
        cadigest.c
        cadigest.h
        caencoder.c
        caencoder.h
        cafileroot.c
        cafileroot.h
        caformat-util.c
        caformat-util.h
        caformat.h
        camatch.c
        camatch.h
        caindex.c
        caindex.h
        calocation.c
        calocation.h
        camakebst.c
        camakebst.h
        canametable.c
        canametable.h
        canbd.c
        canbd.h
        caorigin.c
        caorigin.h
        caprotocol-util.c
        caprotocol-util.h
        caprotocol.h
        caremote.c
        caremote.h
        caseed.c
        caseed.h
        castore.c
        castore.h
        casync.c
        casync.h
        cautil.c
        cautil.h
        chattr.c
        chattr.h
        compressor.c
        compressor.h
        def.h
        dirent-util.c
        dirent-util.h
        fssize.c
        fssize.h
        gc.c
        gc.h
        gcc-macro.h
        hash-funcs.c
        hash-funcs.h
        hashmap.c
        hashmap.h
        mempool.c
        mempool.h
        notify.c
        notify.h
        parse-util.c
        parse-util.h
        quota-projid.c
        quota-projid.h
        realloc-buffer.c
        realloc-buffer.h
        reflink.c
        reflink.h
        rm-rf.c
        rm-rf.h
        set.h
        siphash24.c
        siphash24.h
'''.split())

libcasync = shared_library(
        'casync',
        [libshared_sources, util_sources],
        dependencies : [
                liblzma,
                libzstd,
                libz,
                libacl,
                libselinux,
                math,
                openssl],
        version : '0.1',
        soversion : '0',
        install: true)

libcasync_static = static_library(
              'casync',
              libshared_sources,
              util_sources,
              install: true)

casync_sources = files('''
        casync-tool.c
        canbd.c
        canbd.h
        cafuse.h
        signal-handler.c
        signal-handler.h
'''.split())

if conf.get('HAVE_FUSE') == 1
        casync_sources += files('cafuse.c')
endif

casync_http_sources = files('casync-http.c')
