
# TinyVM Python

![Python](https://img.shields.io/badge/Python-3.12%2B-blue?logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![Version](https://img.shields.io/badge/Version-v9.1-brightgreen)

**TinyVM** – pure Python'da yozilgan stack-based Python bytecode interpreter.  
Python 3.12+ bytecode'ini qo'llab-quvvatlaydi va ko'p muhim xususiyatlarni amalga oshiradi.

Bu loyiha o'quv maqsadida yaratilgan bo'lib, Python VM ichki ishini chuqur tushunish uchun ideal.

## Xususiyatlar

- **Python 3.12+ qo'llab-quvvatlash** (RESUME, CACHE, RETURN_CONST, KW_NAMES skip)
- **Stack-based execution** va to'g'ri frame management
- **CALL_FUNCTION** va **CALL_FUNCTION_KW** – positional, keyword args va defaults
- **Nested funksiyalar** va **closures** (MAKE_FUNCTION, LOAD_DEREF, STORE_DEREF)
- **If/while shartlari** (COMPARE_OP, POP_JUMP_IF_FALSE/TRUE, JUMP_FORWARD)
- **List, tuple, dict yaratish** (BUILD_LIST, BUILD_TUPLE, BUILD_MAP)
- **Builtins fallback** (len, print, sum va boshqalar)
- **Exception handling** (stack trace bilan)
- **Toza va type-hinted kod** – o'qish va kengaytirish oson

## O'rnatish

Loyiha qo'shimcha kutubxona talab qilmaydi – faqat Python 3.8+.

```bash
git clone https://github.com/sudoxlite/tinyvm-python.git
cd tinyvm-python
```

## Ishlatish

```python
from tinyvm import TinyVM

def test_func(a, b):
    def inner(x, y=1):
        return x * y
    return a + inner(b, y=2)

vm = TinyVM()
result = vm.run_code(test_func.__code__, globals=globals(), locals={'a': 10, 'b': 5})
print(result)  # 10 + (5 * 2) = 20
```

Yoki to'g'ridan-to'g'ri skriptni ishga tushirish:

```bash
python tinyvm.py
```

## Test misoli (tinyvm.py ichida)

```python
def inner(x, y=1):
    return x * y

def test_func(a, b):
    return a + inner(b, y=2)

vm = TinyVM()
result = vm.run_code(test_func.__code__, globals=globals(), locals={'a': 3, 'b': 4})
print(f"VM result: {result}")  # Natija: 11
```

## Kengaytirish

Loyiha oson kengaytirilishi uchun mo'ljallangan. Quyidagilarni qo'shish mumkin:

- To'liq `FOR_ITER` va loops
- `TRY_EXCEPT` va exception table
- `IMPORT` mekanizmi
- Ko'proq builtins va method calls

## Muallif

- **GitHub**: [@sudoxlite](https://github.com/sudoxlite)
- **Telegram**: [@pythondev_www](https://t.me/pythondev_www)

Fikr-mulohaza, taklif yoki yordam uchun bemalol yozing!

## License

Bu loyiha **MIT License** bilan tarqatiladi – erkin ishlatish, o'zgartirish va tarqatish mumkin.

Batafsil: [LICENSE](LICENSE) faylida ko'ring.
