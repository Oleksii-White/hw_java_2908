# hw_java_2908
/*Task 2
    Есть устройство, на табло которого показывается количество секунд, оставшихся до конца рабочего дня.
    Когда рабочий день начинается ровно в 9 часов утра — табло отображает «28800» (т.е. остаётся 8 часов),
    когда 14:30 — на табло «9000» (т.е. остаётся два с половиной часа), а когда наступает 17 часов —
    на табло отображается «0» (т.е. рабочий день закончился).
    Некоторый сотрудники не умеют оценивать остаток рабочего дня в секундах.
    Требуется написать программу, которая вместо секунд будет выводить на табло понятные фразы с информацией о том,
    сколько полных часов осталось до конца рабочего дня.

    Например: «осталось 7 часов», «осталось 4 часа», «остался 1 час», «осталось менее часа».

    Объяснение: в переменную n должно записываться случайное (на время тестирования программы)
    целое число из диапазона от 0 до 28800, далее оно должно выводиться на экран (для тех, кто понимает в секундах)
    и на следующей строке (для тех кто не понимает) должна выводиться фраза о количестве полных часов,
    содержащихся в n секундах.*/

import java.util.Scanner;

public class WorkTime {
    public static void main(String[] args) {
        Scanner timeScan = new Scanner(System.in);
        System.out.println("Введите количество секунд до конца рабочего дня от 0 до 28800: ");
        int n = timeScan.nextInt();
        System.out.println("До конца смены осталось " + n + " секунд.");
        int hour = howManyHour(n);
        if (hour == 1) {
            System.out.println("Для особо одарёных - до конца смены " + hour + " час");
        } else if (hour > 1 && hour < 5) {
            System.out.println("Для особо одарёных - до конца смены " + hour + " часа");
        } else {
            System.out.println("Для особо одарёных - до конца смены " + hour + " часов");
        }

        System.out.println("\n" + "Для подсчёта зарплаты введи количество отработанных полных часов за неделю: ");
        double workHour = timeScan.nextDouble();
        System.out.println("Введи зарплату в час: ");
        double payHour = timeScan.nextDouble();
        String salary = salarySum(workHour, payHour);
        System.out.println("Ваша зарплата за неделю: " + salary);
    }

    public static int howManyHour(int a) {

        double restMin = (double) a / 60;
        double restHour = restMin / 60;

        if (restHour > 0 && restHour <= 1) {
            return 1;
        } else if (restHour > 1 && restHour <= 2) {
            return 2;
        } else if (restHour > 2 && restHour <= 3) {
            return 3;
        } else if (restHour > 3 && restHour <= 4) {
            return 4;
        } else if (restHour > 4 && restHour <= 5) {
            return 5;
        } else if (restHour > 5 && restHour <= 6) {
            return 6;
        } else if (restHour > 6 && restHour <= 7) {
            return 7;
        } else if (restHour > 7 && restHour <= 8) {
            return 8;
        } else {
            System.out.println("Что-то пошло не так =(");
            return 0;
        }
    }

    public static String salarySum(double hoursWorked, double hoursPay) {
        int regularHours = 40;
        int minPay = 8;
        double overHour;
        double salary = 0;
        if (hoursPay < minPay) {
            System.out.println("Зарплата слишком низкая");
        }

        if (hoursPay >= minPay && hoursWorked <= 40) {
            salary = hoursWorked * hoursPay;
            System.out.println("Твоя зарплата: " + salary);
        }

        if (hoursWorked > regularHours && hoursPay >= minPay) {
            overHour = (hoursWorked - regularHours) * 1.5;
            salary = (40 + overHour) * hoursPay;
            System.out.println("Твоя зарплата с учётом переработки: " + salary);
        }
        return "Зарплата " + salary;
    }
}
        /*
    Дополнительно
    Создайте метод, который будет считать сколько денег получает работник в неделю.
    Метод должен принимать на входе два аргумента (зарплата в час, кол-во проработанных часов).

    Каждый час после 40 считается за полтора.
    Работник не может работать больше, чем 60 часов в неделю.
    Работник не может получать меньше 8 долларов в час.
     */
