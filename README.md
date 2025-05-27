

crypto_db = {
    "Bitcoin": {
        "price_trend": "rising",
        "market_cap": "high",
        "energy_use": "high",
        "sustainability_score": 3/10
    },
    "Ethereum": {
        "price_trend": "stable",
        "market_cap": "high",
        "energy_use": "medium",
        "sustainability_score": 6/10
    },
    "Cardano": {
        "price_trend": "rising",
        "market_cap": "medium",
        "energy_use": "low",
        "sustainability_score": 8/10
    }
}

def crypto_buddy(user_query):
    user_query = user_query.lower()

    if "sustainable" in user_query:
        recommend = max(crypto_db, key=lambda x: crypto_db[x]["sustainability_score"])
        return f"Invest in {recommend}! 🌱 It’s eco-friendly and has long-term potential!"

    elif "trending" in user_query or "rising" in user_query:
        trending_coins = [coin for coin in crypto_db if crypto_db[coin]["price_trend"] == "rising"]
        return f"These coins are trending up: {', '.join(trending_coins)}! To the moon! 🚀"

    elif "most profitable" in user_query or "long-term growth" in user_query:
        top_profitables = [coin for coin in crypto_db if crypto_db[coin]["price_trend"] == "rising" and crypto_db[coin]["market_cap"] == "high"]
        if top_profitables:
            return f"{top_profitables[0]} is your best bet for profitability right now! High trend, high cap—just how we like it! 💰"
        else:
            return "Hmm, nothing checks all the boxes right now—might be time to HODL."

    elif "should i buy" in user_query:
        for coin, data in crypto_db.items():
            if data["price_trend"] == "rising" and data["sustainability_score"] >= 0.7:
                return f"{coin} is trending up and has a top-tier sustainability score! 🚀"
        return "None of the coins are looking perfect, but maybe check Cardano for a solid eco-friendly choice!"

    else:
        return "I’m not sure how to help with that... try asking about trending coins, sustainability, or long-term investments."

if __name__ == "__main__":
    print("Hi! I’m CryptoBuddy! Ask me about trending, profitable, or sustainable crypto! Type 'exit' to quit.")
    while True:
        query = input("You: ")
        if query.lower() == "exit":
            print("Crypto is risky—always DYOR. Goodbye!")
            break
        response = crypto_buddy(query)
        print("CryptoBuddy:", response)
        
