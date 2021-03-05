<div align="center">

# Emacs native-comp Windows 10 Builds

Personal (*unofficial*) builds of the [Emacs native-comp branch](https://www.emacswiki.org/emacs/GccEmacs) for Windows using [MSYS2](https://www.msys2.org/).

</div>

## Instructions

```sh
./packages.sh
pacman -Scc
git clone https://git.savannah.gnu.org/git/emacs.git
cd emacs
git checkout feature/native-comp && git pull --ff-only

./autogen.sh
./configure --with-native-compilation --with-gnutls --without-pop --without-make-info
# --with-jpeg --with-png --with-rsvg --with-xml2 --without-imagemagick
make -j4 # -j8

make install prefix=~/emacs-build
cp /mingw64/bin/*.dll ~/emacs-bin/bin/

# rebuild
git clean -dxf
```

## Thanks

- https://www.reddit.com/r/emacs/comments/lxabxs/outline_of_how_to_compile_emacs28_with_nativecomp/
- https://gist.github.com/nauhygon/f3b44f51b34e89bc54f8
- https://sourceforge.net/p/emacsbinw64/wiki/Build%20guideline%20for%20MSYS2-MinGW-w64%20system/
