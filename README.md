# BTC HashRoll
https://happydao.github.io/BTC.RollDraw/

Public and verifiable winning ticket generator powered by Bitcoin block hashes.

HOW HASHROLL WORKS

HashRoll uses the hash of a future Bitcoin block to generate a public and verifiable winning ticket.

Since nobody can know a block hash before the block is mined, the result cannot be predicted in advance and can be independently verified by anyone.

--------------------------------------------------

STEP 1

Choose a future Bitcoin block.

Example:

Bitcoin Block = 950000

Wait for the block to be mined.

Retrieve the block hash from:

https://mempool.space

Example block hash:

000000000000000000f7a83d91bc1ea2b6c54d8fa3e7c21ab91d3f8e29bb2919

--------------------------------------------------

STEP 2

Convert the hash into a number.

Bitcoin hashes use hexadecimal format (base 16):

0 1 2 3 4 5 6 7 8 9 A B C D E F

Values:

A = 10
B = 11
C = 12
D = 13
E = 14
F = 15

Formula:

H = Σ(dᵢ × 16ⁱ)

Where:

H = number obtained from the hash conversion
dᵢ = character value
i = character position

Simple example:

Hash:

1A3

Values:

1 = 1
A = 10
3 = 3

Calculation:

H = (1×16²)+(10×16¹)+(3×16⁰)

H = 256+160+3

H = 419

For a real Bitcoin hash, the system automatically converts the entire sequence into a very large number:

H = 279483729483729847239847239847239847239847...

(The actual number may contain many digits)

--------------------------------------------------

STEP 3

Divide the converted number by the total amount of tickets.

Formula:

C = H ÷ T

Where:

H = converted hash number
T = total number of tickets
C = wheel step count

Example:

H = 256

T = 10

C = 256 ÷ 10

C = 25

(The decimal part is discarded)

--------------------------------------------------

STEP 4

Move the circular wheel forward by C steps.

Wheel formula:

V = ((C−1) mod T)+1

Where:

V = winning ticket
C = wheel step count
T = total number of tickets

Example:

Wheel:

1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9 → 10
→ 1 → 2 → 3 → ...

Since:

C = 25

the wheel moves forward by 25 steps:

Step 1 = Ticket 1
Step 2 = Ticket 2
...
Step 10 = Ticket 10
Step 11 = Ticket 1
...
Step 25 = Ticket 5

--------------------------------------------------

WINNER:

Ticket number 5

--------------------------------------------------

Anyone can repeat the same calculation using the public Bitcoin block hash and obtain exactly the same result.

This makes the process public, transparent, and independently verifiable by anyone.
