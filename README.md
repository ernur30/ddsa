import os

# Функция для регистрации новых студентов
def register_student():
    print("Регистрация нового студента")
    first_name = input("Введите имя: ")
    last_name = input("Введите фамилию: ")
    login = input("Введите логин: ")
    password = input("Введите пароль: ")

    # Проверка на уникальность логина
    if not is_login_unique(login):
        print("Пользователь с таким логином уже существует.")
        return

    # Сохранение информации о студенте в файле "students.txt"
    with open("students.txt", "a") as file:
        file.write(f"{first_name} {last_name}, {login}, {password}\n")
    print("Регистрация успешно завершена.")

# Функция для проверки уникальности логина
def is_login_unique(login):
    with open("students.txt", "r") as file:
        lines = file.readlines()
        for line in lines:
            if login in line:
                return False
    return True

# Функция для авторизации студентов
def login_student():
    print("Авторизация студента")
    login = input("Введите логин: ")
    password = input("Введите пароль: ")

    # Проверка существования логина и пароля в файле "students.txt"
    with open("students.txt", "r") as file:
        lines = file.readlines()
        for line in lines:
            if f"{login}, {password}\n" == line:
                print("Авторизация успешна.")
                return
    print("Неверный логин или пароль.")

# Основная функция программы
def main():
    while True:
        print("\nВыберите действие:")
        print("1. Регистрация нового студента")
        print("2. Авторизация студента")
        print("3. Выход")
        choice = input("Введите номер действия: ")

        if choice == "1":
            register_student()
        elif choice == "2":
            login_student()
        elif choice == "3":
            print("Выход из программы.")
            break
        else:
            print("Неверный выбор. Пожалуйста, выберите 1, 2 или 3.")

if __name__ == "__main__":
    main()
