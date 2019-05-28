## Laboratory work III

[![Build Status](https://travis-ci.com/AndreevSemen/lab04.svg?branch=wp%2Flab)](https://travis-ci.com/AndreevSemen/lab04)
[![Build status](https://ci.appveyor.com/api/projects/status/f15qah26nrb99asd?svg=true)](https://ci.appveyor.com/project/AndreevSemen/lab04)

Данная лабораторная работа посвещена изучению систем автоматизации сборки проекта на примере **CMake**

```ShellSession
$ open https://cmake.org/
```

### Homework

## Задание:

Вы продолжаете проходить стажировку в "Formatter Inc." (см подробности).

В прошлый раз ваше задание заключалось в настройке автоматизированной системы CMake.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в прошлый раз. Настройте сборочные процедуры на различных платформах:

    используйте TravisCI для сборки на операционной системе Linux с использованием компиляторов gcc и clang;
    используйте AppVeyor для сборки на операционной системе Windows.

## Решение для TravisCI:

```
notifications:
  email: false

language: cpp

os:
  - linux

# интегрировать на двух разных компиляторах
compiler:
  - gcc
  - clang

# Using SOFT
addons:
  apt:
    sources:
      - ubuntu-toolchain-r-test
      - llvm-toolchain-precise-3.6
    packages:
      - g++-7
      - clang-3.6

# Target scripts
script:
  - cmake CMakeLists.txt
  - cmake --build .
```

## Решение для AppVeyor:


```
image: Visual Studio 2017


# Bыбраны две архитектуры для большего покрытия возможных ошибок
platform:
  - x64
  - x86

# Release mode
configuration:
  - Release

# Собираем на Microsoft Visual Studio 2017
environment:
  matrix:
    - TOOLCHAIN: msvc17

# Target scripts
build_script:
  - cmake CMakeLists.txt
  - cmake --build .
```


## Links
- [Основы сборки проектов на С/C++ при помощи CMake](https://eax.me/cmake/)
- [CMake Tutorial](http://neerc.ifmo.ru/wiki/index.php?title=CMake_Tutorial)
- [C++ Tutorial - make & CMake](https://www.bogotobogo.com/cplusplus/make.php)
- [Autotools](http://www.gnu.org/software/automake/manual/html_node/Autotools-Introduction.html)
- [CMake](https://cgold.readthedocs.io/en/latest/index.html)

```
Copyright (c) 2015-2019 The ISC Authors
```
