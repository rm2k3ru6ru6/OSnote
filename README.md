####Day 1
使用二進位編輯器(Binary Editor)編寫機器碼，將[helloos.img](projects/01_day/helloos0/helloos.img)硬生生的寫出來。<br>
使用[qemu](tolset/z_tools/qemu)虛擬出一台PC，執行helloos。<br>
使用[nask](tolset/z_tools/nask.exe)組合語言編寫[helloos.nas](projects/01_day/helloos1/helloos.nas)，並組譯成機器碼:<br>
```bat
..\z_tools\nask.exe helloos.nas helloos.img
```

