[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/7TXVPuTD)

# 1. - Why we need to use OOP ? Some major OOP languages ?

Object Oriented programlama bir yazılım paradigmasıdır ve kendi yapısında bulunan dinamikler ile birlikte gerçek hayatta karşılaşılan problemlerin daha doğal bir şekilde kodlanabilmesine olanak sağlar.

Bunu kodun yapısını tanımlanan sınıflar üzerine kurarak sağlar. Encapsulation ile dataların korunmasını, inheritence ile objeler arasında ilişkiler kurulmasını ve gerektiğinde polymorphism ile de bu ilişkilerin özelleştirilmesini sağlar.

### Sağladığı bazı esneklikler.

1. Objeler üzerine kurulu bir yapıda bir sınıf başka bir sınıfın özelliklerini miras almasıyla ve kendininmiş gibi kullanabilmesiyle birlikte yazılımcının kod tekrarı yapmamasını ve daha temiz bir yapı kurmasına yardımcı olur.

2. Encapsulation sayesinde yazılımcı kullanılacak dataların nereden erişilebileceğini kontrol etmesine izin verir ve bu yüzden oluşabilecek hataların en başından önüne geçmesine yardımcı olur.

3. Abstraction ile araya bir perde çekerek yazılımcının implementation detaillerdan kullanımı soyutlayabilmesini sağlar. Bu soyutlamayla birlikte tek yerden kod değişimiyle bir metodun kontrol edilebilmesini sağlar.

Object Oriented programming için designlanmış programlama dillerine örnekler Java, C++, C# verebiliriz.

# 2. – Interface vs Abstract class ?

Javada abstraction soyutlama dediğimiz kavramın sağlanması bu yapılar ile sağlanır. Sistemin detaylarından arındılarak bu detayların öteki katmanlardan soyutlaştırılmasını sağlar.

### Interface

Kullanım amacı farklı sınıflar arasında ortak bir özelliği tanımlamak ve hepsinin bunu uygulaması gerektiğini belirtmektir. Bu şekilde soyutlamayı tam anlamıyla sağlar.

Bunu bir class'ın implemente etmesi gereken metod tanımlarını içine alarak yapar. Nasıl implemente edileceği interfacenin kullanıldığı class içerisinde gerçekleşir.

Çoklu kalıtım yapılmasını destekler yani bir class birden fazla interfaceyi implemente edebilir.

### Abstract Class

Kullanım amacı ortak bir temel sınıf oluşturarak bu classı extend eden classlar ile kendilerine göre uyarlamaları yapmasını sağlamaktır. Alt sınıflar bu temel sınıfın metod implementasyonlarını kullanabilir.

Metodlar abstract veya somut olabilir. Metod implementasyonlarını da içerebildiği için bir class birden fazla abstract classı extend edemez bunun nedeni farklı abstract classlarda aynı metod isimleri olması durumunda extend edilen sınıfta hangi metodun kullanılacağının bilinememesidir.

##İkisinin farkları

1. Interface: sadece metod imzalarını içerebilirken Abstract class: Hem abstract metodları hem de somut metodları içerebilir.

2. Interface: bir sınıf birden fazla interfaceyi implemente edebilir. Abstract class: Bir sınıf sadece bir abstract classı extend edebilir.

3. Interface içerisinde tanımlanan variable sadece public static final olabilirken abstract class içerisindeki variablelar herhangi bir erişim belirleyiciye sahip olabilir.

# 3. - Why wee need equals and hashcode? When to override?

## equals()

Javada iki objenin karşılaştırılması ve bu duruma göre işlemlerin devam edilebilmesinde kullanılır. Genel olarak equals metodu iki objenin hangi durumda birbirine eşit sayılmasını gerektiğini tanımlar. Bu karşılaştırmayı yapmak için equals() metoduna ihtiyaç duyarız.

### Ne zaman override edilmeli?

equals() metodu override edilmediğinde Java Object Classında bulunan objelerin referanslarını karşılaştırarak dönecek şekilde bir karşılaştırma yapar. Fakat biz iki objemizi içinde bulunan id veya başka variablelerine göre karşılaştırmak isteyebiliriz. Bu durumda equals() metodunu override ederek istediğimiz özelliklerine göre karşılaştırarak bu objelerin karşılaştırılmasını sağlarız.

## hashCode()

Bir obje için integer bir değer üreterek HashMap ve HashSet gibi collectionlarda karşılaştırma yapılmasında kullanılır.Default olarak equals() metodunda olduğu gibi objenin memory referansından oluşturulur.

### Ne zaman override Edilmeli?

HashSet ve HashMap de bu objelerin doğru şekilde karşılaştırılması gerekir. Eğer equals() metodu override edilip hashCode() metodu override edilmezse iki obje equals() ile karşılaştırıldığında aynı objeler olarak gözükmesine rağmen HashSet veya HashMap de farklı objeler olarak gözükecektir. Bu yüzden iki objeyi farklı bi identity vererek karşılaştırmak istiyorsak equals() metodunu override ederiz. equals() true olarak dönen iki objenin de bir problem çıkarmaması için hashCode() larının aynı dönmesi gerektiğinden hashCode() metodu da hash kullanılan collectionlarda doğru çalışması için override edilmelidir.

