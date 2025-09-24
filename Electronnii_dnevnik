import random

# список учеников
students = ['Аполлон', 'Ярослав', 'Александра', 'Дарья', 'Ангелина']
students.sort()

# список предметов
classes = ['Математика', 'Русский язык', 'Информатика']

# словарь с оценками по каждому ученику и предмету
students_marks = {}

# генерируем данные по оценкам
for student in students:
    students_marks[student] = {}
    for class_ in classes:
        marks = [random.randint(1, 5) for i in range(3)]
        students_marks[student][class_] = marks

def calc_avg(student):
    """Вычисляем средний балл ученика по всем предметам"""
    total = 0
    count = 0
    for marks in students_marks[student].values():
        if marks:
            total += sum(marks)
            count += len(marks)
    return total / count if count > 0 else 0

print('''
Список команд:
1. Добавить оценку ученика по предмету
2. Вывести средний балл по всем предметам по каждому ученику
3. Вывести все оценки по всем ученикам
4. Удалить оценку ученика по предмету
5. Редактировать оценку ученика по предмету
6. Добавить нового ученика
7. Удалить ученика
8. Добавить новый предмет
9. Удалить предмет
10. Показать все оценки конкретного ученика
11. Показать средний балл конкретного ученика по предметам
12. Редактировать ученика (переименовать)
13. Редактировать предмет (переименовать)
14. Выход из программы
15. Хорошисты (ср.балл >= 3.5 и < 4.5)
16. Отличники (ср.балл >= 4.5)
''')

while True:
    try:
        command = int(input('Введите команду: '))
    except ValueError:
        print("Нужно ввести число!")
        continue

    if command == 1:
        student = input('Введите имя ученика: ')
        class_ = input('Введите предмет: ')
        try:
            mark = int(input('Введите оценку: '))
        except ValueError:
            print("Ошибка: нужно ввести число.")
            continue
        if student in students_marks and class_ in students_marks[student]:
            students_marks[student][class_].append(mark)
            print(f'Для {student} по предмету {class_} добавлена оценка {mark}')
        else:
            print('ОШИБКА: неверное имя ученика или название предмета')

    elif command == 2:
        for student in students_marks:
            print(student)
            for class_ in students_marks[student]:
                marks = students_marks[student][class_]
                if marks:
                    avg = sum(marks) / len(marks)
                    print(f'{class_} - {avg:.2f}')
            print()

    elif command == 3:
        for student in students_marks:
            print(student)
            for class_ in students_marks[student]:
                print(f'\t{class_} - {students_marks[student][class_]}')
            print()

    elif command == 4:
        student = input('Введите имя ученика: ')
        class_ = input('Введите предмет: ')
        if student in students_marks and class_ in students_marks[student]:
            print(f'Оценки: {students_marks[student][class_]}')
            try:
                index = int(input('Введите номер оценки для удаления (начиная с 1): ')) - 1
                removed = students_marks[student][class_].pop(index)
                print(f'Удалена оценка {removed}')
            except Exception:
                print("Ошибка при удалении оценки.")
        else:
            print("Ученик или предмет не найден.")

    elif command == 5:
        student = input('Введите имя ученика: ')
        class_ = input('Введите предмет: ')
        if student in students_marks and class_ in students_marks[student]:
            print(f'Оценки: {students_marks[student][class_]}')
            try:
                index = int(input('Введите номер оценки для изменения (начиная с 1): ')) - 1
                new_mark = int(input('Введите новую оценку: '))
                students_marks[student][class_][index] = new_mark
                print("Оценка изменена.")
            except Exception:
                print("Ошибка при редактировании оценки.")
        else:
            print("Ученик или предмет не найден.")

    elif command == 6:
        new_student = input("Введите имя нового ученика: ")
        if new_student not in students_marks:
            students_marks[new_student] = {class_: [] for class_ in classes}
            print(f"Ученик {new_student} добавлен.")
        else:
            print("Такой ученик уже есть.")

    elif command == 7:
        student = input("Введите имя ученика для удаления: ")
        if student in students_marks:
            del students_marks[student]
            print(f"Ученик {student} удалён.")
        else:
            print("Ученик не найден.")

    elif command == 8:
        new_class = input("Введите название нового предмета: ")
        if new_class not in classes:
            classes.append(new_class)
            for student in students_marks:
                students_marks[student][new_class] = []
            print(f"Предмет {new_class} добавлен.")
        else:
            print("Такой предмет уже есть.")

    elif command == 9:
        class_ = input("Введите название предмета для удаления: ")
        if class_ in classes:
            classes.remove(class_)
            for student in students_marks:
                if class_ in students_marks[student]:
                    del students_marks[student][class_]
            print(f"Предмет {class_} удалён.")
        else:
            print("Предмет не найден.")

    elif command == 10:
        student = input("Введите имя ученика: ")
        if student in students_marks:
            print(student)
            for class_ in students_marks[student]:
                print(f'{class_}: {students_marks[student][class_]}')
        else:
            print("Ученик не найден.")

    elif command == 11:
        student = input("Введите имя ученика: ")
        if student in students_marks:
            print(student)
            for class_ in students_marks[student]:
                marks = students_marks[student][class_]
                if marks:
                    avg = sum(marks) / len(marks)
                    print(f'{class_}: {avg:.2f}')
        else:
            print("Ученик не найден.")

    elif command == 12:  # редактировать ученика
        old_name = input("Введите имя ученика, которого хотите переименовать: ")
        if old_name in students_marks:
            new_name = input("Введите новое имя ученика: ")
            students_marks[new_name] = students_marks.pop(old_name)
            print(f"Ученик {old_name} переименован в {new_name}.")
        else:
            print("Ученик не найден.")

    elif command == 13:  # редактировать предмет
        old_subject = input("Введите название предмета, который хотите переименовать: ")
        if old_subject in classes:
            new_subject = input("Введите новое название предмета: ")
            classes[classes.index(old_subject)] = new_subject
            for student in students_marks:
                students_marks[student][new_subject] = students_marks[student].pop(old_subject)
            print(f"Предмет {old_subject} переименован в {new_subject}.")
        else:
            print("Предмет не найден.")

    elif command == 14:
        print("Выход из программы")
        break

    elif command == 15:  # хорошисты
        print("Хорошисты:")
        found = False
        for student in students_marks:
            avg = calc_avg(student)
            if 3.5 <= avg < 4.5:
                print(f"{student} - ср.балл {avg:.2f}")
                found = True
        if not found:
            print("Нет хорошистов.")

    elif command == 16:  # отличники
        print("Отличники:")
        found = False
        for student in students_marks:
            avg = calc_avg(student)
            if avg >= 4.5:
                print(f"{student} - ср.балл {avg:.2f}")
                found = True
        if not found:
            print("Нет отличников.")

    else:
        print("Нет такой команды.")
