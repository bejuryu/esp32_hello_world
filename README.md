# ESP32-IDF Hello World : CLion 예제

[https://github.com/masoncj/esp32-examples](https://github.com/masoncj/esp32-examples) 참조.

## Requirements
- [ESP32 toolchain](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html#setup-toolchain)
- [ESP32-IDF](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html#get-esp-idf)
- Python2
- 환경변수 설정

### Python 이슈

 ESP32를 flash, monitor 하기위해 pyserial을 사용하는데 ESP-IDF에 기본포함된 pyserial 라이브러리가 python2 용이라 python3 환경에서 사용시 호환성 에러가 발생.
Python3 환경이라면, virtualenv등을 이용하여 Python2를 사용하도록 설정.

### 환경변수 설정
- esp32 toolchain 경로 설정
- IDF_PATH 경로 설정
- **추가** ESP32_ROOT 경로 설정 : ESP32-IDF가 설치된 루트경로 설정

IDF_PATH, PATH 의 졍우 ESP32 공식 문서에 나오는 대로 설정을 따라하면되고, ESP32_ROOT는 CMake 환경에서 include 경로를 찾기위한 환경변수 지정

```bash
export IDF_PATH="$HOME/esp/esp-idf"
export PATH="$PATH:$HOME/esp/xtensa-esp32-elf/bin"
export ESP32_ROOT="$HOME/esp/xtensa-esp32-elf"
```

## 주의사항

- Clion 환경에서 소스에디팅을 하기위한 설정이므로 flash, debug 등 다른 작업은 동작하지 않음
- 기본 문서대로 make, make flush, make monitor를 이용한 개발 진행 필요