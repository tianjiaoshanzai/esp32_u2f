| Supported Targets | ESP32-S2 | ESP32-S3 |
| ----------------- | -------- | -------- |

# ESP32 U2F Security Key.

Turns your cheap ESP32 U2F token.

### Hardware Required

Any ESP board that have USB-OTG supported.

### Flash Example

> **WARNING**
> using erase_flash will lose all stored keys

```
# Erase first 1MB size
esptool erase_region 0x0 0x100000
```

Flash binaries:

esp32s2
bootloader address is 0x1000

```
esptool --chip esp32s2  write_flash --flash_mode dio --flash_size 2MB --flash_freq 80m 0x1000 bootloader/bootloader.bin 0x8000 partition_table/partition-table.bin 0x10000 esp32_u2f.bin
```

esp32s3
bootloader address is 0x0

```
esptool --chip esp32s3  write_flash --flash_mode dio --flash_size 2MB --flash_freq 80m 0x0 bootloader/bootloader.bin 0x8000 partition_table/partition-table.bin 0x10000 esp32_u2f.bin

```

### 用法

1 、没 esp32 开发板的话淘宝 10 元买个 s2 mini 开发板 

2 、去 https://github.com/jocover/esp32_u2f/releases 发布页下载 esp32s2 版的固件 

3 、去 https://github.com/espressif/esptool/releases 下载刷机工具 

4 、按板子上按钮和重启键进入刷机模式 (长按按钮->短按reset松开->松开按钮)

5 、输入 esptool erase_flash 先清除 flash 

6 、然后输入 esptool --chip esp32s2 write_flash --flash_mode dio --flash_size 2MB --flash_freq 80m 0x1000 bootloader/bootloader.bin 0x8000 partition_table/partition-table.bin 0x10000 esp32_u2f.bin 刷固件 

7 、完成 

### Tools

[espressif esptool](https://github.com/espressif/esptool/releases)

### License

[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html)
