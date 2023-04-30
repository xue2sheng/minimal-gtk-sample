# minimal-gtk-sample
Minimal GTK4 sample in Rust to be used as template from command line or Intellij IDEA

## Starting point

Do not forget to review [online documentation](https://gtk-rs.org/gtk4-rs/stable/latest/book)

## Unable to statically build

GTK4 is not friendly with **musl** builds, so expect a good bunch of dependencies: 

```text
ldd my-gtk-app      
                                                                                                     02:00:10
	linux-vdso.so.1 (0x00007ffe3d696000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f4bc812d000)
	libgtk-4.so.1 => /usr/lib/libgtk-4.so.1 (0x00007f4bc7800000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f4bc80c4000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f4bc807e000)
	libcairo-gobject.so.2 => /usr/lib/libcairo-gobject.so.2 (0x00007f4bc8073000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f4bc76ce000)
	libgraphene-1.0.so.0 => /usr/lib/libgraphene-1.0.so.0 (0x00007f4bc8052000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00007f4bc74f9000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007f4bc73ae000)
	libgcc_s.so.1 => /usr/lib/libgcc_s.so.1 (0x00007f4bc8032000)
	libc.so.6 => /usr/lib/libc.so.6 (0x00007f4bc71c7000)
	/lib64/ld-linux-x86-64.so.2 => /usr/lib64/ld-linux-x86-64.so.2 (0x00007f4bc825c000)
	libffi.so.8 => /usr/lib/libffi.so.8 (0x00007f4bc8027000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f4bc801e000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f4bc800e000)
	libharfbuzz.so.0 => /usr/lib/libharfbuzz.so.0 (0x00007f4bc70cc000)
	libfribidi.so.0 => /usr/lib/libfribidi.so.0 (0x00007f4bc7fee000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f4bc707d000)
	libepoxy.so.0 => /usr/lib/libepoxy.so.0 (0x00007f4bc6f49000)
	libm.so.6 => /usr/lib/libm.so.6 (0x00007f4bc6e61000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f4bc7fd8000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f4bc6d1e000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f4bc6d06000)
	libcloudproviders.so.0 => /usr/lib/libcloudproviders.so.0 (0x00007f4bc6cef000)
	libtracker-sparql-3.0.so.0 => /usr/lib/libtracker-sparql-3.0.so.0 (0x00007f4bc6c1e000)
	libpng16.so.16 => /usr/lib/libpng16.so.16 (0x00007f4bc6be5000)
	libtiff.so.6 => /usr/lib/libtiff.so.6 (0x00007f4bc6b4e000)
	libjpeg.so.8 => /usr/lib/libjpeg.so.8 (0x00007f4bc6acb000)
	libxkbcommon.so.0 => /usr/lib/libxkbcommon.so.0 (0x00007f4bc6a84000)
	libwayland-client.so.0 => /usr/lib/libwayland-client.so.0 (0x00007f4bc6a72000)
	libwayland-egl.so.1 => /usr/lib/libwayland-egl.so.1 (0x00007f4bc6a6d000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f4bc6a58000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f4bc6a4c000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f4bc6a47000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f4bc6a3f000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f4bc6a32000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f4bc6a2d000)
	libcairo-script-interpreter.so.2 => /usr/lib/libcairo-script-interpreter.so.2 (0x00007f4bc6a08000)
	libthai.so.0 => /usr/lib/libthai.so.0 (0x00007f4bc69fd000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f4bc69e3000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f4bc6906000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f4bc68f9000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f4bc68cc000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00007f4bc68bd000)
	libxcb-shm.so.0 => /usr/lib/libxcb-shm.so.0 (0x00007f4bc68b8000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f4bc680b000)
	libmount.so.1 => /usr/lib/libmount.so.1 (0x00007f4bc67c7000)
	libpcre2-8.so.0 => /usr/lib/libpcre2-8.so.0 (0x00007f4bc672a000)
	libgraphite2.so.3 => /usr/lib/libgraphite2.so.3 (0x00007f4bc6707000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f4bc66dc000)
	libjson-glib-1.0.so.0 => /usr/lib/libjson-glib-1.0.so.0 (0x00007f4bc66b1000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x00007f4bc6549000)
	libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x00007f4bc63f8000)
	libzstd.so.1 => /usr/lib/libzstd.so.1 (0x00007f4bc6325000)
	liblzma.so.5 => /usr/lib/liblzma.so.5 (0x00007f4bc62f2000)
	liblzo2.so.2 => /usr/lib/liblzo2.so.2 (0x00007f4bc62d1000)
	libdatrie.so.1 => /usr/lib/libdatrie.so.1 (0x00007f4bc62c8000)
	libbz2.so.1.0 => /usr/lib/libbz2.so.1.0 (0x00007f4bc62b3000)
	libbrotlidec.so.1 => /usr/lib/libbrotlidec.so.1 (0x00007f4bc62a5000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f4bc62a0000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f4bc6298000)
	libblkid.so.1 => /usr/lib/libblkid.so.1 (0x00007f4bc6260000)
	libicuuc.so.72 => /usr/lib/libicuuc.so.72 (0x00007f4bc6000000)
	libbrotlicommon.so.1 => /usr/lib/libbrotlicommon.so.1 (0x00007f4bc623b000)
	libicudata.so.72 => /usr/lib/libicudata.so.72 (0x00007f4bc4200000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f4bc3e00000)
```

Therefore, just go for simple builds:

```text
cargo build --release
```