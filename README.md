def factorial(n):
    if n < 0:
        return "Факториал не определен для отрицательных чисел"
    elif n == 0:
        return 1
    else:
        result = 1
        for i in range(1, n + 1):
            result *= i
        return result

# Пример использования для a + b:
a = 3  # Замените это число на нужное вам значение
b = 2  # Замените это число на нужное вам значение
sum_ab = a + b
result = factorial(sum_ab)
print(f"Факториал числа {sum_ab} равен {result}")
