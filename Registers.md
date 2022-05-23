# Assembly 101

Registerlar Nedir?

Registerlar işlemci çalışması sırasında kullanılan değişkenlerdir. Bellekteki verilere ulaşmak Registerler işlemci çekirdeğindedir ve bu yüzden istenen işlemi hızlı bir şekilde işleme alabilmektedir. Sınırlı sayıda bulunurlar. Registerler genel amaçlı kullanılabilecekleri gibi özel görevler içinde kullanılabilir.

32 Bit Registers:
EAX,EBX,ECX,EDX,EBP,ESP,ESI,EDI,EIP,EFLAGS

16 Bit Registers:
AH AL
BH BL
CH CL
DH DL

BP,SP,SI,DI,CS,DS,SS,ES,FS,GS

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
CX : Counter Register, Loop işlemlerinde sayaç olarak kullanılır, döngü kaç defa daha dönecek bunun sayısını tutar.
DX : Data Register, Donanım ile yapılan giriş çıkış işlemlerinde kullanılır.
CS : Code Segment Register, Segmentler bellekte bir alt bölümü işaret ederler. En önemli segment kod segmentdir. İçinde yazdığımız programın komutları yer alır. Hem programcı hemde kullanılan işletim sistemi kod segmentteki komutlar üzerine başka dataların yazılmayacağının garantisini almalıdır. Aksi taktirde programımız garip hatalar verir ve kitlenir. Programların sağlıklı çalışmaları için Code Segment içeriği en önemli noktadır.
DS : Data Segment Register, Programımızı yazarken kullandığımız değişkenler, arraylar ayrıca çalışma anında oluşturulan değişken tiplerinin tamamı bu segment altında tutulur.
SS : Stack Segment Register, Stack özel bir data segment tipidir. Alt programlardan, Fonksiyonlardan kodlar yürütülmeden önce gerekli değişkenler bu segmente sadece bu amaçla kullanılan bir Assembly komutu ile alınırlar. Daha sonra çağırma (CALL) işlemi yapılır. Önemli olan çalışma prensibini anlamaktır. Data segmentlerde olduğu gibi istenilen adresden veri çekebilmektedir. Farkı ise stack'e yollanan son verinin çağırılma esnasında ilk olarak geri dönmesidir. Son giren-ilk çıkar mantığı. Veriler stackin sonundan başına doğru alınırlar.(Bir kutuya 10 tane kitap koyduğunuzu düşünün. bu kitaplardan hangisini ilk koyarsanız en son onu çıkartacaksınız fakat hangisini en son koyarsanız ilk onu çıkartacaksınız). Stack'e son yollanan veri "SP" isimli Stack Pointerla işaret edilir.
ES : Extra Data Segment Register, Data segment ile aynı özelliklere sahiptir. Özel olarak bu segmenti kullanan birkaç komut bulunmaktadır.
FS,GS : Bu segment registerleri ihtiyaç olduğu zaman kullanılmaktadır. Aslında ek olarak kullanılan Data Segment Registerleridir.
BP : Base Pointer, Stack segmentin başlangıç noktasını gösterir. Yani genelde içeriği sıfırdır.
SP : Stack Pointer, Stack segment içine gönderilmiş olan son değerin adresini gösterir. Stack içine veriler yollandıkça değeri azalır çünkü veri segmentin sonundan başına doğru alınır. Veriler stackdan çekildikçe değeri artar, böylece eski verileri gösterir.
Not: BP ve SP aslında SI ve DI gibi segmentler içindeki verinin adresini gösterirler. Stack Segmentin özel bir çalışma şekli olduğu için bu Pointer registerleri özel olarak sadece Stack Segmentin sağlıklı çalışması için görev yapmaktadır.
SI : Source Index, Data segment ve/veya istenirse başına küçük bir tanımlama eklenerek diğer data segmentlerdeki verileri de göstermek için kullanılan bir index (işaretçi) registerdir.
DI : Destination Index, SI ile tamamen aynı özelliklere sahiptir. Fakat SI ve DI bazı string komutları tarafından kaynak ve hedef işaretçisi olarak da kullanılır.
IP : Bir pointer registerdir. Çok özel bir pointer'dır. Code Segment içinde işlenecek bir sonraki komutun yerini işaret eder. Yaptığınız işten emin olmadan üzerinde oynama yapmamalısınız.(Buffer Owerflow zafiyetlerinde bu register'a odaklanılır.)
FLAGS : 32 bitlik yine çok özel bir işlevi olan registerdir. Bu registerin içerisindeki bitler çok önemlidir. Bazı bitler anlamsızdır, diğerleri ise daha önce işlenen komutların sonuçları ile ilgili bilgiler verir. Örneğin CMP komutu ile iki sayı karşılaştırılır ise sayıların eşit olma veya birinin diğerine göre büyük olması bu register içindeki bazı bitleri 1 (set) veya 0 (reset) durumuna getirecektir. Daha sonra kullanılacak bir dallanma komutu ile bu flaglar kontrol edilerek sonuca göre belirli adreslere dallanmalar yapılır. Bazı komutlar işleyişleri sırasında bu registeri gizli olarak kullanır.
Aşağıda hangi Segmentlerin hangi pointer registerlar ile kullanılacakları gösterilmektedir:

CS:IP
DS:SI
DS:DI 
SS:BP 
SS:SP
