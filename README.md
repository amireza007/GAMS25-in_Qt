# GAMS25-in_Qt

- As you might know, the only "stable" version of GAMS currently available with full solvers support is GAMS 25.1 \*\*for free\*\*, and hence _we are stuck with a very old (probably around 2017 verison) of GAMS_.
- For integration of GAMS inside a QT, you need:
  - visual studio 17 2022 with all c++ sdk and MSVC sdks (The most crucial of all is **`cl.exe`**, which is a command line based MS C++ needed for `CMAKE_COMPILER_CXX` variable)
  - QT 6.7.3
- After cloning this repo, You need to set `CMAKE_GENERATOR` to `Visual Studio 17 2022` and unset `CMAKE_PROJECT_INCLUDE_BEFORE`. (alternatively you could set `-DCMAKE_PROJECT_INCLUDE_BEFORE=""` in Qt's `preferences->kits->The-kit->CMake Configuration`)
- Then build and enjoy coding in QT! (For now :))