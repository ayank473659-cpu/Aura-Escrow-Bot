# Aura-Escrow-Bot
Escrow Bot 
python-telegram-bot==20.7
main.py
import os
from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, filters, ContextTypes

TOKEN = os.getenv(")

async def form(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(
        "🛡 ESCROW FORM\n\nBuyer:\nSeller:\nAmount:\nDetails:"
    )

async def keyword(update: Update, context: ContextTypes.DEFAULT_TYPE):
    if update.message.text.lower() == "form":
        await form(update, context)

app = ApplicationBuilder().token(TOKEN).build()

app.add_handler(CommandHandler("form", form))
app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, keyword))

app.run_polling()
