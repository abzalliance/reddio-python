# **red-py-sdk**

![](https://img.shields.io/pypi/pyversions/Django.svg)


## **Overview**
`red-py-sdk` is a Python SDK for interacting with the Reddio Layer 2 ecosystem on StarkNet. It allows developers to mint, transfer, withdraw NFTs, and manage balances securely and efficiently.

---

## **Installation**

Install the SDK via `pip`:

```bash
pip3 install red-py-sdk
```

---

## **Quick Start**

### **1. Import and Initialize**

Import the SDK and initialize the `Reddio` object. You can use either the **testnet** or **mainnet** environment:

```python
from redpysdk import Reddio

# Initialize on testnet
reddio = Reddio("testnet")

# Initialize on mainnet
# reddio = Reddio("mainnet")
```

---

### **2. Generate Stark Key Pair**
Generates a random Stark key pair.

**Method**: `get_stark_key_pair()`

**Example**:
```python
stark_pair = reddio.get_stark_key_pair()
print(stark_pair)
```

**Output**:
```plaintext
('0x395d1708ab0ee91efcb7f26a2f4fcbe20faf3c7390517667fed37b0e481882a', 
 '0x5aa1b67a486b6564a2b6ae7426950c03dfe6991f9d34ea45b6b0be0672a1818')
```

---

### **3. Mint NFT**
Mint NFTs to a specified Stark key.

**Method**: `mintNFT(api_key, contract_address, stark_key, amount)`

**Parameters**:
- `api_key` *(string)*: Your API key (register at [Reddio Dashboard](https://dashboard.reddio.com)).
- `contract_address` *(string)*: The ERC721M contract address.
- `stark_key` *(string)*: The recipient's Stark key.
- `amount` *(int)*: Number of tokens to mint.

**Example**:
```python
minted_tokens = reddio.mintNFT(
    api_key="your_api_key_here",
    contract_address="0xd60523fd920eb9b7eff3e115203e32d91de5cf59",
    stark_key="0x1ccc27877014bc1a81919fc855ebbd1b874603283c9ea93397d970b0704e581",
    amount=10
)
print(minted_tokens)
```

**Output**:
```plaintext
[302808, 302809, 302810, 302811, 302812, 302813, 302814, 302815, 302816, 302817]
```

---

### **4. Get Balances**
Retrieve balances of ETH, ERC20, and ERC721 tokens for a specific Stark key.

**Method**: `get_balances(stark_key, page=1, limit=10)`

**Parameters**:
- `stark_key` *(string)*: The Stark key to fetch balances for.
- `page` *(int, optional)*: Page number (default = 1).
- `limit` *(int, optional)*: Number of records per page (default = 10).

**Example**:
```python
balance = reddio.get_balances(
    stark_key="0x6ecaebbe5b9486472d964217e5470380782823bb0d865240ba916d01636310a"
)
print(balance)
```

---

### **5. Transfer NFT**
Transfer NFTs between Stark keys.

**Method**: `transferNFT(stark_private_key, starkkey, receiver, token_type, contract, tokenID, expiration_timestamp=4194303)`

**Parameters**:
- `stark_private_key` *(string)*: Sender's private key.
- `starkkey` *(string)*: Sender's Stark key.
- `receiver` *(string)*: Recipient's Stark key.
- `token_type` *(string)*: "ERC721" or "ERC721M".
- `contract` *(string)*: The token's contract address.
- `tokenID` *(string)*: The token ID to transfer.
- `expiration_timestamp` *(int, optional)*: Expiry time (default = 4194303).

**Example**:
```python
reddio.transferNFT(
    stark_private_key="your_private_key_here",
    starkkey="0x6ecaebbe5b9486472d964217e5470380782823bb0d865240ba916d01636310a",
    receiver="0x1ada455b26b246260b7fd876429289639d7a0ce5fe295ff2355bd4f4da55e2",
    token_type="ERC721",
    contract="0x941661Bd1134DC7cc3D107BF006B8631F6E65Ad5",
    tokenID="618"
)
```

---

### **6. Withdraw NFT**
Withdraw NFTs from Layer 2 back to Layer 1.

**Method**: `withdrawNFT(stark_private_key, starkkey, receiver, token_type, contract, tokenID, expiration_timestamp=4194303)`

**Parameters**:
- `stark_private_key` *(string)*: Sender's private key.
- `starkkey` *(string)*: Sender's Stark key.
- `receiver` *(string)*: Recipient's Stark key.
- `token_type` *(string)*: "ERC721" or "ERC721M".
- `contract` *(string)*: The token's contract address.
- `tokenID` *(string)*: The token ID to withdraw.
- `expiration_timestamp` *(int, optional)*: Expiry time (default = 4194303).

**Example**:
```python
reddio.withdrawNFT(
    stark_private_key="your_private_key_here",
    starkkey="0x6ecaebbe5b9486472d964217e5470380782823bb0d865240ba916d01636310a",
    receiver="0xffc882996cFAB2C8B9983394E09bb025a98e52bc",
    token_type="ERC721",
    contract="0x941661Bd1134DC7cc3D107BF006B8631F6E65Ad5",
    tokenID="663"
)
```

---

### **7. Other Methods**
- **`buy_nft`**: Purchase an NFT on Layer 2.
- **`sell_nft`**: List an NFT for sale on Layer 2.

*(Detailed documentation for these methods coming soon.)*

---

## **Security Best Practices**
1. **Keep Private Keys Secure**: Store keys securely, e.g., in environment variables or a key vault.
2. **API Key Management**: Avoid hardcoding API keys in source code.
3. **Validate Input**: Ensure parameters such as `contract_address` and `stark_key` are properly formatted.

---

## **Contributing**
Contributions are welcome! Submit a pull request or open an issue to help improve the SDK.

---

## **License**
This project is licensed under the MIT License.






