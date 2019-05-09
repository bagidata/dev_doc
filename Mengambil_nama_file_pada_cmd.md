Misal nama file 'c:\tmp\filecmd.bat' :

Anda dapat mengambil nama file juga mengambil full path tergantung bagaimana anda menempatkan huruf diantara `%~` dan `0` 

Berikut huruf yg diperlukan:

```
d unutk drive
p untuk path
n untuk nama file
x untuk extension
f untuk full path

contoh 1 :
`%~nx0`

hasilnya :

`filecmd.bat`

contoh 2:

`%~n0`

hasil :

`filecmd`

contoh 3 :

`%~dpnx0`

hasil :

`c:\tmp\filecmd.bat`

contoh 4 :

`%~xnpd0`

hasil :

`c:\tmp\filecmd.bat`

[Sumber](https://stackoverflow.com/questions/8797983/can-a-windows-batch-file-determine-its-own-file-name)