# 4- Diamond problem in Java ? How to fix it?

Elmas problemi object oriented paradigmasının kullanıldığı programlama dillerinde çoklu kalıtım yapıldığında karşılaşılan bir durumdur. Bir sınıfın kalıtım olarak aldığı sınıflarda ortak bir metod tanımı olduğunda ortaya çıkar. Java' da sınıflarda bu durum bir class'ın birden fazla classı miras alması mümkün olmadığı için karşılaşılmaz diye düşünülebilir fakat Java 8den sonra interfacelerde de default olarak metod tanımı koyulabilmesi geldiği için diamond problem ile Javada da karşılaşılabilir.

### Çözüm Yöntemleri

Ortak default metod tanımlarının olduğu metod interfacelerin kullanıldığı sınıfta override edilerek çözülebilir.

Eğer interfacelerin default tanımlamaları kullanılmak istiyorsa da super kullanılarak bu default metodlara da erişilebilir.

# 5- Why we need Garbagge Collector ? How does it run?

C gibi dillerde memoryde kullanılacak alanlar yazılımcı tarafından üretilir ve bu alana ihtiyaç kalınmadığında ise memorynin bu kısım serbest bırakılır. Bu da kontrol edilmesi zor bir durumdur. Daha sonra serbest bırakılmayan memory alanları programın bir süre sonunda kullandığı belleğin artmasına ve programın hata vermesine sebep olabilir. Java da ise bunun gibi durumların olasılığının azaltılması için Garbage Collector adında bir mekanizma işlem görmektedir. Bu mekanizma eğer bir nesneye hiçbir referans yoksa bu nesnenin çöp olduğunu belirler.

Bu işlem sonrasında JCM tarafından tetiklenerek bu nesnelerin heapte alan kaplamamasını sağlamak için kaldırılmasını sağlar.

# 6 – Java ‘static’ keyword usage ?

Static kelimesi javada class seviyesinde variablelar ve metodlar tanımlanması için kullanılır. Static olmayan değerler için bir classın objesi oluşturulup bu obje için özel olarak oluşturulurken static değerler o classın bütün objeleri için ortak bir şekilde oluşturulur. Statik değişkenler sınıf belleğe yüklenirken oluşturulur ve program kapanana kadar tüm nesneler tarafından paylaşılır.

### Kullanım türleri

- Static Variable: Kullanıldığı sınıftan oluşturulan tüm nesneler tarafından ortak olarak kullanılır. Hepsi için tek bir bellek alanı kullanılır.

- Static Metod: Nesneden bağımsız olarak Classİsmi.metodİsmi şeklinde çağırılabilen metodlardır. Class içinde tanımlı olan static olmayan değişkenlere erişimleri objeden bağmsız oldukları için yoktur.

- Static Blok: Sınıf ilk yüklendiğinde çalışacak özel tanımlanmış kod bloklarıdır.

# 7-Immutability means ? Where, How and Why to use it ?

Javada immutable nesneler nasıl oluşturulduysa hep öyle kalan nesnelerdir. Statelerini bir kere belirlersiniz ve hiçbir şey o nesnenin durumunu değiştiremez. Eğer bir değişiklik yapmak isterseniz farklı referanslı yeni bir nesne oluşturulur.

## Ne zaman kullanılırlar?

Bir objeye birden fazla thread aynı anda kullanıyor ve değişiklik yapabiliyor ise bu durumda kaydedilen ve okunan değerler arasında threadler arasında tutarızlıklar görünmeye başlayabilir.

Immutable bir nesnenin durumu değiştirilemeyeceği için bu tutarsızlık ihtimali ortadan kalkar.

## Nasıl Oluşturulurlar?

Sınıf final olarak tanımlanır. İçindeki değişkenler private final tanımlanır ve herhangi bir setter metodu kullanılmaz. Bu şekilde o objede değişiklik yapılması önlenir.

## Neden kullanılırlar?

Immutable nesneler sadece bir durumda olabileceği için sabit bir yapıdadır ve güvenilirdirler.

Yeni oluşturulan birbiriyle aynı durumu tutan değerler için bellekte yeni bir yer tutulması gerekmez. Aynı bellek alanı kullanılabilir.

# 8- Composition and Aggregation means and differences ?

Composition ve aggregation iki sınıf arasındaki has-a ilişkisini ifade eder. Ama ilişki kurulan sınıfların birbirlerine bağımlılığına göre birbirlerinden ayrılan kavramlardır.

## Composition

Bağımlı nesnenin sadece bağlı olduğu nesne ile birlikte var olduğu bağlılık türüdür. Burada has-a ilişkisi ile tutulan nesne bu sınıfın içerisinde oluşturulur ve depolanır.

## Aggregation

