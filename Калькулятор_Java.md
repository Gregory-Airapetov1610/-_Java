import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine(); // Считываем с клавиатуры и записываем в input.

// Разделяем строку спомощью пробела и пресваеваем значения переменным number1, number2 и operation.
// В индекс массива array вприсываем числа и операцию.
        String[] array = input.split(" ");
        if (array.length > 3) {
            System.out.println("Ошибка, формат ввода неверный. Приммер ввода 5 + 5 или V + V");
            return;
        }
        int number1;
        if (romanNum(array[0])) {    //Проверяем какое число римское или арабское. Переменная 1
            number1 = romanToArabic(array[0]);
        } else {
            number1 = Integer.parseInt(array[0]);
        }

            String operation = array[1];

        int number2;
        if (romanNum(array[2])) {   //Проверяем какое число римское или арабское. Переменная 2
            number2 = romanToArabic(array[2]);
        } else {
            number2 = Integer.parseInt(array[2]);
        }

// Проверяем подходит ли число под критерии. От 1 до 10 переменная 1 и переменная 2
        if (!((number1 >= 1) && (number1 <= 10)) || !((number2 >= 1) && (number2 <= 10))) {
            System.out.println("Ошибка, число должно быть от 1 до 10, включительно");
            return;
        }

// Выполняем операцию в зависимости от знака.
        int result;
        switch (operation) {
            case "+":
                result = number1 + number2;
                break;
            case "-":
                result = number1 - number2;
                break;
            case "*":
                result = number1 * number2;
                break;
            case "/":
                result = number1 / number2;
                break;
            default:
                System.out.println("Не верная операция");
                return;
        }
        if (!romanNum(array[0]) && !romanNum(array[2])) { // в зависимости от ввода, вывод ответ в нужной раскладке
            System.out.println(result);
        }
        else if (romanNum(array[0]) && romanNum(array[2])){
        System.out.println(arabicToRoman(result));
        }
        else if (!romanNum(array[0]) && romanNum(array[2]) || romanNum(array[0]) && !romanNum(array[2])){
            System.out.println("Ошибка, формат ввода неверный. Приммер ввода 5 + 5 или V + V");
        }
    }
    private static boolean romanNum(String input) { // проверка, соответствует ли строка заданному регулярному выражению.
        return input.matches("[IVXLCDM]+");
    }

    private static int romanToArabic(String roman) { // Функция для преобразования римского числа в арабское для выполнения арифметических операций.
        switch (roman) {
            case "I":
                return 1;
            case "II":
                return 2;
            case "III":
                return 3;
            case "IV":
                return 4;
            case "V":
                return 5;
            case "VI":
                return 6;
            case "VII":
                return 7;
            case "VIII":
                return 8;
            case "IX":
                return 9;
            case "X":
                return 10;
            case "XX":
                return 20;

            default:
                throw new IllegalArgumentException("Ошибка, число должно быть от I до X, включительно"); //Исключение недопустимый аргумент.
        }
    }
    private static String arabicToRoman(int number) {   // Преобразуем арабские числа в римские.
        if (number <= 0) {
            System.out.println("Отрицательные числа недопустимы");
        }

        String[] arrayRomanNum = {"I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X",
                "XI", "XII", "XIII", "XIV", "XV", "XVI", "XVII", "XVIII", "XIX", "XX",
                "XXI", "XXII", "XXIII", "XXIV", "XXV", "XXVI", "XXVII", "XXVIII", "XXIX", "XXX",
                "XXXI", "XXXII", "XXXIII", "XXXIV", "XXXV", "XXXVI", "XXXVII", "XXXVIII", "XXXIX", "XL",
                "XLI", "XLII", "XLIII", "XLIV", "XLV", "XLVI", "XLVII", "XLVIII", "XLIX", "L",
                "LI", "LII", "LIII", "LIV", "LV", "LVI", "LVII", "LVIII", "LIX", "LX",
                "LXI", "LXII", "LXIII", "LXIV", "LXV", "LXVI", "LXVII", "LXVIII", "LXIX", "LXX",
                "LXXI", "LXXII", "LXXIII", "LXXIV", "LXXV", "LXXVI", "LXXVII", "LXXVIII", "LXXIX", "LXXX",
                "LXXXI", "LXXXII", "LXXXIII", "LXXXIV", "LXXXV", "LXXXVI", "LXXXVII", "LXXXVIII", "LXXXIX", "XC",
                "XCI", "XCII", "XCIII", "XCIV", "XCV", "XCVI", "XCVII", "XCVIII", "XCIX", "C"};

        return arrayRomanNum[number - 1]; // поскольку индекс массива начинается от 0, мы вычитаем 1
    }
}

