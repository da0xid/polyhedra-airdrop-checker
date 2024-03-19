import requests

with open("wallets.txt", "r") as file:
    wallets = [row.strip() for row in file]


def check(address: str) -> float:
    addr_prefix = address.lower()[2:5]
    # для Ethereum
    url = f"https://pub-88646eee386a4ddb840cfb05e7a8d8a5.r2.dev/eth_data/{addr_prefix}.json"

    # для BSC
    # url = f"https://pub-88646eee386a4ddb840cfb05e7a8d8a5.r2.dev/bsc_data/{addr_prefix}.json"
    resp = requests.get(url)

    try:
        json = resp.json()
        if json is None:
            return 0
        else:
            return int(json[address]['amount'], 16) / 10 ** 18
    except:
        return 0


total = 0

for wallet in wallets:
    tokens = check(wallet)
    print(f"{wallet}: {tokens}")
    total += tokens

print(f"Total: {total}")
