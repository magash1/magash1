from telegram import Update, ReplyKeyboardMarkup
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

# Токен вашего бота
TOKEN = '7690435037:AAH0DfEy7YSjSv_02qKWC1ywWUgcdlDK4Uc'

# Функция для обработки команды /start
def start(update: Update, context: CallbackContext) -> None:
    keyboard = [['Привет', 'Как дела?']]
    reply_markup = ReplyKeyboardMarkup(keyboard, resize_keyboard=True)
    update.message.reply_text('Привет! Выберите вариант:', reply_markup=reply_markup)

# Функция для обработки команды /help
def help_command(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(
        "Доступные команды:\n"
        "/start - Начать диалог\n"
        "/help - Получить справку"
    )

# Функция для обработки текстовых сообщений
def echo(update: Update, context: CallbackContext) -> None:
    user_message = update.message.text.lower()
    
    if "привет" in user_message:
        update.message.reply_text("Привет! Как я могу помочь?")
    elif "как дела" in user_message:
        update.message.reply_text("У меня всё отлично, спасибо! А у вас?")
    elif "спасибо" in user_message:
        update.message.reply_text("Пожалуйста! Обращайтесь ещё.")
    elif "пока" in user_message:
        update.message.reply_text("До свидания! Буду рад помочь снова.")
    else:
        update.message.reply_text("Извините, я не понимаю. Попробуйте написать что-то другое.")

# Основная функция для запуска бота
def main() -> None: 'Старт'
    # Создаем Updater и передаем ему токен вашего бота
    updater = Updater(TOKEN)
7690435037:AAH0DfEy7YSjSv_02qKWC1ywWUgcdlDK4Uc
    # Получаем диспетчер для регистрации обработчиков
    dispatcher = updater.dispatcher

    # Регистрируем обработчики команд
    dispatcher.add_handler(CommandHandler("start", start))
    dispatcher.add_handler(CommandHandler("help", help_command))

    # Регистрируем обработчик текстовых сообщений
    dispatcher.add_handler(MessageHandler(Filters.text & ~Filters.command, echo))

    # Запускаем бота
    updater.start_polling()Start

    # Работаем до тех пор, пока не будет нажата комбинация Ctrl+C
    updater.idle()Go

if __name__ == '__main__':
    main()![IMG-20250127-WA0021](https://github.com/user-attachments/assets/e5088c76-750b-4e00-9d5c-6a1740c5de0c)
