# BTC HashRoll
https://happydao.github.io/BTC.RollDraw/

Public and verifiable winning ticket generator powered by Bitcoin block hashes.

## How it works

The winning ticket is determined using the hash of a future Bitcoin block. Since the block hash cannot be known before the block is mined, the result is transparent, public, and independently verifiable by anyone.

### Process

1. Choose a future Bitcoin block number.

2. Wait for the selected block to be mined.

3. Retrieve the block hash from:

https://mempool.space

4. Convert the Bitcoin block hash into a numerical value.

The Bitcoin block hash is represented in hexadecimal format (base 16).

Character values:

```text
0 = 0
1 = 1
2 = 2
...
9 = 9
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

Conversion formula:

```text
H = Σ(dᵢ × 16ⁱ)
```

Where:

- `H` = resulting numerical value
- `dᵢ` = character value
- `i` = character position

Simple example:

```text
Hash: 1A3

Values:

1 = 1
A = 10
3 = 3

H = (1×16²) + (10×16¹) + (3×16⁰)

H = 256 + 160 + 3

H = 419
```

5. Divide the converted number by the total amount of tickets:

```text
C = H ÷ T
```

Where:

- `H` = converted hash number
- `T` = total ticket amount
- `C` = wheel step count

6. Move through the circular wheel:

```text
1 → 2 → 3 → ... → 50,000 → 1 → 2 → ...
```

7. The ticket where the wheel stops becomes the winning ticket.

Winning formula:

```text
V = ((C − 1) mod T) + 1
```

Where:

- `V` = winning ticket
- `C` = wheel step count
- `T` = total tickets

---

This process allows anyone to independently verify the result using publicly available Bitcoin blockchain data.
