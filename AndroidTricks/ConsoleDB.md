
# Generar el archvio .db desde consola

Se debe de localizar el archvio raiz del proyecto

```console
C:\>cd C:\Users\LuisVillalobos\AppData\Local\Android\Sdk\platform-tools
C:\Users\LuisVillalobos\AppData\Local\Android\Sdk\platform-tools>adb devices
C:\Users\LuisVillalobos\AppData\Local\Android\Sdk\platform-tools>adb -e shell
root@vbox86p:/ # su root
root@vbox86p:/ # cd data/data/com.desarollo.luisvillalobos.sqlcipherexample/databases
root@vbox86p:/data/data/com.desarollo.luisvillalobos.sqlcipherexample/databases # cp Example.db /sdcard/DCIM
root@vbox86p:/data/data/com.desarollo.luisvillalobos.sqlcipherexample/databases # exit
root@vbox86p:/ # exit
C:\Users\LuisVillalobos\AppData\Local\Android\Sdk\platform-tools>adb pull /sdcard/DCIM/Example.db
adb pull /data/data/com.desarollo.luisvillalobos.sqlcipherexample/databases/Example.db

adb shell "run-as com.desarollo.luisvillalobos.sqlcipherexample chmod 666 /data/data/com.desarollo.luisvillalobos.sqlcipherexample/databases/Example.db"
adb exec-out run-as com.desarollo.luisvillalobos.sqlcipherexample cat databases/Example.db > test.db
adb shell "run-as com.desarollo.luisvillalobos.sqlcipherexample chmod 600 /data/data/com.desarollo.luisvillalobos.sqlcipherexample/databases/Example.db"
```
 
 Ya esta el archivo .bd en la direccion de la carpte
https://www.androidauthority.com/about-android-debug-bridge-adb-21510/  
https://www.androidauthority.com/how-to-install-android-sdk-software-development-kit-21137/