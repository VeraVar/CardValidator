# Отчёт о тестировании Credit Card Number Validator

## Краткое описание

18/06/2020 было проведено тестирование установки IntelliJ IDEA и функциональное тестирование кода для приложения Credit Card Number Validator.

На тестирование затрачено: 2 часа

В результате тестирования выявлены следующие дефекты:
* https://github.com/VeraVar/CardValidator/issues/1
* https://github.com/VeraVar/CardValidator/issues/2
* https://github.com/VeraVar/CardValidator/issues/3
* https://github.com/VeraVar/CardValidator/issues/4
* https://github.com/VeraVar/CardValidator/issues/5
* https://github.com/VeraVar/CardValidator/issues/6
* https://github.com/VeraVar/CardValidator/issues/7
* https://github.com/VeraVar/CardValidator/issues/8
* https://github.com/VeraVar/CardValidator/issues/9

## Описание процесса тестирования

В процессе тестирования использовались следующие артефакты:
* руководство по установке IntelliJ IDEA
* код для проверки валидации номеров банковских карт
```
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```
* тест-кейсы
* баг-репорты

В качестве тестовых данных использовались:
* валидные номера карт, сгенерированные сайтом https://creditcardgenerator.in (содержатся в файле "Card numbers")
Ожидаемый результат: OK
* невалидные значения (указаны в тест-кейсах)	
Ожидаемый результат: FAIL

Тестирование производилось в следующем окружении:
* ОС Windows 7 Prof 64x
* openjdk version "11.0.7" 2020-04-14
* IntelliJ IDEA 2020.1.2 (Community Edition)
