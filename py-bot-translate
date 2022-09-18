import asyncio
from aiogram import Bot, Dispatcher
from aiogram import types, utils, filters 
from aiogram.utils import executor
from googletrans import Translator
from googletrans.client import LANGUAGES

#region Свойства
api_hash =  ""
api_id = 1
bot_token = ""
#endregion
bot = Bot(token=bot_token)
dp = Dispatcher(bot)
trans = Translator()

@dp.message_handler(commands=['t'])
async def process_start_command(message: types.Message):
    result = trans.translate(message.text)
    await message.answer(text=result.text)


@dp.message_handler(commands=['trans'])
async def process_start_command(message: types.Message):
    _from     = message.text[7:9]
    _to       = message.text[10:12]
    trans_rdy = trans.translate(text=message.text[12:], dest=_to, src=_from)
    await message.answer(trans_rdy.text)

@dp.message_handler(commands=['langs'])
async def process_start_command(message: types.Message):
    keys   = list(LANGUAGES.keys())
    values = list(LANGUAGES.values()) 
    s = ""
    c = 0
    for i in keys:
        s = s + " " + i + " - " + values[c] + ", \n"
        c+=1
    await message.answer(s)

@dp.message_handler(commands=['help'])
async def process_help_command(message: types.Message):
    await message.answer("/t - перевод с русского на англ \n" +
                        "/trans - выбор языков для перевода  \"/trans ru en (с какого на какой) жопа\" \n" +
                        "/langs - языки \n" +
                        "/help - помощь")

@dp.message_handler()
async def id_by_nik(message: types.Message):

    print(message.as_json(forward_from.id))
    


if __name__ == '__main__':
    executor.start_polling(dp)

