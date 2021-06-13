# Data types


## Numeric types

```java

	/*All literal numbers in java are by default ints, which has range -2147483648 to  2147483647 inclusive.Your literals are outside this range, so to make this compile you need to indicate they're long literals (ie suffix with L):           http://stackoverflow.com/questions/8924896/java-long-number-too-large-error */

	int maxInt=2147483647;
	int minInt=-2147483648;

	short maxShort=32767;
	short minShort=-32768;

	long maxLong=9223372036854775807L;
	long minLong=-9223372036854775808L;

	byte maxByte=127;
	byte minByte=-128;

	int n16=0x735; // шестнадцатиричные с префиксом 0x

	/*Шестнадцатеричная система счисления — позиционная система счисления по целочисленному основанию 16. В качестве цифр этой системы счисления обычно используются цифры от 0 до 9 и латинские буквы от A до F. Буквы A, B, C, D, E, F имеют значения 10, 11, 12, 13, 14, 15 соответственно. */

	int n8=010; // восьмеричные с префиксом 0
	int n2=0b011100; // двоичные с префиксом b или B

	int util=1_000_000;// для удобочитаемости
	            
	float fl=26786796965f; // просто пример не крайнее значение
	double d=3677967979780787d;    //  просто пример не крайнее значение  
	float fl2=5.1F;
            
	boolean tr=true;//Преобразование значений типа boolean в целочисленные и наоборот невозможно.
            
	char ch=7;

	/*Числа  с  плавающей точкой  нельзя  использовать  в  финансовых  расчетах,  где  ошибки  округления  недопустимы.  Например,  в  результате  выполнения  оператора  System.out.println(2 .0 - 1.1 )будет  выведено  значение  0 .8 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 ,  а  не  0 .9 ,  как было  бы логично предположить. Подобные ошибки связаны с внутренним двоичным представлением чисел. Как  в  десятичной  системе  счисления  нельзя  точно  представить  результат деления  1 /3 ,  так  и  в двоичной  системе  невозможно точно  представить  результат деления  1 /1 0 .  Если же требуется  исключить ошибки округления, то следует воспользоваться классом BigDecimal, рассматриваемым далее  в этой  главе.  */
    
       
	//преобразование типов при присваивании
	//расширяющее преобразование

	int i;
	float f;
	i=10;
	f=i;// значение преобразовалось к float
	    
	long L;
	double D;
	L = 100123285L;
	// Автоматическое преобразование типа long в тип double.
	 D = L;
	  
	/*В то же время тип double не может быть автоматически преобразован в тип long,поскольку такое преобразование уже не является расширяющим.*/
	    
	//narrowing conversion
	//сужающее  реобразование
	       
	double x=8.8,y=2;
	print((int)(x/y)+"   потерялось дробное значение при сужающеи преобразовании");
	        
	int i=4000;
	print((byte)i +" тоже потерялось значение");
	        
	byte b=88;
	print((char)b+"   представление byte via char");
	        
	/*В выражении можно свободно употреблять два или несколько типов данных, приусловии их совместимости друг с другом. Например, в одном выражении допускается применение типов short и long, поскольку оба типа являются числовыми. Когда в выражении употребляются разные типы данных, они преобразуются в один и тот же тип по принятым в Java правилам продвижения типов. Сначала все значения типа char, byte и short продвигаются к типу int. Затем все выражение продвигается к типу long, если хотя бы один из его операндов принадлежит к типу long. Далее все выражение продвигается к типу float, если хотя бы один из операндов относится к типу float. А если какой-нибудь из операндов относится к типу double, то результат также относится к типу double.Но продвижение типов может иногда привести к неожиданным результатам. Если, например, в арифметической операции используются два значения типа byte, то происходит следующее. Сначала операнды типа byte продвигаются к типу int. А затем выполняется операция, дающая результат типа int. Следовательно, результат выполнения операции, в которой участвуют два значения типа byte, будет иметь тип int. Но ведь это не тот результат, который можно было бы с очевидностью предположить. Рассмотрим следующий пример программы: */
	
	byte b;
	int i;
	b = 10;
	      
	i= b * b;        // В данном случае приведение типов не требуется, так как результат вычисления выражения уже относится к типу int.
	       
	b = 10;        // А в этом случае приведение типов требуется для       
	b = (byte) (b * b); // присваивания значения int переменной типа byte!
	        
	int i;
	for(i = 0; i < 5; i++) {
	print (i + " / 3 INT="  + i / 3) ;
	print(i + " / 3 with (double) i= " + (double) i / 3);
	}
	
	
```