Bağımlı nesnenin bağlı olduğu nesne olmadan da var olabildiği bağlılık türüdür. Burada has-a ilişkisinde tutulacak nesne bu sınıftan bağımsız olarak oluşturulur ve bu sınıfa bir method aracılığı ile iletilerek bu nesneni erişimine sunulur.

# 9 – Cohesion and Coupling means and differences ?

Cohesion ve coupling sınıflar veya modüller arasındaki bağımlılığı sembolize etmemize yarayan kavramlardır.

## Cohesion

Bir sınıfın veya modülün ne kadar tek bir özellik üzerine odaklandığını ifade eder. Bu yapılması istenen işlerin her birinin bölümlendirilmesi ve birbirinden ayrılarak bağımsız olarak modülerleştirilmesi ile sağlanır. Yüksek cohesion tercih edilir. Örneğin bir müşteri sınıfının sadece müşterilerle ilgili işlemlere odaklanması ödeme vs gibi farklı işlemler için bundan bağımsız olarak geliştirme yapılması ile sağlanabilir.

## Coupling

Bir sınıfın başka bir sınıfa ne kadar bağımlı olduğunun göstergesidir. Yüksek coupling istenmeyen durumlar oluşturabilir. Örnek olarak bir sınıf içerisinde has-a ilişkisi ile bağlanmış başka bir objenin bu sınıf içierisinde oluşturulmasından ziyade bu bağımlılığı dependency injection yoluyla dışarıdan alması classın bu objeye olan bağımlılığını azaltır ve test edilme gibi konularda bize kolaylık sağlar.

Özet olarak cohesion bir sınıfın tek bir sorumluluğu ne kadar aldığını ifade ederken coupling bir sınıfın başka sınıflara ne kadar bağımlı olduğunu ifade eder.

# 10 - Heap and Stack means and differences ?

Javada program çalıştığında kullanılan belleğin yönetilmesi için bu alanlar kullanılır. Bu iki bellek veriyi saklama biçimleri, süresi ve bu verinin erişim şekilleri açısından farklılıklar gösterir.

## Stack

- Yerel değişkenlerin ve metod çağrılarının tutulduğu alandır.

- Heape göre daha hızlı erişimin olduğu saklama alandır.

- LIFO presibiyle çalışır. Yani en son giren veri ilk çıkar.

## Heap

- Objelerin saklandığı alandır.

- Statik değişkenler burada tutulur.

- Stacke göre daha fazla yer kaplar ama yönetimi daha yavaştır.

- Garbage Collector tarafından yönetilir.

Özetleyecek olursak stack daha hızlı ve küçük bir veri tutulmasını sağlarken buna uygun olarak kısa süreli metod çağrılarının ve yerel değişkenlerinin tutulduğu ve işlem bittiğinde temizlendiği depolama alanıdır. Heap ise program çalıştığı sürece kalabilecek verileri depolar ve alan yönetimi garbage collector tarafından yapılır.

# 11 – Exception means ? Type of Exceptions ?

Exceptionlar programın derlenmesinde veya çalışma aşamasında programın beklenmedik bir durumla karşılaştığında durmasına sebep olan beklenmeyen durumlardır. Bu durumlar programın ilerleyişini aksatabilir bu yüzden denetlenebilir olanlarının kontrol altına alınması gerekmektedir.

## Denetlenen Hatalar

Denetlenen hatalar derleme zamanında yakalanabilir olan hatalardır. Try-catch bloğu ile yakalanıp kontrol edilebilir veya throws kullanılarak etiketlenebilir.

Örnek olarak ParseException, FileNotFoundException, IOException gösterilebilir.

## Denetlenmeyen Hatalar

Denetlenmeyen hatalar ise run-time da uygulama çalışırken karşılaşabileceğimiz hatalardır. Örnek olarak ArrayIndexOutOfBoundsException, NullPointerException gösterilebilir.

# 12 – How to summarize ‘clean code’ as short as possible ?

Clean kod herkes tarafından dahi okunabilecek seviyeye yakın, gereksiz karmaşıklık içermeyen, yeniden düzenlenirken zorluk çıkarmayan koddur.

# 13 - What is the method of hiding in Java ?

Alt bir sınıfın üst sınıfta bulunan statik bir metodun aynı imzasını kullanarak bir method tanımlaması durumunda gerçekleşir. Burda statik olarak tanımlandığı için overloading işlemi olmaz.

# 14 - What is the difference between abstraction and polymorphism in Java ?

## Abstraction

Abstraction bir sınıfın tanımlanmasından önce sınıfın ana hatlarının basit bir şekilde modellenmesini sağlama yöntemidir. Bu sayede classın ne yapması gerektiği belirlenir ama bu özellikleri nasıl yapılacağı implementasyona bağlı olarak değişebilir. Javada abstraction abstract class ve interfaceler kullanılarak sağlanır.

## Polymorphism

Polymorphism ise kalıtım yoluyla miras alınan özelliklerin farklı classlarda farklı şekilde çalışabilmesi özelliğidir. Bu yapı ise method overloading ve method overriding ile sağlanır.
