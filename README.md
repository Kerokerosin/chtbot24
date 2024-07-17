from aiogram.filters import Command
from aiogram.types import Message
from aiogram import Bot, Dispatcher, F
from aiogram.filters import CommandStart
from aiogram.types import (KeyboardButton, Message, ReplyKeyboardMarkup,
                           ReplyKeyboardRemove)

async def set_main_menu(bot: Bot):


    main_menu_commands = [
        BotCommand(command='/help',
                   description='Справка по работе бота'),
        BotCommand(command='/support',
                   description='Поддержка'),
        BotCommand(command='/partner',
                   description='наш партнер'),

    ]

    await bot.set_my_commands(main_menu_commands)

bot = Bot('7032814735:AAFjNVtvK6tEa1MEhVftQ0vLfYgfNLZWy-M')

dp = Dispatcher()


button_1 = KeyboardButton(text='Кнопка 1')
button_2 = KeyboardButton(text='Кнопка 2')
button_3 = KeyboardButton(text='Кнопка 3')
button_4 = KeyboardButton(text='Наши спонсор')

# Создаем объект клавиатуры, добавляя в него кнопки
my_keyboard = ReplyKeyboardMarkup(
    keyboard=[[button_1, button_2], [button_3, button_4]],
    resize_keyboard=True
)

@dp.message(Command(commands=["start"]))
async def process_start_command(message: Message):
    await message.answer ('Привет меня зовут WB-Bot/n я помогу найти тебе товары за 1 рубль!/nведи итересуюший тебя товар./nвведите команду /help')

@dp.message(Command(commands=["help"]))
async def process_help_command(message: Message):
    await message.answer ("Введи категорию товара и когда хочешь найти одежду пиши какую в плане женскую мужскую , я моментально найду тебя товар по типу: Наушники_Huawei лего перчатки")

@dp.message()
async def send_echo(message: Message):
    if message.text == ("куртка"):
        await message.answer("https://www.wildberries.ru/catalog/236551547/detail.aspx")
    elif message.text == ("кроссовки женские"):
        await message.answer("https://www.wildberries.ru/catalog/237573438/detail.aspx")
    elif message.text == ("наушнки"):
        await message.answer("https://www.wildberries.ru/catalog/204565643/detail.aspx")
    elif message.text == ("платье женское"):
        await message.answer("https://www.wildberries.ru/catalog/186700362/detail.aspx")
    elif message.text == ("платье летнее женское"):
        await message.answer("https://www.wildberries.ru/catalog/167573167/detail.aspx")
    elif message.text == ("брюки женские"):
        await message.answer("https://www.wildberries.ru/catalog/167300712/detail.aspx")
    elif message.text == ("zarina"):
        await message.answer("https://www.wildberries.ru/catalog/216539702/detail.aspx")
    elif message.text == ("футболка мужская"):
        await message.answer("https://www.wildberries.ru/catalog/156345633/detail.aspx")
    elif message.text == ("зипка"):
        await message.answer("https://www.wildberries.ru/catalog/146448170/detail.aspx") 
    elif message.text == ("кроссовки мужские"):
        await message.answer("https://www.wildberries.ru/catalog/210802695/detail.aspx")
    elif message.text == ("джинсы женские"):
        await message.answer("https://www.wildberries.ru/catalog/230146214/detail.aspx")
    elif message.text == ("найк"):
        await message.answer("https://www.wildberries.ru/catalog/229035007/detail.aspx")
        await message.answer("https://www.wildberries.ru/catalog/211695060/detail.aspx")
    else:
        await message.answer(
        text='Чего кошки боятся больше?',
        reply_markup=my_keyboard
    )   



if __name__ == '__main__':
    dp.run_polling(bot)