## String
```java
        
       /*Строковый литерал — последовательность символов заключенных в двойные кавычки. Важно понимать, что всегда когда вы используете строковой литерал компилятор создает объект со значением этого литерала:*/
     
	String habr = "habrahabr";
	char[] habrAsArrayOfChars = {'h', 'a', 'b', 'r', 'a', 'h', 'a', 'b', 'r'};
	byte[] habrAsArrayOfBytes = {104, 97, 98, 114, 97, 104, 97, 98, 114};

	String first = new String();
	String second = new String(habr);
	String third = new String(habrAsArrayOfChars); 
	String fourth = new String(habrAsArrayOfChars, 0, 4); // "habr"
            
	String habra = "habra";
	String habr = "habr";
	String habrahabr_ = habra + habr;
	String habrahabr =( new StringBuilder()).append(habra).append(habr).toString(); 

	int integerVariable = 10;
	String first = integerVariable + ""; // конкатенация с пустой строкой
	String second = String.valueOf(integerVariable); // вызов статического метода valueOf класса String
	String third = Integer.toString(integerVariable); // вызов метода toString класса-обертки
	String string = "10";
	int first = Integer.parseInt(string); //получаем примитивный тип (primitive type)используя метод parseXхх нужного класса-обертки, где Xxx - имя примитива с заглавной буквы (например parseInt) 
	int second = Integer.valueOf(string); // получаем объект wrapper класса и автоматически распаковываем
        
	StringBuffer firstBuffer = new StringBuffer(); // capacity = 16
	StringBuffer secondBuffer = new StringBuffer("habrahabr"); // capacity = str.length() + 16
	StringBuffer thirdBuffer = new StringBuffer(secondBuffer); // параметр - любой класс, что реализует CharSequence
	StringBuffer fourthBuffer = new StringBuffer(50); // передаем capacity
       
        /*Строки являются неизменными,  частая их модификация приводит к созданию новых объектов, что расходует  память. Для решения  проблемы  создан класс java.lang.StringBuffer,  Класс является mutable, то есть изменяемым — используйте его, если Вы хотите изменять содержимое строки.  StringBuffer может быть использован в многопоточных средах, так как все необходимые методы являются синхронизированными. Существует четыре способа создания объекта класса StringBuffer. Каждый объект имеет свою вместимость (capacity), что отвечает за длину внутреннего буфера. Если длина строки, что хранится в внутреннем буфере, не превышает размер этого буфера (capacity), то нет необходимости выделять новый массив буфера. Если же буфер переполняется —  он автоматически становиться больше. В большинстве случаев мы используем StringBuffer для многократного выполнения операций  добавления (append), вставки (insert) и удаления (delete) подстрок. */ 

	String domain = ".ru";
	StringBuffer buffer = new StringBuffer("habrahabr"); // "habrahabr"
	buffer.append(domain); // "habrahabr.ru"
	buffer.delete(buffer.length() - domain.length(), buffer.length()); // "habrahabr"
	buffer.insert(buffer.length(), domain); // "habrahabr.ru"

     
 	/*StringBuilder — класс, что представляет изменяемую последовательность символов. Класс был введен в Java 5 и имеет полностью идентичный API с StringBuffer. Единственное отличие — StringBuilder не синхронизирован. Это означает, что его использование в многопоточных средах есть нежелательным. */
 
```


# Data Structures

## Arrays 

```java
      int ar1[];//  определили ссылку массива
      ar1[1]=0;     //нельзя  инициализировать так как не известна размерность
      int []x1, x2, x3;// определили ссылку нескольких массивов
      
      int ar2[]=new int[10];// массив с 10 значениями
      ar2[1]=5; // правильная инициализация
      
      Object a3[]={1,'j',"kl", new Integer(7),sample};// объявление и инициализация в одной точке
      Object ar4[]=new String[20];
      char[] ar5={'a','b','c'};
      Object all[]={str3,ar4,ar5};

      byte[] b={1,8};
      
       
      //двумерный массив
      int dimenthion2[][]=new int[10][20];//  [n столбцов][n значений в столбце]

       int n2Ar[][]={
           {1,5,7}, 
           {1,5,7}, 
           {1,5,7},
           {2,7,8,9,46}
       };
       
       int multidim[][][] = new int[8][10][3];
       multidim.length;
       tmultidim.getClass().getCanonicalName();
```

