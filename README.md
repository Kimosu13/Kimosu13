- 👋 Hi, I’m @Kimosu13
interests = "cryptocurrency trading"
learning = "machine learning algorithms for financial analysis"
collaboration = "developing trading bots"
contact = "naliakajane11@gmail.com"
pronouns = "he/him"
fun_fact = "I once backpacked across Europe for a month!".


<!---
Kimosu13/Kimosu13 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->import random
import time

# Function to simulate trading with a success rate of 99.99%
def simulate_trade():
    success_rate = 0.9999
    if random.random() < success_rate:
        return True
    else:
        return False

# Function to simulate trading and calculate profits
def run_trading_simulation(balance_ksh, duration_hours):
    investment_ksh = balance_ksh
    profit_ksh = 0
    successful_trades = 0
    total_trades = 0
    start_time = time.time()

    while time.time() - start_time < duration_hours * 3600:
        total_trades += 1
        if simulate_trade():
            # Simulating a successful trade with a random profit
            trade_profit_ksh = random.uniform(0, 0.1) * investment_ksh
            profit_ksh += trade_profit_ksh
            investment_ksh += trade_profit_ksh
            successful_trades += 1
        else:
            # Simulating an unsuccessful trade with a loss of 10%
            investment_ksh -= 0.1 * investment_ksh
        
        # Simulate a delay between trades
        time.sleep(random.uniform(0.5, 2))

    success_rate = (successful_trades / total_trades) * 100 if total_trades > 0 else 0
    return profit_ksh, success_rate

# Main function to run the trading simulation
def run_trading_app(balance_ksh, duration_hours):
    initial_balance_ksh = balance_ksh
    total_profit_ksh, success_rate = run_trading_simulation(balance_ksh, duration_hours)
    final_balance_ksh = initial_balance_ksh + total_profit_ksh
    return f"Initial Balance: {initial_balance_ksh} KSH, Final Balance: {final_balance_ksh} KSH, Profit: {total_profit_ksh} KSH, Success Rate: {success_rate:.2f}%"

# Example usage
if __name__ == "__main__":
    initial_balance_ksh = 100  # Initial balance in KSH
    trading_duration_hours = 24  # Trading duration in hours
    result = run_trading_app(initial_balance_ksh, trading_duration_hours)
    print(result)
