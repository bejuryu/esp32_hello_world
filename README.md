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

IDF_PATH, PATH 의 졍우 ESP32 공식 문서에 나오는 대로 설정을 따라한다.

```bash
export IDF_PATH="$HOME/esp/esp-idf"
export PATH="$PATH:$HOME/esp/xtensa-esp32-elf/bin"
```


### environments.txt 파일 수정
environments.default.txt 파일을 environments.txt로 복사 한 후 ESP32_ROOT, IDF_PATH 값을 개인 환경에 맞게 수정.

## 주의사항

- Clion 환경에서 소스에디팅을 하기위한 설정이므로 flash, debug 등 다른 작업은 동작하지 않음
- 기본 문서대로 make, make flush, make monitor를 이용한 개발 진행 필요

### For Windows

Aliexpress에서 구매한 ESP32 모듈이고 COM 포트가 **Silicon Labs CP210x USB** 으로 잡히는데 flash가 동작하지 않는다면.
[https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers) 에서 드라이버를 설치 한 후 다시 시도해 본다 . 