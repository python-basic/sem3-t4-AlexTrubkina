ИСР:

4.1. Разработать программу для считывания данных JSON-формата из файла и вывод их в табличном виде на экран. Организовать тестирование работоспособности программы с помощью assert, print.

4.2. Дополнение программы задания 4.1 (считывание данных JSON-формата) тестами с использованием библиотеки doctest. 

4.3. Дополнение программы задания 4.1, 4.2 (считывание данных JSON-формата) тестами с использованием пакета py.test. 

4.4. Формирование отчета по самостоятельной работе и публикация его в портфолио.


ВСР:

4.1. Создание таблицы со сравнительным анализом библиотек для тестирования. Формирование отчета по выполнению задания и размещение его в портфолио, персональном репозитории. 

4.2. Написать программу для вычисления факториала натурального числа от 0 до n (где, n — целое, натуральное число, помещающееся в переменную целого числа). Для всех других случаев функция должна поднимать исключение TypeError, ValueError. Протестировать работу этой программы с использованием unittest. Учтите ситуации, для которых должны подниматься исключения. Формирование отчета по выполнению задания и размещение его в портфолио, персональном репозитории.

```python
def main():
    n = -1
    num = input("Введите число: ")
    try:
        n = int(num)
    except:
        print("Вы ввели неверное значение")
    res = fact(n)
    print(res)


def fact(num):
    if type(num) is int and num >= 0:
        fc = 1
        i = num
        if num == 0:
            return 1
        else:
            while i > 1:
                fc = fc * i
                i -= 1
        return fc
    else:
        raise ValueError("Вы ввели неверное число")
```

Тесты:

```python
from factorial import fact
import unittest


class TestFunFact(unittest.TestCase):

    def test1(self):
        self.assertEqual(fact(1), 1)

    def test2(self):
        self.assertEqual(fact(2), 2)

    def test3(self):
        self.assertEqual(fact(4), 24)

    def test4(self):
        with self.assertRaises(ValueError):
            fact("")

    def test5(self):
        with self.assertRaises(ValueError):
            fact([2, 5, 6])

    def test6(self):
        with self.assertRaises(ValueError):
            fact([1])

    def test7(self):
        with self.assertRaises(ValueError):
            fact({3})

    def test8(self):
        with self.assertRaises(ValueError):
            fact(5.1)

    def test9(self):
        with self.assertRaises(ValueError):
            fact(-1)



if __name__ == '__main__':
    unittest.main()

```
