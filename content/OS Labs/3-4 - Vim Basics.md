
## Основы Vim

Установка:

```bash

sudo apt-get install vim

```

Режимы:

- **Командный** (Normal) — `Esc`

- **Редактирование** (Insert) — `i`, `a`, `o`

- **Визуальный** — `v`, `V`, `Ctrl-v`

Повторяющиеся команды:

- `20j` — вниз на 20 строк

- `5dd` — удалить 5 строк

- `3x` — удалить 3 символа

- `yy` — копировать строку, `p` — вставить

---

## Переменные окружения

### 2. printenv.py

```bash

python3 printenv.py

```

![[Pasted image 20260310010101.png]]

```bash

python3 printenv.py HOME NOT_EXISTING

```

![[Pasted image 20260310010112.png]]

### 3. set vs printenv

```bash

set | grep -E '^HOME=|^PATH='

python3 printenv.py HOME PATH

```

![[Pasted image 20260310010123.png]]

### 4. Inline-переменная

```bash

SOME_VAR=hello python3 printenv.py SOME_VAR

python3 printenv.py SOME_VAR

```

![[Pasted image 20260310010134.png]]

### 5–6. Экспорт и source

```bash

VAR_NO_EXPORT="no_export_value"

export VAR_EXPORT="export_value"

```

Прямой запуск (`bash script.sh`):

![[Pasted image 20260310010145.png]]

Через `source`:

![[Pasted image 20260310010156.png]]

**Вывод:** без `source` переменные живут только внутри скрипта. С `source` — они попадают в текущую оболочку.

### 7. sys.argv в printenv.py

```python

import sys

for arg in sys.argv[1:]:

...

```

![[Pasted image 20260310010207.png]]

---

## Права доступа

### 8–9. ls -l и chmod

```bash

ls -l /tmp/test_chmod.py

chmod a+x /tmp/test_chmod.py

ls -l /tmp/test_chmod.py

```

![[Pasted image 20260310010218.png]]

### 10. Восьмеричная нотация

```bash

chmod 755 file

chmod 644 file

```

### 11. Права на каталоги

`x` на каталоге — право входить в него (`cd`).

---

## Shebang

```bash

cat > /tmp/test_chmod.py << 'PY'

#!/usr/bin/env python3

print("Hello from chmod test")

PY

chmod a+x /tmp/test_chmod.py

/tmp/test_chmod.py

```

![[Pasted image 20260310010229.png]]

---

## Разные формы запуска bash

```bash

bash

# вложенный сеанс

VAR=test

exit

echo $VAR # пусто

```

```bash

bash -c 'echo $HOME; VAR=123; echo $VAR'

```

---

## find

```bash

find /tmp -name "*.py" -type f

find /tmp -name "test_*"

find /tmp -name "test_chmod.py" -exec ls -l {} \;

```

![[Pasted image 20260310010240.png]]

---

## См. также
- [[00 OS Labs MOC|К оглавлению OS Labs]]
