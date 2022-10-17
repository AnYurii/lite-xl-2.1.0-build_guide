Its guide how to build lite-xl 2.1.0
I created that guide because main guide how to build includeing some mistakes and dont includeing all needed information. I also had some problems with luaconf.h, which i had fixed.

## Building

needed libraries and programs: libfreetype6-dev, libsdl2-dev, lua5.4, liblua5.4-dev, libagg2-dev, meson, git
if you using debian, you can use that command:
```sh
sudo apt install libfreetype6-dev libsdl2-dev lua5.4 liblua5.4-dev libagg2-dev meson git
```
on other distros names of libraries can be changed


download and copy additional files
```sh
git clone https://codeberg.org/Yurii/lite-xl-2.1.0-build_guide.git && cd lite-xl-2.1.0-build_guide/
sudo cp files/lua5.4.pc /usr/lib/pkgconfig/ && sudo cp files/include/* /usr/include/
cd ..

```

next download source code using that command: 
```sh
git clone https://github.com/lite-xl/lite-xl.git && cd lite-xl/
```

now build lite-xl using that command:
```sh
meson setup --buildtype=release --prefix /usr build
meson compile -C build
DESTDIR="$(pwd)/lite-xl" meson install -C build
```
and copy builded files:
```sh
sudo cp --recursive lite-xl/usr/* /usr/
```
it will copy binary lite-xl file to /usr/bin, and other needed files to /usr/share

now lite-xl installed and redy for using.
