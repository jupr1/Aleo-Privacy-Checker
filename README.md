# Aleo-Privacy-Checker-Script  
Aleo Privacy Checker is a useful Python script that allows users of the Aleo blockchain to check the privacy level of their transactions and contracts. With this script, you can easily assess how confidential and secure your actions on the Aleo blockchain are.
import requests

def check_privacy(address_or_hash):
    api_url = f"https://api.aleoexplorer.io/v1/transactions/{address_or_hash}"
    response = requests.get(api_url)
    
    if response.status_code == 200:
        transaction_data = response.json()
        if "privacy" in transaction_data:
            privacy_level = transaction_data["privacy"]
            return privacy_level
        else:
            return "Unknown"
    else:
        return "Error: Transaction not found or invalid input."

if __name__ == "__main__":
    print("Welcome to Aleo Privacy Checker!")
    address_or_hash = input("Enter the wallet address or transaction hash to check: ")
    privacy_level = check_privacy(address_or_hash)
    print(f"Privacy Level: {privacy_level}")