## Collections

##### Arraylist

```java
     List<Integer> list=new ArrayList<>();
     list.add(1);
     list.add(2);
     list.contains(2); // true
     list.size(); 
     for( Integer i:list){}
```
##### HashMap

```java
    Map<String,String> map = new HashMap<>();
    map.put("tnpReseach"," Обработка ТНП ");
    map.get("tnpReseach");
```


##### Ilerators

```java
	/*Большинство коллекций из пакета java.util предоставляют возможность выборки элемента по его индексу но таким образом можно поступить далеко не со всеми коллекциями (Set, for exemple).
Вот тут то нам и придёт на помощь итератор.Все коллекции из java.util реализуют интерфейс Collection, который, в свою очередь,расширяет интерфейс Iterable. В  Iterable описан только один метод: */

	public class MyIterator{
	public  MyIterator run(){
	Set set = new HashSet();
	set.add("One");
	set.add("Two");
	set.add("Three");
	Iterator iterator = set.iterator();
	while (iterator.hasNext()) { System.out.println(iterator.next()); }
	return this;
	}
    
	/* Итераторы в Map. В этом интерфейсе нет метода iterator, но зато есть метод entrySet(). Этот метод вернёт нам Set */

	Map pets = new HashMap();
	pets.put("Мурзик", "кот");
	pets.put("Бобик", "собака");
	pets.put("Кеша", "попугай");

	Iterator iter = pets.entrySet().iterator();
	while (iter.hasNext()) {
	Map.Entry pet = ( Map.Entry) iter.next();
	Object key = pet.getKey();
	Object value = pet.getValue();
	System.out.println(pet.getKey() + " это " + pet.getValue());
		}
	}
```


## Generics

```java
	/* Обобщения  понадобились потому,  что они  позволяют писать более безопасный код,  который легче  читается,  чем  код,  перегруженный  переменными  типа  Object и приведениями типов. Обобщения особенно полезны для классов коллекций вроде вездесущего класса ArrayList. Обобщенное программирование означает написание кода, который может быть неоднократно использован с объектами самых разных типов.
Обобщенным называется класс с одной или несколькими переменными типа. 
Переменные  типа  используются  повсюду  в  определении  класса  для обозначения типов,  возвращаемых методами,  а также типов полей и локальных переменных.
Обобщенный  класс  действует  как  фабрика  обычных  классов. */

	//РАНЬШЕ ДЕЛАЛИ ТАК до появления обобщенных классов
	/* Такой подход порождает серьезые проблемы.  Всякий раз,  когда извлекается значение, необходимо выполнить приведение типа, как показано ниже. */
	public class ArrayList{
	private Object[]  elementData;
	public Object get(int i)  { return this; } ;
	public void add(Object o)  {   };
	}
	ArrayList myfiles = new ArrayList();
	String filename =  (String)  myfiles.get(1);

	/* Более того, в таком коде отсутствует проверка ошибок. Ничто не мешает добавить значения любого  класса следующим образом:*/
	myfiles.add(new File("...."));
	String filename =  (String)  myfiles.get(0);


	//ТЕПЕРЬ делают так
	/*Ошибка компиляции  —  это намного лучше, чем исключение в связи с неправильным  приведением типов во время выполнения. Привлекательность параметров типа в  том  и  состоит,  что  они  делают  исходный  код  программы  более  удобочитаемым и безопасным.*/
	ArrayList<Integer> files  = new ArrayList<> ();  
	files.add(new File(".  .  ."));  //  теперь на стадии компиляции выдавст ошибку 



    public class Pair<T> {
        private T first; //объявить переменную типа
        private T second;
        
        public Pair()  { 
            first = null;  second = null;
        } 
        public  Pair(T first,  T second)        {
            this.first = first; 
            this.second = second;
         
        }
        public T getFirst () { 
            return first;  
        } 
        public T getSecond () {
            return second;  
        }
        public void getAll(){
            print ((String)getFirst ());
            print ((String)getSecond ());
            
        }
        public void setFirst(T newValue)  {
            first = newValue;  
        } 
        public void setSecond(T newValue)  {
            second = newValue; 
        }
    }
   
        String[]  words =  {  "Mary",  "had",  "a",  "little",  "lamb"  };
        Pair<String> mm = ArrayAlg.minmax(words);
        System.out.println("min = "  + mm.getFirst());
        System.out.println("max = "  + mm.getSecond());

        Pair <String>  x= string.new Pair <String> ("Строка1", "Строка2");
        // x.getAll();
        Pair <Integer> y=integer.new Pair <Integer>(2,2);
           
        //сравнение строк
        String kt="vkvkcgfffgjfgjfgjkck";
        String ktr="vkvkcgfffgjfgjfgjkc";
        print( kt.compareTo(ktr));
       
       

	class ArrayAlg{
        public static Pair<String> minmax(String[]  a)  {
            if  (a == null  ||  a.length == 0)  return null;
             String min =  a[0];
             String max =  a[0];
           
             for  (int i = 1;  i < a.length;  i++){
                if  (min.compareTo(a[i])  > 0)  min = a[i];
                if  (max.compareTo(a[i])  < 0)  max = a[i];
            }
             
             /*
             
             compareTo
             
             The value 0 if the argument is a string lexicographically equal
             to this string; a value less than 0 if the argument is a string
             lexicographically greater than this string; and a value greater than 
             0 if the argument is a string lexicographically less than this string.
             */
             
             
             return new Pair<>(min,max);
             }
  
```

