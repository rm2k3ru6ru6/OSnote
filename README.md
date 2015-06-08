####Day 1
使用二進位編輯器(Binary Editor)編寫機器碼，將[helloos.img](projects/01_day/helloos0/helloos.img)硬生生的寫出來。<br>
使用[qemu](tolset/z_tools/qemu)虛擬出一台PC，模擬電源啟動後自動載入並執行helloos。<br>
```bat
copy helloos.img ..\z_tools\qemu\fdimage0.bin
..\z_tools\make.exe	-C ../z_tools/qemu
```
使用[nask](tolset/z_tools/nask.exe)組合語言編寫[helloos.nas](projects/01_day/helloos1/helloos.nas)。
將helloos.nas組譯成機器碼。<br>
```bat
..\z_tools\nask.exe helloos.nas helloos.img
```
nask組合語言指令
```
DB  (Data Byte)直接在檔案裡寫入1個Byte (8 bit)
DW  (Data Word)直接在檔案裡寫入2個Byte (16 bit)
DW  (Data Double-Word)直接在檔案裡寫入4個Byte (32 bit)
```

