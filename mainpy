import random

# Define alternatives
HUNDRED = ["H", "Hund", "Hundred", "C Note", "Bills"]
THOUSAND = ["K", "k", "Thousand", "Thou", "Grand", "G", "Stacks"]
TEN_THOUSAND = ["10K", "10k", "Ten Thousand", "10 Large", "10 Grand"]
LAKH = ["Lakh", "L", "Lac", "Lacs"]
MILLION = ["M", "Million", "Mil"]

def distribute_savings(total_savings, days):
    """
    Distribute total savings over the specified days with daily savings:
    - Divisible by 5
    - Within the range 50 to 1000
    """
    min_daily = 50
    max_daily = 1000

    # Ensure total savings is feasible
    if total_savings < days * min_daily or total_savings > days * max_daily or total_savings % 5 != 0:
        raise ValueError(f"Savings amount must be divisible by 5 and between {days * min_daily} and {days * max_daily} for {days} days.")
    
    savings = []
    remaining = total_savings

    for day in range(days - 1):
        max_possible = min(max_daily, remaining - (days - len(savings) - 1) * min_daily)
        daily_saving = random.randrange(min_daily, max_possible + 1, 5)
        savings.append(daily_saving)
        remaining -= daily_saving

    # Final day
    savings.append(remaining)

    # Shuffle for randomness
    random.shuffle(savings)
    return savings

def amt():
    while True:
        try:
            # Input total savings
            amount = input("Enter the saving amount (e.g., 5k, 1000): ").strip()
            
            # Input number of days
            days = input("How many days you want to save? ").strip()
            if not days.isdigit() or int(days) <= 0:
                raise ValueError("Invalid number of days. Please enter a positive integer.")
            days = int(days)

            # Process the amount
            if not amount.isdigit():
                digit = ''.join(filter(str.isdigit, amount))  # Extract numeric part
                word = ''.join(filter(str.isalpha, amount)).title()  # Extract alphabetic part, capitalize
                
                # Match the word with defined alternatives
                if word in HUNDRED:
                    digit += "00"  # Add two zeros for hundred
                elif word in THOUSAND:
                    digit += "000"  # Add three zeros for thousand
                elif word in TEN_THOUSAND:
                    digit += "0000"  # Add four zeros for ten thousand
                elif word in LAKH:
                    digit += "00000"  # Add five zeros for lakh
                elif word in MILLION:
                    digit += "000000"  # Add six zeros for million
                else:
                    raise ValueError("Unrecognized unit. Please use valid alternatives like K, Lakh, or Million.")
                total_savings = int(digit)
            elif amount.isdigit():
                total_savings = int(amount)
            else:
                raise ValueError("Invalid amount format. Please try again.")

            # Distribute savings and display results
            savings_distribution = distribute_savings(total_savings, days)
            print(f"\nYour savings distribution over {days} days:")
            print(savings_distribution)
            print(f"Total savings: {sum(savings_distribution)} (Target: {total_savings})\n")

        except ValueError as e:
            print(f"Error: {e}")
        except Exception as e:
            print(f"An unexpected error occurred: {e}")

        if not restart_prompt():
            break  # Exit the loop if the user doesn't want to restart

def restart_prompt():
    """Prompt the user to restart or exit."""
    while True:
        again = input("Do you want to restart? (yes/no): ").strip().lower()
        if again == 'yes':
            return True
        elif again == 'no':
            print("Okay, exiting!")
            return False
        else:
            print("Invalid input. Please type 'yes' or 'no'.")

# Call the function
amt()