# OOP

## Interfaces
```java
	/* В  языке  C++ допускается  множественное  наследование.  Это  вызывает  много осложнений,  связанных с виртуальными базовыми  классами,  правилами доминирования  и  приведением типов указателей.  Множественным  наследованием  пользуются лишь немногие программирующие  на  C++.  Некоторые  вообще  им  не  пользуются,  а  остальные  рекомендуют  применять  множественное  наследование только  в  "примешанном”  виде.  Это  означает,  что  первичный  базовый класс  описывает  родительский  объект,  а дополнительные  базовые  классы  (так  называемые  примеси]  описывают  вспомогательные  свойства.  Такой  подход  чем-то  напоминает те  классы  в  Java, у  которых  имеется  только  один  базовый  класс  и  дополнительные  интерфейсы.  Но  в  C++  примеси  позволяют добавлять  некоторые  виды  поведения  по умолчанию, тогда  как  интерфейсы  в  Java на это  не способнЫ */

	public interface MyInterface <T> {
	double MYCONSTANT=2.4; // автоматически становится public static final
	public static final double MYCONSTANT2=2.4; // не ошибка
	default  int  compareTo(T other)  {  return 0;  }
}

```


## Initialisation via basis class 

```java

abstract class A{
    A(){print("A()");}
}

class B extends A{
    B(){print(" B()");}
}
 
// Clients code
new B(); //  output: A() B()

```





## Traits 

```java
    class One{int x;};
    class Two{int x=5;};
    
    One one=new One();
    Two two=new Two();
    
    int i=0;
       
    one.x=two.x;//5 по значению
    
    i++;
    ++i;
    
    // по умолчанию equals сравнивает ссылки,  для оберток он переопределен 
    new Integer(1)).equals(new Integer(1))
    new One()).equals(new One())

```

# Snippets - tips and trics

###### View all characters

```java

       for(int i=0;i<1000000; i++){
            if(Character.isDefined(i)){
                System.out.print(Character.toChars(i));
                System.out.print("  ");
            }else{
                print("\n\n\n\n"+i+"---Это последний элемент".toUpperCase()+"\n");
                break;
            }
           if(i%50==0) 
               print("");
        } 
    
    
    
```
###### Time of operations

```Java
    private static void test(Appendable obj) throws java.io.IOException {
        // узнаем текущее время до теста 
        long before = System.currentTimeMillis();
        for (int i = 0; i++ < 1e9; ) {
            obj.append("");
        }
        // узнаем текущее время после теста 
        long after = System.currentTimeMillis();
        // выводим результат
        System.out.println(obj.getClass().getSimpleName() + ": " + (after - before) + "ms.")
    }
```
