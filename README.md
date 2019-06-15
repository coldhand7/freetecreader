# freetecreader
Dies ist eine Quelloffene Lesesoftware für den [FreeTec NC7004 "USB-Temperatur- &amp; Luftfeuchtigkeits-Datenlogger V2"](http://www.free-tec.de/USB-Temperatur-NC-7004-919.shtml) von [Pearl](https://www.pearl.de/a-NC7004-3044.shtml).

Die offizielle Software für den NC7004 heißt "DataLogger3.3". Die Software verwendet eine Variante der "EasyWeather" Bibliothek.
Der NC7004 ist allerdings nicht protokollkompatibel mit den [populären WH1080 Wetterstationen](http://www.weewx.com/hwcmp.html).
Hilfreich war [dieses Blog](https://baublog.ozerov.de/2011/12/software-fuer-meine-wetterstation-wh1080) mit Hinweis auf das Projekt [weatherpoller](https://code.google.com/archive/p/weatherpoller) mit dem Verweis auf [Jim Easterbrook's Weather station memory map](http://www.jim-easterbrook.me.uk/weather/mm).

Getestet unter Linux mit Python 3.6.8 und hidapi 0.2.1.  
Bitte beachten: Diese Software funktioniert zwar für das mir vorliegende Gerät, ich garantiere aber in keiner Weise für Zuverlässigkeit oder Korrektheit der Daten.

USB-Permission
--------------
Um die Berechtigungen für den USB-Logger korrekt zu setzen, muss eine udev Regel eingerichtet werden:
- Kopieren von https://github.com/coldhand7/freetecreader/blob/master/99-hid_freetec_nc_7004.rules nach /etc/udev/rules.d/

Prüfung, ob das USB Gerät erkannt wurde:
- `dmesg` -> idVendor=10c4, idProduct=8468
- `sudo lsusb -v` -> Cygnal Integrated Products, Inc.

Achtung! hidapi nutzt intern unterschiedliche Libraries, je nach dem welche verfügbar ist (hidapi-libusb', 'hidapi-hidraw', 'hidapi). Im Detail gibt es dabei Unterschiede.

Ein paar hilfreiche Seiten bei Berechtigung/Verbindungsproblemen:
- [/dev/hidraw: read permissions](https://unix.stackexchange.com/questions/85379/dev-hidraw-read-permissions)
- [Permissions on HID device. Why is my udev rule being ignored?](https://stackoverflow.com/questions/38210022/permissions-on-hid-device-why-is-my-udev-rule-being-ignored)
- [HIDAPI hid_open_path() how to determine which path to use](https://stackoverflow.com/questions/38867444/hidapi-hid-open-path-how-to-determine-which-path-to-use)
- [Using Python hidapi to open device with multiple usages](https://stackoverflow.com/questions/38448312/using-python-hidapi-to-open-device-with-multiple-usages)
- [pyhidapi is a Python binding for the hidapi library.](https://github.com/awelkie/pyhidapi)