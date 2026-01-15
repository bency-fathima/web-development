# bcrypt.hash(password, 10) – Detailed Explanation

This document explains the following line used in authentication systems (MERN stack):

```js
const hashedPassword = await bcrypt.hash(password, 10);
1. What is bcrypt?
bcrypt is a password hashing library used to securely store passwords.

Passwords should never be stored as plain text.

bcrypt converts a plain password into an irreversible hashed string.

❌ Wrong:

vbnet
Copy code
password: "123456"
✅ Correct:

perl
Copy code
password: "$2b$10$K9s82j..."
2. What is Hashing?
Hashing is:

One-way process

Cannot be reversed

Same password produces different hashes every time (due to salt)

Example:

perl
Copy code
"123456" → $2b$10$A92ks...
"123456" → $2b$10$P0x8d...
3. Breaking the Code Line
js
Copy code
const hashedPassword = await bcrypt.hash(password, 10);
password
Plain text password from frontend

Example:

js
Copy code
password = "123456"
bcrypt.hash()
Syntax:

js
Copy code
bcrypt.hash(plainPassword, saltRounds)
Example:

js
Copy code
bcrypt.hash("123456", 10)
4. What is Salt?
Salt is random data added to the password before hashing.

Purpose:

Prevent rainbow table attacks

Ensure same password never produces same hash

5. What are Salt Rounds (10)?
Salt rounds define how many times hashing runs internally.

Salt Rounds	Security	Speed
8	Low	Fast
10	✅ Balanced (Recommended)	
12+	High	Slow

👉 Industry standard is 10

6. Why use await?
bcrypt.hash() is asynchronous.

js
Copy code
await bcrypt.hash(...)
Waits for hashing to finish

Prevents saving unresolved Promise

Without await:

javascript
Copy code
Promise { <pending> }
7. Output of bcrypt.hash()
Example hashed password:

perl
Copy code
$2b$10$Fj92kR8K1pL4x8KpTz...
This contains:

Algorithm identifier ($2b$)

Salt rounds (10)

Salt

Final hash

8. Why Hashing Instead of Encryption?
Encryption	Hashing
Can be decrypted	❌ Cannot be reversed
Uses secret key	No key needed
Not ideal for passwords	✅ Best for passwords

👉 Passwords must always be hashed, not encrypted.
