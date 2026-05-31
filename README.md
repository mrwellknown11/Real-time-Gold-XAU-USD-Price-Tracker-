# Real-time-Gold-XAU-USD-Price-Tracker-
#1. main.py
import yfinance as yf
import time

def fetch_gold_price():
    print("Initializing Live Gold (XAU/USD) Price Tracker...\n")
    print("Press Ctrl+C to stop.\n")
    try:
        # XAU/USD ticker for Yahoo Finance
        gold = yf.Ticker("XAUUSD=X")
        
        while True:
            # Fetch latest 1-minute interval data
            data = gold.history(period="1d", interval="1m")
            if not data.empty:
                latest_price = data['Close'].iloc[-1]
                current_time = data.index[-1].strftime("%Y-%m-%d %H:%M:%S")
                
                print(f"[{current_time}] XAU/USD Live Price: ${latest_price:.2f}")
            else:
                print("Failed to retrieve data. Retrying...")
                
            time.sleep(60) # Wait for 60 seconds before next update
            
    except KeyboardInterrupt:
        print("\nTracker stopped successfully.")
    except Exception as e:
        print(f"\nAn error occurred: {e}")

if __name__ == "__main__":
    fetch_gold_price()                     # 2. requirements.txt
   yfinance>=0.2.37
pandas>=2.2.1
## Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# Virtual environments
venv/
env/
ENV/

# OS generated files
.DS_Store
Thumbs.db
#4. README.md
# Live Gold (XAU/USD) Price Tracker 📈

A simple, lightweight Python script that tracks the real-time market price of Gold (XAU/USD) using the Yahoo Finance API. Perfect for monitoring market movements directly from your terminal.

## Features
* Fetches live market data for XAU/USD accurately.
* Automatically refreshes and updates the price every 60 seconds.
* Clean and minimal terminal output.

## Prerequisites
Make sure you have Python 3 installed on your system.

## Installation

1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/xauusd-price-tracker.git](https://github.com/YOUR_USERNAME/xauusd-price-tracker.git)
   cd xauusd-price-tracker
   

