# LibertyAdvanceRecomp

A static recompilation project for Grand Theft Auto Advance (GBA), aiming to convert the original binary into native executable code for PC and mobile platforms.

---

## 📌 Features

- **Static Recompilation:** Converts GBA ARM7TDMI assembly into native C++ code using [gbarecomp](https://github.com/mstan/gbarecomp).
- **Cross-Platform:** Native builds for Linux, Windows, and Android (via Termux).
- **Fast & Lightweight:** Direct native execution using SDL2 for windowing, inputs, and audio rendering.

---

## 🛠️ Prerequisites & Dependencies

### Linux (Ubuntu / Debian)
```bash
sudo apt update
sudo apt install git cmake ninja-build build-essential libsdl2-dev

Android (Termux)
pkg install x11-repo -y
pkg update -y
pkg install git cmake ninja clang make sdl2 -y

🚀 Building & Running
1. Clone the Repository
git clone [https://github.com/luispolis124/LibertyAdvanceRecomp.git](https://github.com/luispolis124/LibertyAdvanceRecomp.git)
cd LibertyAdvanceRecomp

2. Build the Recompiler Tool
mkdir -p tools
cd tools
git clone [https://github.com/mstan/gbarecomp.git](https://github.com/mstan/gbarecomp.git)
cd gbarecomp
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
cd ../..

3. Provide the ROM & Generate Recompiled Code
Place your legally acquired gta_advance.gba ROM in the project root directory, then run:
./tools/gbarecomp/build/gbarecomp config/gta_advance.toml

4. Build the Native Executable
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build

📁 Repository Structure
LibertyAdvanceRecomp/
├── CMakeLists.txt
├── README.md
├── .gitignore
├── config/
│   └── gta_advance.toml   # Target ROM address map & memory sections
├── src/
│   ├── main.cpp           # Entry point and SDL2 platform layer
│   └── gba_runtime.cpp    # Display, input, and audio register emulation
└── tools/
    └── gbarecomp/         # Submodule / Static recompiler binary

📜 License
This project is open-source and intended solely for educational, reverse-engineering, and static recompilation research. All original game assets and code rights belong to their respective owners.
