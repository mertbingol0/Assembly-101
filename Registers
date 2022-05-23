# Assembly 101

Registerlar Nedir?

Registerler işlemci çalışması sırasında kullanılan değişkenlerdir. Bellekteki verilere ulaşmak Registerler işlemci çekirdeğindedir ve bu yüzden istenen işlemi hızlı bir şekilde işleme alabilmektedir. Sınırlı sayıda bulunurlar. Registerler genel amaçlı kullanılabilecekleri gibi özel görevler içinde kullanılabilir.

32 Bit Registers:
EAX
EBX
ECX
EDX
EBP
ESP
EIP
ESI
EDI
EFLAGS

16 Bit Registers:
AH AL
BH BL
CH CL
DH DL

BP
SP
SI
DI
CS
DS
SS
ES
FS
GS

Registerlerin Sınıflandırılmış Hali:

Data Registers = EAX,EBX,ECX,EDX,AX,BX,CX,DX,AH,AL,BH,BL,CH,CL,DH,DL
Pointer Registers = EBP,ESP,BP,SP
Index Registers = ESI,EDI,SI,DI	
Segment Registers = CS,DS,SS,ES,FS,GS

x86 İşlemcisi 8 bitlik bir işlemcidir. Bu nedenle EAX şeklindeki bir register 32 bittir, fakat bu registerin ilk 16 bitlik bölümü AX ile ifade edilir. Bu AX şeklindeki 16 bitlik bölüm ise kendi içinde ilk 8 bitlik bölüm AL, sonraki 8 bitlik bölüm AH olmak üzere alt bölümleri bulunur. Ben 4 bytelık bir veri depolamak istersem EAX,EBX gibi 32 bitlik; 2 byte bilgi depolamak istersem AX,BX gibi 16 bit; eger 1 byte bilgi depolamak istersem AH,AL,BH,BL registerlerini kullanabilirim.
AX,AH,AL registerleri EAX registerinin alt bölümleridir.
AX,AL,AH bir bütün olarak EAX'dir. Sadece byteları aynı değildir.

32 Bit Registers
EAX,EBX,ECX,EDX,EBP,ESP,ESI,EDI,EIP,EFLAGS

16 Bit Registers
AX,BX,CX,DX,BP,SP,SI,DI,CS,DS,SS,ES,FS,GS,IP,FLAGS

8 Bit Registers 
AH,AL,BH,BL,CH,CL,DH,DL

Şimdi bu Registerlarımızın ne olduklarını açıklayalım.
AX : Accumulator Register, Dört işlemlerde kullanılır.
BX : Base Register, Memory lokasyonlarında adres göstericisi olarak kullanılır, yani index registeri gibi kullanılabilir.
CX : Counter Register, Loop işlemlerinde sayaç olarak kullanılır, yani döngü kaç defa daha dönecek bunun sayısını tutar.
DX : Data Registeri, Donanım ile yapılan giriş çıkış işlemlerinde kullanılır.
