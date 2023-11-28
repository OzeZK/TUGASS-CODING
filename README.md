# TUGASS-CODING
from telegram import Update
from telegram.ext import Application, CommandHandler, ContextTypes, filters, MessageHandler


key_token = "6635535264:AAGWYK0o1s7CLz6qpG3YcBF12PmirTXhETs"
user_bot = "Ocean_IGS_bot"


async def  start_command(update: Update, context:ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Gunakan /help untuk menampilkan apa yang dapat saya berikan..")
    
async def  help_command(update: Update, context:ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Kirim pesan, bot akan membalas pesan..")


async def  text_massage(update: Update, context:ContextTypes.DEFAULT_TYPE):
    text_diterima : str = update.message.text
    print(f"Pesan diterima : {text_diterima}")
    text_lwr_diterima = text_diterima.lower()
    if 'halo' in text_lwr_diterima:
        await update.message.reply_text("Hallo juga")
    elif 'selamat malam' in text_lwr_diterima:
        await update.message.reply_text("TEDOK KAU")
    elif 'siapa kamu ?' in text_lwr_diterima:
        await update.message.reply_text(f"bot adalah : {user_bot}")
    elif 'selamat pagi' in text_lwr_diterima:
        await update.message.reply_text("pagi bang")
    elif 'game apa yang bagus untuk dimainkan ?' in text_lwr_diterima:
        await update.message.reply_text("POUUUUUU")
    elif 'apakah kau menikmati sekolah di IGS ?' in text_lwr_diterima:
        await update.message.reply_text("ya, aku sungguh menikmatinya")
    else:
        await update.message.reply_text("bot tidak mengerti")


async def photo_message(update: Update, context:ContextTypes.DEFAULT_TYPE):
    return await update.message.reply_text("GAMBAR KAU BURIK KALI")
        
async def  error(update: Update, context:ContextTypes.DEFAULT_TYPE):
    print(f"error... : {context.error}")


if __name__ == '__main__':
    print("Mulai")
    app = Application.builder().token(key_token).build()
    #COMMAND :
    app.add_handler(CommandHandler('start', start_command))
    app.add_handler(CommandHandler('help', help_command))
    #MESSAGE:
    app.add_handler(MessageHandler(filters.TEXT, text_massage))
    app.add_handler(MessageHandler(filters.PHOTO, photo_message))
    #error :
    app.add_error_handler(error)
    #polling :
    app.run_polling(poll_interval=1)
