# Tab-Host

### Start
```bash
./tabHost /dev/ttyUSB0
TAB>
```
### Commands
#### TAB commands
- `common_ack [-v]`
- `common_nack [-v]`
- `common_debug [-v]`
- `common_data [-v]`
- `common_write_ext [Addr] [Data] [-v]`
    - Arguements:
        - Addr: 32 bit address (0xHHHHHHHH) to start writing the data
        - Data: Bytes to write to the external flash. The bytes can be caharacters, integers or hex
        - -v: Setting this will make the Tab command not print to the terminal
    - Examples:
        - `common_write_ext 0x00000000 0x01 0x02 0x03 0x04 0x05`
        - `common_write_ext 0x00001111 hello world`
        - `common_write_ext 0x00FFFFFF 10 255 200 133`

- `common_erase_sector_ext [Addr] [-v]`
    - Arguements:
        - Addr: 32 bit address (0xHHHHHHHH)that is the start of a sector to start erasing
        - -v: Setting this will make the Tab command not print to the terminal
    - Examples:
        - `common_erase_sector_ext 0x00000000`
        - `common_erase_sector_ext 0x00001000`
        - `common_erase_sector_ext 0x00FFF000`

- `common_read_ext [Addr] [Len] [-v]`
    - Arguements:
        - Addr: 32 bit address (0xHHHHHHHH) to start writing the data
        - Len: Number of bytes to read
        - -v: Setting this will make the Tab command not print to the terminal
    - Examples:
        - `common_read_ext 0x00000000 1`
        - `common_read_ext 0x00001111 77`
        - `common_read_ext 0x00FFFFFF 200`

- `bootloader_ack [-v]`
- `bootloader_nack [-v]`
- `bootloader_ping [-v]`
- `bootloader_erase [-v]`
- `bootloader_write_page [-v]`
- `bootloader_write_page_addr32 [-v]`
- `bootloader_jump [-v]`
- `bootloader_power [Mode] [-v]`
    - Arguements:
        - Mode: Power mode to enter
            - Run
            - Sleep
            - Low-power run
            - Low-power sleep
            - Stop 0
            - Stop 1
            - Stop 2
            - Standby
            - Shutdown
        - -v: Setting this will make the Tab command not print to the terminal
    - Examples:
        - `bootloader_power run`
        - `bootloader_power sleep`
        - `bootloader_power standby`

- `app_get_telem [-v]`
- `app_get_time [-v]`
- `app_set_time [-v]`
- `app_reboot [-v]`

- `write_file [File] [Addr] [-v]`
    - Arguements:
        - File: File to write to external flash
        - Addr: 32 bit address (0xHHHHHHHH) to start writing the file
        - -v: Setting this will make the Tab command not print to the terminal
    - Examples:
        - `write_file video.mp4 0x00000000`
        - `write_file test.txt 0x00001111`

- `erase_sectors [Addr] [Sectors] [-v]`
    - Arguements:
        - Addr: 32 bit address (0xHHHHHHHH) that is the start of a sector to start erasing
        - Sectors: Number of 4kb sectors to erase
        - -v: Setting this will make the Tab command not print to the terminal
    - Examples:
        - `erase_sectors 0x00001000 1`
        - `erase_sectors 0x00000000 1150`

- `read_file [Addr] [File] [-v]`
    - Arguements:
        - Addr: 32 bit address (0xHHHHHHHH) to start read
        - File: Filename to save read file
        - -v: Setting this will make the Tab command not print to the terminal
    - Examples:
        - `read_file 0x00001000 test.txt`
        - `read_file 0x00FFFFFF file -v`