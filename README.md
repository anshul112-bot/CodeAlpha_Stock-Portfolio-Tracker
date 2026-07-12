# CodeAlpha_Stock-Portfolio-Tracker
# Step 1: Hardcoded stock prices
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOG": 2800,
    "AMZN": 3300,
    "MSFT": 300
}

portfolio = {}
total_investment = 0

print("📊 Stock Portfolio Tracker")
print("Available stocks:", ", ".join(stock_prices.keys()))

# Step 2: Take user input
while True:
    stock = input("\nEnter stock name (or 'done' to finish): ").upper()
    
    if stock == "DONE":
        break
    
    if stock not in stock_prices:
        print("Stock not available!")
        continue
    
    quantity = int(input(f"Enter quantity of {stock}: "))
    
    portfolio[stock] = portfolio.get(stock, 0) + quantity

# Step 3: Calculate total investment
print("\n📈 Your Portfolio:")
for stock, quantity in portfolio.items():
    price = stock_prices[stock]
    value = price * quantity
    total_investment += value
    
    print(f"{stock} - Quantity: {quantity}, Price: {price}, Value: {value}")

print("\n💰 Total Investment Value:", total_investment)

# Step 4 (Optional): Save to file
save = input("\nDo you want to save this to a file? (yes/no): ").lower()

if save == "yes":
    with open("portfolio.txt", "w") as file:
        file.write("Stock Portfolio\n")
        for stock, quantity in portfolio.items():
            price = stock_prices[stock]
            value = price * quantity
            file.write(f"{stock}, {quantity}, {price}, {value}\n")
        file.write(f"\nTotal Investment: {total_investment}")
    
    print("✅ Portfolio saved to portfolio.txt")

