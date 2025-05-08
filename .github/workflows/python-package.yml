import os, requests, time

# Telegram Setup - Replace YOUR_CHAT_ID
TOKEN = "7694416358:AAGblyP746ANjId-dJAgRwBjT2sGsuPIrKw"
CHAT_ID = "YOUR_CHAT_ID"  # Get it by sending /start to @RawDataBot on Telegram

# Your Watchlist - Edit These!
COINS = {
    "bitcoin": "BTC/USDT",
    "ethereum": "ETH/USDT",
    "solana": "SOL/USDT"
}

def send(msg):
    """Send Telegram alert"""
    requests.post(f"https://api.telegram.org/bot{TOKEN}/sendMessage",
                json={'chat_id': CHAT_ID, 'text': msg})

def get_price(coin):
    """Get current price"""
    try:
        url = f"https://api.coingecko.com/api/v3/simple/price?ids={coin}&vs_currencies=usd"
        return requests.get(url).json()[coin]['usd']
    except:
        return None

# Bot Startup
send("🤖 Your FREE Crypto Bot is LIVE!")

# Main Loop
while True:
    for coin, pair in COINS.items():
        price = get_price(coin)
        if price and price < 1000:  # Example buy condition
            send(f"🚀 BUY {pair} NOW: ${price}")
        time.sleep(10)  # Avoid API limits
    time.sleep(60)  # Check every minute
