# Faucet Automation Script for dkargo.io

A PHP-based faucet automation script designed to request tokens from the [dkargo.io](https://dkargo.io/en/developers/faucet) faucet. It supports rotating wallets and proxies, handles multiple faucet request steps, and provides clear colored console output for easy monitoring.

---

## Features

* Loads multiple Ethereum wallet addresses from `addresses.txt`.
* Supports proxy rotation with SOCKS5 and HTTP proxies from `proxies.txt`.
* Sequentially performs 3 required "next-action" steps per faucet request.
* Parses responses and detects success, retry, or stop conditions.
* Prints transaction links on success to [Sepolia Arbiscan](https://sepolia.arbiscan.io/tx/).
* Includes countdown timer to wait 24 hours between faucet runs.
* Colored terminal output for clear status messages.
* Cross-platform console clearing.

---

## Requirements

* PHP 7.4 or higher.
* CLI access to run PHP scripts.
* `curl` extension enabled in PHP.
* Internet connection.
* Optional: Proxy servers if you want to use proxies.

---

## Setup

1. Clone or download this repository.

2. Prepare your wallets file:

   Create a file named `addresses.txt` in the same folder. Add your Ethereum wallet addresses (Sepolia testnet addresses starting with `0x` and 40 hex characters) — one per line. For example:

   ```
   0xAbc123... (40 hex chars)
   0xDef456... (40 hex chars)
   ```

3. (Optional) Prepare your proxies file:

   Create a file named `proxies.txt` if you want to use proxies. Add one proxy per line, supporting formats like:

   * `socks5://username:password@host:port`
   * `http://username:password@host:port`
   * `host:port`

   The script will automatically assign proxies to wallets in order or randomly if fewer proxies than wallets.

---

## Usage

Run the script from your terminal:

```bash
php meomundep.php
```

The script will:

* Clear your console.
* Display a banner and info messages.
* Load wallets and proxies.
* Loop through each wallet and perform faucet requests with multiple steps.
* Display status messages (success, retry, error).
* Wait 24 hours after completing all wallets before restarting.

---

## Notes

* If you receive proxy errors (HTTP 402 or 407), check your proxy credentials.
* If the faucet is "already in progress," the script will skip that wallet until next run.
* Ensure your wallets and proxies files are correctly formatted.
* The faucet URL and next-action codes are hardcoded for the current dkargo.io faucet and may change if the site updates.

---

## Troubleshooting

* Make sure PHP has `curl` enabled (`php -m | grep curl`).
* Check your proxy format if requests fail.
* Review console error messages for hints.
* You can enable debug output by modifying the script `debugResponse()` function if needed.

---

## Useful Links

* [dkargo.io faucet page](https://dkargo.io/en/developers/faucet)
* [Sepolia Arbiscan Explorer](https://sepolia.arbiscan.io/)
* [PHP Manual - curl](https://www.php.net/manual/en/book.curl.php)
* [Ethereum addresses format](https://ethereum.org/en/developers/docs/accounts/)

---

## Author

Script by [@Meomundep](https://github.com/MeoMunDep) from [BlackCatSyndicate](https://t.me/KeoAirDropFreeNe)

---

## License

MIT License — feel free to use and modify responsibly.
