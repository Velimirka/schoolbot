import openpyxl

wb = openpyxl.load_workbook('table.xlsx')
sheet = wb.active

rows = sheet.max_row
cols = sheet.max_column



def main():
    bot_run()


def bot_run():
    """
    запуск бота
    :return:
    """
    connect()

    show_score()

    new_score()

    get_porametrs()


def connect():          #Конект бота
    """
    Конект с вк
    :return:
    """
    pass


def show_score(name):       # Узнаваем сколько очков у человека
    """
    Ввод:
        имя
    Вывод:
        кол-во очков пользователя
    :return:
    """

    for i in range(1, rows + 1):
        cell = sheet.cell(row=i, column=1)
        if name == cell.value:
            cell = sheet.cell(row=i, column=2)
            print('Счет:', cell.value)


def new_score(name, score):        #Изменяем кол-во очков в БД
    """
    Ввод:
        Имя + кол-во очков
    Вывод:
        Новое кол-очков
        Внесение нового значения в БД
    :return:
    """

    for i in range(1, rows + 1):
        cell = sheet.cell(row=i, column=1)
        if name == cell.value:
            cell = sheet.cell(row=i, column=2).value
            cell += score
            print('Новый счет:', cell)
            sheet.cell(row=i, column=2).value = cell

            # wb.save('table.xlsx')

def get_porametrs():
    """

    принимаем данные

    :return:
    """
    name = input("Ведите имя: ")
