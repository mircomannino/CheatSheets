## ESP32 cheat sheet

### Board info and links
* Model: ESP32 -S3 -DevKitC-1-N8R8 WROOM-1
* [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf)
* [ESP-IDF Documentation](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html)

### Activate ESP-IDF env 
Add the following lines to your `.bashrc` file:
```bash 
ESP_PATH=<path/to/esp/folder>
alias get_idf='. $ESP_PATH/esp-idf/export.sh'
```
Run the following command to activate the environment: 
```bash 
user@machine:/$ get_idf 
```

### ESP-IDF commands
|                COMANND                |                DESCRIPTION               |
|:-------------------------------------:|:----------------------------------------:|
|    ```idf.py create-project <name>``` | Create new project called "name"         |
|    ```idf.py build```                 | Build the current project                |
|    ```idf.py set-target <target> ```  | Change target board (es. esp32, esp32s3) |
|    ```idf.py -p <port> flash  ```     | Flash on port "port"                     |
|    ```idf.py monitor ```              | Open serial monitor (```Ctrl + ]``` to exit)|

---

### ESP-IDF path configuration in VSCode
Assuming to have __esp-idf__ installed in default path (~/esp)

In order to include correctly esp-idf paths in your project modify the 
``` c_cpp_properties.json ``` file (```Ctrl + Shift + p``` and search for 
_"C/C++: Edit Configurations (JSON)"_). 
The following lines should be included in your ```c_cpp_properties.json ```:
``` json
{
    "configurations": [
        {
            "name": "ESP-IDF",
            "includePath": [
                "${default}",
                "${workspaceFolder}/**"
            ],
            "browse": {
                "path": [
                    "${default}",
                    "${workspaceFolder}"
                ],
                "limitSymbolsToIncludedHeaders": false
            },
            "cStandard": "c17",
            "cppStandard": "c++17",
            "compileCommands": "${workspaceFolder}/build/compile_commands.json"
        }
    ],
    "version": 4
}
```
__NOTE__: You have to build at least once before having include paths 
(and cross links) work correctly.
