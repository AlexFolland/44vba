# 44VBA

A GBA emulator for various platforms, including ESP32-S3, embedded linux, wasm, etc.

Originally forked from [https://github.com/libretro/vba-next](https://github.com/libretro/vba-next), then later forked from [https://github.com/44670/44vba](https://github.com/44670/44vba) to add fast-forward keyboard control.

# Building and deploying the WASM port on an Arch-based Linux distro on a user with bash as the shell

1. Install AUR package `emsdk`.
2. Install official Arch package `ninja`.
3. Run `sudo /usr/lib/emsdk/emsdk install latest` to install the latest Emscripten SDK.
4. Run `sudo /usr/lib/emsdk/emsdk activate latest` to activate the latest Emscripten SDK.
5. Run `source /usr/lib/emsdk/emsdk_env.sh` to load the Emscripten SDK environment.
6. Run `echo 'source "/usr/lib/emsdk/emsdk_env.sh"' >> $HOME/.bash_profile` to append loading of the Emscripten SDK environment to your bash profile so you can build later.
7. Navigate to your copy of this repository with the `cd` command.
8. Run `cd port-wasm` to navigate to the `port-wasm` directory.
9. Run `emcmake cmake -G Ninja . && ninja clean && ninja`.
10. Copy the following files to your HTTP server: `44gba.js`, `44gba.wasm`, `app.js`, `favicon.ico`, `icon.png`, `index.html`, `localforage.js`, `manifest.json`, `pake.min.js`, `ruffle.js`, `sw.js`.

Whenever you want to make a change and update, you can just run `emcmake cmake -G Ninja . && ninja clean && ninja`, then copy `44gba.js`, `44gba.wasm`, `app.js`, and any other files you've modified to the HTTP server.