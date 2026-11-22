# Advanced Calculator in JavaScript & Python

One calculator, two languages. This repo is the source code for the CorePulse video **"Advanced Calculator in JavaScript & Python"**: five calculation modes, written side by side in JavaScript and Python, giving the same answers.

▶️ **Watch the video:** `https://youtube.com/@CorePulseOffical` *(replace with the video link once it's live)*

| Mode | What it does |
| --- | --- |
| 🔬 **Scientific** | sin, cos, tan (in degrees), log, ln, square root, power, factorial |
| 💻 **Programmer** | Binary, octal and hex conversion, any base to decimal, AND / OR / XOR |
| 📏 **Unit converter** | Length, mass and temperature |
| 🏦 **Loan EMI** | Monthly instalment for any loan amount, interest rate and tenure |
| 📊 **Statistics** | Mean, median and sample standard deviation |

No libraries and no installs. JavaScript uses only built-in `Math`; Python uses only the built-in `math` module.

---

## Contents

- [Quick start](#quick-start)
- [Project structure](#project-structure)
- [API reference](#api-reference)
- [How it works](#how-it-works)
- [JavaScript vs Python: small differences](#javascript-vs-python-small-differences)
- [Run the tests](#run-the-tests)
- [Practice ideas](#practice-ideas)
- [License](#license)

---

## Quick start

Download the repo (**Code → Download ZIP**) or clone it:

```bash
git clone https://github.com/YOUR-USERNAME/advanced-calculator-js-python.git
cd advanced-calculator-js-python
```

### JavaScript (Node.js)

You need [Node.js](https://nodejs.org) 14 or newer.

```text
$ node
> .load calc.js
> scientific.sin(30)
0.5
> emi(500000, 8.5, 60)
10258.27
```

You can also paste `calc.js` into your browser's developer console (F12 → Console) and call the same functions there.

### Python

You need Python 3.8 or newer.

```text
$ python -i calc.py
>>> scientific["sin"](30)
0.5
>>> emi(500000, 8.5, 60)
10258.27
```

The `-i` flag runs the file and then leaves you at the `>>>` prompt with every function ready to use.

---

## Project structure

```text
advanced-calculator-js-python/
├── calc.js              # JavaScript version (exactly as typed in the video)
├── calc.py              # Python version (exactly as typed in the video)
├── tests/
│   ├── test_calc.js     # 19 checks for the JavaScript version
│   └── test_calc.py     # the same 19 checks for the Python version
├── README.md
└── LICENSE
```

---

## API reference

Every example below is a real output, the same as in the video.

### 🔬 Scientific

Angles are in **degrees**.

| Function | JavaScript | Python | Example → result |
| --- | --- | --- | --- |
| Sine | `scientific.sin(d)` | `scientific["sin"](d)` | `sin(30)` → `0.5` |
| Cosine | `scientific.cos(d)` | `scientific["cos"](d)` | `cos(60)` → `0.5` |
| Tangent | `scientific.tan(d)` | `scientific["tan"](d)` | `tan(45)` → `1` |
| Log base 10 | `scientific.log(x)` | `scientific["log"](x)` | `log(1000)` → `3` |
| Natural log | `scientific.ln(x)` | `scientific["ln"](x)` | `ln(10)` → `2.302585093` |
| Square root | `scientific.sqrt(x)` | `scientific["sqrt"](x)` | `sqrt(144)` → `12` |
| Power | `scientific.pow(x, y)` | `scientific["pow"](x, y)` | `pow(2, 10)` → `1024` |
| Factorial | `scientific.fact(n)` | `scientific["fact"](n)` | `fact(5)` → `120` |

### 💻 Programmer

| Function | JavaScript | Python | Example → result |
| --- | --- | --- | --- |
| To binary | `programmer.toBin(n)` | `programmer["to_bin"](n)` | `42` → `'101010'` |
| To octal | `programmer.toOct(n)` | `programmer["to_oct"](n)` | `64` → `'100'` |
| To hex | `programmer.toHex(n)` | `programmer["to_hex"](n)` | `255` → `'FF'` |
| Any base to decimal | `programmer.fromBase(s, base)` | `programmer["from_base"](s, base)` | `("1010", 2)` → `10` |
| Bitwise AND | `programmer.and(a, b)` | `programmer["and"](a, b)` | `(12, 10)` → `8` |
| Bitwise OR | `programmer.or(a, b)` | `programmer["or"](a, b)` | `(12, 10)` → `14` |
| Bitwise XOR | `programmer.xor(a, b)` | `programmer["xor"](a, b)` | `(12, 10)` → `6` |

### 📏 Unit converter

```js
convert(value, from, to, kind)        // JavaScript
convert(value, frm, to, kind)         # Python ("from" is a reserved word in Python)
```

| `kind` | Units |
| --- | --- |
| `"length"` | `m`, `km`, `cm`, `mi`, `ft` |
| `"mass"` | `kg`, `g`, `lb` |
| `"temp"` | `C`, `F` |

| Example | Result |
| --- | --- |
| `convert(5, "km", "mi", "length")` | `3.1068559612` |
| `convert(100, "C", "F", "temp")` | `212` |
| `convert(98.6, "F", "C", "temp")` | `37` |
| `convert(10, "kg", "lb", "mass")` | `22.0462262185` |

### 🏦 Loan EMI

```js
emi(principal, annualRate, months)    // JavaScript
emi(principal, annual_rate, months)   # Python
```

| Loan | Call | Monthly EMI |
| --- | --- | --- |
| ₹5,00,000 at 8.5% for 5 years | `emi(500000, 8.5, 60)` | `10258.27` |
| ₹25,00,000 at 9% for 20 years | `emi(2500000, 9, 240)` | `22493.15` |
| ₹1,20,000 at 0% for 1 year | `emi(120000, 0, 12)` | `10000` |

### 📊 Statistics

Pass a list (array) of numbers.

| Function | JavaScript | Python | `[4, 8, 15, 16, 23, 42]` → |
| --- | --- | --- | --- |
| Mean | `stats.mean(xs)` | `stats["mean"](xs)` | `18` |
| Median | `stats.median(xs)` | `stats["median"](xs)` | `15.5` |
| Standard deviation | `stats.stdev(xs)` | `stats["stdev"](xs)` | `13.4907375632` |

---

## How it works

**Clean results.** Computers store decimals in binary, so `sin(30°)` comes out as `0.49999999999999994`. Results that can pick up this noise are rounded to 10 decimal places: `round()` in JavaScript (`+x.toFixed(10)`) and `r()` in Python (`round(x, 10)`).

**Degrees, not radians.** Trig functions convert first: `deg × π / 180` in JavaScript (`toRad`), and `math.radians` in Python.

**One lookup object per mode.** Each mode is a small object (JavaScript) or dictionary (Python) that maps a name to a function. That keeps the code short and easy to extend: adding a function is one new line.

**Unit conversion through a base unit.** Each unit stores how many base units it equals (metres for length, kilograms for mass). To convert, multiply by the "from" factor and divide by the "to" factor:

```text
5 km → mi  =  5 × 1000 ÷ 1609.344  =  3.1068559612
```

Temperature isn't a simple ratio, so it converts to Celsius first and then to the target with `C × 9/5 + 32`.

**The EMI formula.** With monthly rate `i = annual rate ÷ 12 ÷ 100` and `n` months:

```text
EMI = P × i × (1 + i)ⁿ ÷ ((1 + i)ⁿ − 1)
```

A 0% loan is a special case (the formula would divide by zero), so it returns `principal ÷ months`. Results are rounded to 2 decimals, like money.

**Sample standard deviation.** `stdev` divides by `n − 1`, not `n` (Bessel's correction). That's the usual choice when your numbers are a sample, and it matches Python's `statistics.stdev`.

---

## JavaScript vs Python: small differences

The answers are the same, but the two languages print and behave a little differently:

| | JavaScript | Python |
| --- | --- | --- |
| Whole-number results | `3`, `12`, `212` | `3.0`, `12.0`, `212.0` when the math produced a float |
| Calling a mode function | `scientific.sin(30)` | `scientific["sin"](30)` (dictionary key) |
| Factorial | Recursive; past about 9 × 10¹⁵ (`Number.MAX_SAFE_INTEGER`) large results may be approximate | `math.factorial` gives exact big integers, e.g. `fact(50)` |
| Bitwise operators | Work on 32-bit integers | Work on integers of any size |
| Keyword clash | `from` is fine as a parameter | `from` is reserved, so the parameter is `frm` |

---

## Run the tests

Both test files check the same 19 results.

```bash
node tests/test_calc.js
python tests/test_calc.py
```

Each prints `ok` for every check and ends with `All 19 ... checks passed.`

---

## Practice ideas

Try these after watching, in both languages:

1. **More units:** add `inch`, `yard` and `ounce`, or a whole new kind such as `"speed"` (km/h, mph).
2. **Kelvin:** extend `"temp"` to support `K`.
3. **Mode and range:** add `mode` (the most common value) and `range` (max − min) to statistics.
4. **EMI schedule:** return a month-by-month table of interest paid, principal paid and balance left.
5. **Input checks:** return a clear error for `sqrt(-1)`, `log(0)`, unknown units or an empty list.
6. **A real UI:** build a web page with buttons for each mode on top of `calc.js`.

Built something? Share it in the video's comments.

---

## License

MIT. Use this code in your own projects, freely.

**CorePulse:** trading tech skills and updates. Subscribe on YouTube: **@CorePulseOffical**
