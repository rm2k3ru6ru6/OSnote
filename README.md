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
開機磁區格式以nask組合語言編寫方式
```NASM
		DB		0xeb, 0x4e, 0x90
		DB		"HELLOIPL"		; ブートセクタの名前を自由に書いてよい（8バイト）
		DW		512				; 1セクタの大きさ（512にしなければいけない）
		DB		1				; クラスタの大きさ（1セクタにしなければいけない）
		DW		1				; FATがどこから始まるか（普通は1セクタ目からにする）
		DB		2				; FATの個数（2にしなければいけない）
		DW		224				; ルートディレクトリ領域の大きさ（普通は224エントリにする）
		DW		2880			; このドライブの大きさ（2880セクタにしなければいけない）
		DB		0xf0			; メディアのタイプ（0xf0にしなければいけない）
		DW		9				; FAT領域の長さ（9セクタにしなければいけない）
		DW		18				; 1トラックにいくつのセクタがあるか（18にしなければいけない）
		DW		2				; ヘッドの数（2にしなければいけない）
		DD		0				; パーティションを使ってないのでここは必ず0
		DD		2880			; このドライブ大きさをもう一度書く
		DB		0,0,0x29		; よくわからないけどこの値にしておくといいらしい
		DD		0xffffffff		; たぶんボリュームシリアル番号
		DB		"HELLO-OS   "	; ディスクの名前（11バイト）
		DB		"FAT12   "		; フォーマットの名前（8バイト）
		RESB	18				; とりあえず18バイトあけておく
```

nask指令
```
DB	直接在檔案裡寫入1個Byte (8 bit)
DW	直接在檔案裡寫入2個Byte (16 bit)
DW	直接在檔案裡寫入4個Byte (32 bit)
RESB	保留位元組，如「RESB 10」表示空出10個Byte
```

####Day 2
文字編輯器推薦使用[Notepad++](https://notepad-plus-plus.org/)。
nask指令
```
ORG	從記憶體何處開始讀入程式碼
JMP	跳躍至指定位址，如C的goto
MOV	資料代入，如「MOV AX,0」表示將0代入AX
```
