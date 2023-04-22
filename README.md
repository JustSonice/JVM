// Application class loader берет класс программы и загружает данные о нем в область памяти мета спейс, а затем начинает работу Platform class loader, после чего запрос передается Bootstrap ClassLoader, и после него загрузчики ищут упоминаемые классы и подгружают необходимую информацию и проводят валидацию. 

    public class JvmComprehension {      

    public static void main(String[] args) { // вызывается метод мейн после чего создается фрейм в стеке
        int i = 1;                      // 1 переменная типа инт как примитивный тип данных начинает храниться прямо в стеке метода
        Object o = new Object();        // 2 ссылочный тип данных  хранится в стеке, а в хипе создается место под новый объект и создает адрес в памяти для обращения к нему
        Integer ii = 2;                 // 3 в данной строке Интеджер хранится в хипе со значением 2 и ссылка на этот объект передается в переменную ii
        printAll(o, i, ii);             // 4 вызывается новый метод, появляется новый фрейм который будет над мейном и в него передаются все переменные которые были созданы ранее
        System.out.println("finished"); // 7 Происходит обращение к классу System после чего с помощью методов происходит вывод в консоль строки с текстом
    }

    private static void printAll(Object o, int i, Integer ii) { // это фрейм в котором происходит прием ранее объявленных переменных и создается заново переменная int i
        Integer uselessVar = 700;                   // 5 создается новая переменная ссылочного типа из за чего в хипе создается объект типа Integer со значением 700
        System.out.println(o.toString() + i + ii);  // 6 Происходит обращение к лассу System и создается новый фрейм и в этот фрейм передается одно значение которые расчитывается в выражении и передаются в метод println после чего метод завершает работу и фрейм закрывается и происходит возврат к предыдущему фрейму printAll
    } 
    // после завершение работы начинает работу сборщик мусора который удаляет все неиспользуемые данные
    }