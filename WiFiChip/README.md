A repo demonstrating the WiFi capabilities of the IRIS board.

## Installation
Follow: https://docs.zephyrproject.org/latest/develop/getting_started/index.html

Add this line to ~/.bashrc:

```bash
export ZEPHYR_BASE=~/zephyrproject/zephyr
```

### VSCode
Follow: https://docs.zephyrproject.org/latest/develop/tools/vscode.html

For automatic source of the zephyr venv, do the following:
1. crtl + shift + P
2. Type Python: Select Interpreter
3. Enter ~/zephyrproject/.venv/bin/python

Add a folder secret to modules/udp_socket_demo with makros:

```C
#define BITCRAZE_SSID "my_ssid"
#define BITCRAZE_PASSWORD "my_password"
```

## Building
```bash
west build -p auto -b ubx_evk_iris_w1@fidelix .
```

## Flashing
```bash
west flash
```

## Debugging
```bash
west attatch
```

