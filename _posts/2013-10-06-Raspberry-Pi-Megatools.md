---
layout: post
title: Raspberry Pi - Megatools
---

At the moment, I'm using Amazon S3 to store video from my CCTV, but I wanted to play around with using [Mega.co.nz](http://mega.co.nz) as it is free for the first 10 GBs of data. The first step was to get [Megatools](http://megatools.megous.com/) installed and setup on my Pi. This required me to download and build the megatools source code using the following commands:

	$ cd ~
	$ sudo apt-get install gcc build-essential libcurl4-openssl-dev libglib2.0-dev glib-networking
	$ wget http://megatools.megous.com/builds/megatools-1.9.91.tar.gz
	$ tar -xvzf megatools-1.9.91.tar.gz
	$ cd megatools-1.9.91
	$ ./configure --disable-shared
	$ make
	$ sudo make install

Once the above is completed, Megatools should now be fully installed. The usage of Megatools is quite simple, you get an array of new executables (megadf, megadl, megaget, megals, megamkdir, megamv, megaput, megareg, megarm, megasync) all named similar to their Unix equivalent, but with a prefix of 'mega'. You should quickly guess what each of them does!

Example usage:

	$ megals -u <USERNAME>
 
	$ megaput -u <USERNAME> <FILENAME>



The output of my build / install process was:

	19:28:40 rpicam:~$ sudo apt-get install gcc build-essential libcurl4-openssl-dev libglib2.0-dev glib-networking
	Reading package lists... Done
	Building dependency tree
	Reading state information... Done
	build-essential is already the newest version.
	gcc is already the newest version.
	gcc set to manually installed.
	glib-networking is already the newest version.
	glib-networking set to manually installed.
	The following extra packages will be installed:
	  curl libcurl3 libelf1 libgcrypt11-dev libglib2.0-bin libgnutls-dev libgnutls-openssl27 libgnutlsxx27 libgpg-error-dev libidn11-dev libldap2-dev libp11-kit-dev libpcre3-dev libpcrecpp0 librtmp-dev libssh2-1-dev libtasn1-3-dev
	Suggested packages:
	  libcurl3-dbg libgcrypt11-doc libglib2.0-doc gnutls26-doc
	The following NEW packages will be installed:
	  libcurl4-openssl-dev libelf1 libgcrypt11-dev libglib2.0-bin libglib2.0-dev libgnutls-dev libgnutls-openssl27 libgnutlsxx27 libgpg-error-dev libidn11-dev libldap2-dev libp11-kit-dev libpcre3-dev libpcrecpp0 librtmp-dev libssh2-1-dev libtasn1-3-dev
	The following packages will be upgraded:
	  curl libcurl3
	2 upgraded, 17 newly installed, 0 to remove and 50 not upgraded.
	Need to get 1,798 kB/8,896 kB of archives.
	After this operation, 19.2 MB of additional disk space will be used.
	Do you want to continue [Y/n]? y
	Get:1 http://mirrordirector.raspbian.org/raspbian/ wheezy/main curl armhf 7.26.0-1+wheezy4 [267 kB]
	Get:2 http://mirrordirector.raspbian.org/raspbian/ wheezy/main libcurl3 armhf 7.26.0-1+wheezy4 [312 kB]
	Get:3 http://mirrordirector.raspbian.org/raspbian/ wheezy/main libcurl4-openssl-dev armhf 7.26.0-1+wheezy4 [1,218 kB]
	Fetched 1,798 kB in 13s (133 kB/s)
	Selecting previously unselected package libgnutls-openssl27:armhf.
	(Reading database ... 67269 files and directories currently installed.)
	Unpacking libgnutls-openssl27:armhf (from .../libgnutls-openssl27_2.12.20-7_armhf.deb) ...
	Preparing to replace curl 7.26.0-1+wheezy3 (using .../curl_7.26.0-1+wheezy4_armhf.deb) ...
	Unpacking replacement curl ...
	Preparing to replace libcurl3:armhf 7.26.0-1+wheezy3 (using .../libcurl3_7.26.0-1+wheezy4_armhf.deb) ...
	Unpacking replacement libcurl3:armhf ...
	Selecting previously unselected package libelf1.
	Unpacking libelf1 (from .../libelf1_0.152-1+wheezy1_armhf.deb) ...
	Selecting previously unselected package libglib2.0-bin.
	Unpacking libglib2.0-bin (from .../libglib2.0-bin_2.33.12+really2.32.4-5_armhf.deb) ...
	Selecting previously unselected package libpcrecpp0:armhf.
	Unpacking libpcrecpp0:armhf (from .../libpcrecpp0_1%3a8.30-5_armhf.deb) ...
	Selecting previously unselected package libgnutlsxx27:armhf.
	Unpacking libgnutlsxx27:armhf (from .../libgnutlsxx27_2.12.20-7_armhf.deb) ...
	Selecting previously unselected package libidn11-dev.
	Unpacking libidn11-dev (from .../libidn11-dev_1.25-2_armhf.deb) ...
	Selecting previously unselected package libldap2-dev:armhf.
	Unpacking libldap2-dev:armhf (from .../libldap2-dev_2.4.31-1+nmu2_armhf.deb) ...
	Selecting previously unselected package libgpg-error-dev.
	Unpacking libgpg-error-dev (from .../libgpg-error-dev_1.10-3.1_armhf.deb) ...
	Selecting previously unselected package libgcrypt11-dev.
	Unpacking libgcrypt11-dev (from .../libgcrypt11-dev_1.5.0-5+deb7u1_armhf.deb) ...
	Selecting previously unselected package libtasn1-3-dev.
	Unpacking libtasn1-3-dev (from .../libtasn1-3-dev_2.13-2_armhf.deb) ...
	Selecting previously unselected package libp11-kit-dev.
	Unpacking libp11-kit-dev (from .../libp11-kit-dev_0.12-3_armhf.deb) ...
	Selecting previously unselected package libgnutls-dev.
	Unpacking libgnutls-dev (from .../libgnutls-dev_2.12.20-7_armhf.deb) ...
	Selecting previously unselected package librtmp-dev.
	Unpacking librtmp-dev (from .../librtmp-dev_2.4+20111222.git4e06e21-1_armhf.deb) ...
	Selecting previously unselected package libssh2-1-dev.
	Unpacking libssh2-1-dev (from .../libssh2-1-dev_1.4.2-1.1_armhf.deb) ...
	Selecting previously unselected package libcurl4-openssl-dev.
	Unpacking libcurl4-openssl-dev (from .../libcurl4-openssl-dev_7.26.0-1+wheezy4_armhf.deb) ...
	Selecting previously unselected package libpcre3-dev.
	Unpacking libpcre3-dev (from .../libpcre3-dev_1%3a8.30-5_armhf.deb) ...
	Selecting previously unselected package libglib2.0-dev.
	Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.33.12+really2.32.4-5_armhf.deb) ...
	Processing triggers for man-db ...
	Processing triggers for install-info ...
	Processing triggers for libglib2.0-0:armhf ...
	Setting up libgnutls-openssl27:armhf (2.12.20-7) ...
	Setting up libcurl3:armhf (7.26.0-1+wheezy4) ...
	Setting up curl (7.26.0-1+wheezy4) ...
	Setting up libelf1 (0.152-1+wheezy1) ...
	Setting up libglib2.0-bin (2.33.12+really2.32.4-5) ...
	Setting up libpcrecpp0:armhf (1:8.30-5) ...
	Setting up libgnutlsxx27:armhf (2.12.20-7) ...
	Setting up libidn11-dev (1.25-2) ...
	Setting up libldap2-dev:armhf (2.4.31-1+nmu2) ...
	Setting up libgpg-error-dev (1.10-3.1) ...
	Setting up libgcrypt11-dev (1.5.0-5+deb7u1) ...
	Setting up libtasn1-3-dev (2.13-2) ...
	Setting up libp11-kit-dev (0.12-3) ...
	Setting up libgnutls-dev (2.12.20-7) ...
	Setting up librtmp-dev (2.4+20111222.git4e06e21-1) ...
	Setting up libssh2-1-dev (1.4.2-1.1) ...
	Setting up libcurl4-openssl-dev (7.26.0-1+wheezy4) ...
	Setting up libpcre3-dev (1:8.30-5) ...
	Setting up libglib2.0-dev (2.33.12+really2.32.4-5) ...

	19:30:47 rpicam:~$ wget http://megatools.megous.com/builds/megatools-1.9.91.tar.gz
		snip....

	19:30:55 rpicam:~$ tar -xvzf megatools-1.9.91.tar.gz
		snip....

	19:31:10 rpicam:~$ cd megatools-1.9.91
	19:31:15 rpicam:megatools-1.9.91$ ./configure --disable-shared
	checking for a BSD-compatible install... /usr/bin/install -c
	checking whether build environment is sane... yes
	checking for a thread-safe mkdir -p... /bin/mkdir -p
	checking for gawk... no
	checking for mawk... mawk
	checking whether make sets $(MAKE)... yes
	checking whether make supports nested variables... yes
	checking whether to enable maintainer-specific portions of Makefiles... no
	checking whether make supports nested variables... (cached) yes
	checking for gcc... gcc
	checking whether the C compiler works... yes
	checking for C compiler default output file name... a.out
	checking for suffix of executables...
	checking whether we are cross compiling... no
	checking for suffix of object files... o
	checking whether we are using the GNU C compiler... yes
	checking whether gcc accepts -g... yes
	checking for gcc option to accept ISO C89... none needed
	checking for style of include used by make... GNU
	checking dependency style of gcc... gcc3
	checking whether gcc and cc understand -c and -o together... yes
	checking build system type... armv6l-unknown-linux-gnueabihf
	checking host system type... armv6l-unknown-linux-gnueabihf
	checking how to print strings... printf
	checking for a sed that does not truncate output... /bin/sed
	checking for grep that handles long lines and -e... /bin/grep
	checking for egrep... /bin/grep -E
	checking for fgrep... /bin/grep -F
	checking for ld used by gcc... /usr/bin/ld
	checking if the linker (/usr/bin/ld) is GNU ld... yes
	checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
	checking the name lister (/usr/bin/nm -B) interface... BSD nm
	checking whether ln -s works... yes
	checking the maximum length of command line arguments... 1572864
	checking whether the shell understands some XSI constructs... yes
	checking whether the shell understands "+="... yes
	checking how to convert armv6l-unknown-linux-gnueabihf file names to armv6l-unknown-linux-gnueabihf format... func_convert_file_noop
	checking how to convert armv6l-unknown-linux-gnueabihf file names to toolchain format... func_convert_file_noop
	checking for /usr/bin/ld option to reload object files... -r
	checking for objdump... objdump
	checking how to recognize dependent libraries... pass_all
	checking for dlltool... dlltool
	checking how to associate runtime and link libraries... printf %s\n
	checking for ar... ar
	checking for archiver @FILE support... @
	checking for strip... strip
	checking for ranlib... ranlib
	checking command to parse /usr/bin/nm -B output from gcc object... ok
	checking for sysroot... no
	checking for mt... mt
	checking if mt is a manifest tool... no
	checking how to run the C preprocessor... gcc -E
	checking for ANSI C header files... yes
	checking for sys/types.h... yes
	checking for sys/stat.h... yes
	checking for stdlib.h... yes
	checking for string.h... yes
	checking for memory.h... yes
	checking for strings.h... yes
	checking for inttypes.h... yes
	checking for stdint.h... yes
	checking for unistd.h... yes
	checking for dlfcn.h... yes
	checking for objdir... .libs
	checking if gcc supports -fno-rtti -fno-exceptions... no
	checking for gcc option to produce PIC... -fPIC -DPIC
	checking if gcc PIC flag -fPIC -DPIC works... yes
	checking if gcc static flag -static works... yes
	checking if gcc supports -c -o file.o... yes
	checking if gcc supports -c -o file.o... (cached) yes
	checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
	checking dynamic linker characteristics... GNU/Linux ld.so
	checking how to hardcode library paths into programs... immediate
	checking whether stripping libraries is possible... yes
	checking if libtool supports shared libraries... yes
	checking whether to build shared libraries... no
	checking whether to build static libraries... yes
	checking for ANSI C header files... (cached) yes
	checking for pkg-config... /usr/bin/pkg-config
	checking pkg-config is at least version 0.16... yes
	checking for GLIB - version >= 2.32.0... yes (version 2.32.4)
	checking for gobject-introspection... no
	checking for MEGA... yes
	checking for FUSE... no
	checking for GLIBTESTS... no
	checking that generated files are newer than configure... done
	configure: creating ./config.status
	config.status: creating Makefile
	config.status: creating libmega.pc
	config.status: creating mega/Makefile
	config.status: creating mega/gjs/Makefile
	config.status: creating tools/Makefile
	config.status: creating tests/Makefile
	config.status: creating docs/Makefile
	config.status: creating config.h
	config.status: executing depfiles commands
	config.status: executing libtool commands

	Configured features:

	  docs build: no
	  warnings: no
	  megafs: no (requires fuse)
	  tests: no (requires glib-2.0 >= 2.34.0)

	Run make now.

	NOTE: On FreeBSD, you need to use GNU make (gmake)

	19:32:00 rpicam:megatools-1.9.91$ make
	make  all-recursive
	Making all in mega
	  GEN    mega-marshal.list
	  GEN    mega-marshal.c
	  GEN    mega-marshal.h
	  GEN    mega-enum-types.c
	  GEN    mega-enum-types.h
	make  all-recursive
	Making all in gjs
	make[4]: Nothing to be done for `all'.
	  CC       mega-aes-key.lo
	  CC       mega-rsa-key.lo
	  CC       mega-chunked-cbc-mac.lo
	  CC       mega-http-client.lo
	  CC       mega-http-io-stream.lo
	  CC       mega-http-input-stream.lo
	  CC       mega-http-output-stream.lo
	  CC       mega-aes-ctr-encryptor.lo
	  CC       utils.lo
	  CC       mega-marshal.lo
	  CC       mega-enum-types.lo
	  CCLD     libmega.la
	Making all in tests
	make[2]: Nothing to be done for `all'.
	Making all in tools
	  CC       sjson.gen.lo
	  CC       http.lo
	  CC       oldmega.lo
	  CC       tools.lo
	  CCLD     libtools.la
	  CC       df.o
	  CCLD     megadf
	  CC       dl.o
	  CCLD     megadl
	  CC       get.o
	  CCLD     megaget
	  CC       ls.o
	  CCLD     megals
	  CC       mkdir.o
	  CCLD     megamkdir
	  CC       put.o
	  CCLD     megaput
	  CC       reg.o
	  CCLD     megareg
	  CC       rm.o
	  CCLD     megarm
	  CC       mv.o
	  CCLD     megamv
	  CC       sync.o
	  CCLD     megasync
	Making all in docs
	make  all-am
	make[3]: Nothing to be done for `all-am'.

	19:35:13 rpicam:megatools-1.9.91$ sudo make install
	Making install in mega
	make  install-recursive
	Making install in gjs
	make[4]: Nothing to be done for `install-exec-am'.
	 /bin/mkdir -p '/usr/local/share/gjs-1.0'
	 /usr/bin/install -c -m 644 mega.js '/usr/local/share/gjs-1.0'
	 /bin/mkdir -p '/usr/local/lib'
	 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libmega.la '/usr/local/lib'
	libtool: install: /usr/bin/install -c .libs/libmega.lai /usr/local/lib/libmega.la
	libtool: install: /usr/bin/install -c .libs/libmega.a /usr/local/lib/libmega.a
	libtool: install: chmod 644 /usr/local/lib/libmega.a
	libtool: install: ranlib /usr/local/lib/libmega.a
	libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /usr/local/lib
	----------------------------------------------------------------------
	Libraries have been installed in:
	   /usr/local/lib

	If you ever happen to want to link against installed libraries
	in a given directory, LIBDIR, you must either use libtool, and
	specify the full pathname of the library, or use the `-LLIBDIR'
	flag during linking and do at least one of the following:
	   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
		 during execution
	   - add LIBDIR to the `LD_RUN_PATH' environment variable
		 during linking
	   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
	   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

	See any operating system documentation about shared libraries for
	more information, such as the ld(1) and ld.so(8) manual pages.
	----------------------------------------------------------------------
	 /bin/mkdir -p '/usr/local/include/mega'
	 /usr/bin/install -c -m 644 mega-aes-key.h mega-rsa-key.h mega-chunked-cbc-mac.h mega-http-client.h mega-http-io-stream.h mega-http-input-stream.h mega-http-output-stream.h mega-aes-ctr-encryptor.h utils.h megatypes.h mega.h mega-enum-types.h '/usr/local/include/mega'
	Making install in tests
	make[2]: Nothing to be done for `install-exec-am'.
	make[2]: Nothing to be done for `install-data-am'.
	Making install in tools
	 /bin/mkdir -p '/usr/local/bin'
	  /bin/bash ../libtool   --mode=install /usr/bin/install -c megadf megadl megaget megals megamkdir megaput megareg megarm megamv megasync '/usr/local/bin'
	libtool: install: /usr/bin/install -c megadf /usr/local/bin/megadf
	libtool: install: /usr/bin/install -c megadl /usr/local/bin/megadl
	libtool: install: /usr/bin/install -c megaget /usr/local/bin/megaget
	libtool: install: /usr/bin/install -c megals /usr/local/bin/megals
	libtool: install: /usr/bin/install -c megamkdir /usr/local/bin/megamkdir
	libtool: install: /usr/bin/install -c megaput /usr/local/bin/megaput
	libtool: install: /usr/bin/install -c megareg /usr/local/bin/megareg
	libtool: install: /usr/bin/install -c megarm /usr/local/bin/megarm
	libtool: install: /usr/bin/install -c megamv /usr/local/bin/megamv
	libtool: install: /usr/bin/install -c megasync /usr/local/bin/megasync
	make[2]: Nothing to be done for `install-data-am'.
	Making install in docs
	make  install-am
	make[3]: Nothing to be done for `install-exec-am'.
	 /bin/mkdir -p '/usr/local/share/man/man1'
	 /usr/bin/install -c -m 644 megadf.1 megadl.1 megaget.1 megals.1 megamkdir.1 megaput.1 megareg.1 megarm.1 megamv.1 megasync.1 megafs.1 '/usr/local/share/man/man1'
	 /bin/mkdir -p '/usr/local/share/man/man5'
	 /usr/bin/install -c -m 644 megarc.5 '/usr/local/share/man/man5'
	 /bin/mkdir -p '/usr/local/share/man/man7'
	 /usr/bin/install -c -m 644 megatools.7 '/usr/local/share/man/man7'
	make[2]: Nothing to be done for `install-exec-am'.
	 /bin/mkdir -p '/usr/local/share/doc/megatools'
	 /usr/bin/install -c -m 644 LICENSE NEWS TODO README INSTALL HACKING '/usr/local/share/doc/megatools'
	 /bin/mkdir -p '/usr/local/lib/pkgconfig'
	 /usr/bin/install -c -m 644 libmega.pc '/usr/local/lib/pkgconfig'
	19:36:41 rpicam:megatools-1.9.91$
