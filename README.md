<details>
  <summary>Table of Contents</summary>
  <ul>
    <li><a href="#coding-style">Coding Style</a>
      <ul>
        <li><a href="#documentation">Documentation</a></li>
        <li><a href="#indentations-and-spaces">Indentation & Spaces</a></li>
        <li><a href="#naming">Naming</a></li>
      </ul>
    </li>
    <li><a href="#type-annotation">Type Annotation</a></li>
    <li><a href="#formatting-with-black-and-isort">Formatting with Black and isort</a></li>
    <li><a href="#references">References</a></li>
  </ul>
</details>


## Coding Style

### Documentation

🧱 **Module**
```py
"""A one-line summary

Detailed descriptions for the module or program.
You may include 'how to run this' or 'usage of functions/classes'

"""
```

📦 **Function**
```py
def function_name(args):
    """Function Description shortly

    More details for this class...
    More details for this class...

    Args:
        arg_name: description

    Returns:
        what to return
    
    Raises:
        error_type: why we get this error
    """
```

🎁 **Class**
```py
class ClassName:
    """A one-line summary

    More details for this class...
    More details for this class...

    Attributes:
        attrib_name: description
    """
```

### Indentations and Spaces

🗞 **Parentheses**

```py
# YES: 괄호 내 문자 시작 지점에 정렬
foo = long_function_name(var_one, var_two,
                         var_three, var_four)
meal = (spam,
        beans)

# YES: 4 space (1 Tab) 들여쓰기 & 닫는 괄호 붙여쓰기
foo = long_function_name(
    var_one, var_two, var_three,
    var_four)
meal = (
    spam,
    beans)

# YES: 4 space (1 Tab) 들여쓰기 & 닫는 괄호 새 줄에 쓰기
foo = long_function_name(
    var_one, var_two, var_three,
    var_four
)
meal = (
    spam,
    beans,
)

# NO: 넘어가는 줄에만 space / Tab
foo = long_function_name(var_one, var_two,
    var_three, var_four)
meal = (spam,
    beans)
```

📝 **String**

Preferee `"` for long string

```py
# One Tab (= 4 spaces)
long_string = """This is fine if your use case can accept
    extraneous leading spaces."""

# Use parentheses
long_string = ("And this is fine if you cannot accept\n" +
               "extraneous leading spaces.")
long_string = ("And this too is fine if you cannot accept\n"
               "extraneous leading spaces.")

# textwarp
import textwrap

long_string = textwrap.dedent("""\
    This is also fine, because textwrap.dedent()
    will collapse common leading spaces in each line.""")
```

📦 **Function signature**

```py
def my_method(
    self,
    first_var: int,
    second_var: Foo,
    third_var: Bar | None,
) -> int:

# spaces around `=` if the argument have type annotation & default value
def func(a: int = 0) -> int:
```


### Naming
- Package / module - `package_name` , `module_name`
  - DO NOT use dashes(`-`)
- Function - `function_name`
- Variable
  - Global Constant - `GLOBAL_CONSTANT_NAME`
  - others - `var_name`
- Class - `ClassName`
- Exception - `ExceptionName`

Here's a guideline from [Gudio](https://en.wikipedia.org/wiki/Guido_van_Rossum)

|Type|	Public|	Internal|
|---|---|---|
|Packages               |`lower_with_under`   |                   |
|Modules                |`lower_with_under`     |`_lower_with_under`  |
|Classes                |`CapWords`           |`_CapWords`          |
|Exceptions             |`CapWords`           |               	|
|Functions              |`lower_with_under()` |`_lower_with_under()`|
|Global/Class Constants |`CAPS_WITH_UNDER`    |`_CAPS_WITH_UNDER`   |
|Global/Class Variables |`lower_with_under`   |`_lower_with_under`  |
|Instance Variables     |`lower_with_under`   |`_lower_with_under` (protected)|
|Method Names           |`lower_with_under()` |`_lower_with_under()` (protected)|
|Function/Method Parameters|`lower_with_under`|                   |
|Local Variables        |`lower_with_under`   |                   |

<br><br><br>

## Type Annotation

👉 `var: type = value`

```py
# Variables
path: str = '/home/winterbloooom/foo.txt'
paths: list = [path1, path2, path3]

# Functions
def show_paths(paths: list, max_num: int = 3) -> str:
  return 'done'
```

👉 Using `typing` module

```py
from typing import List, Dict

food: List[str] = ['banana', 'apple']
students: Dict[str, int] = {'eungi': 100, 'winterbloooom': 99}
```

<br><br><br>

## Formatting with Black and isort

- [Black](https://black.readthedocs.io/en/stable/index.html) for Python code formatting
- [isort](https://pycqa.github.io/isort/) for Python import sorting

### 1. Install VSCode extensions

- [Black Formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter) (by Microsoft)
- [isort](https://marketplace.visualstudio.com/items?itemName=ms-python.isort) (by Microsoft)

### 2. Settings
 1. `command + shift + p`
 2. `Preferences: Open User Settings (JSON)`
 3. Insert code blow
   
```json
"[python]": {
    "diffEditor.ignoreTrimWhitespace": false,
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
},
"isort.args":["--profile", "black"],
```

<br><br><br>

## References
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)
- [Documenting Python Code: A Complete Guide](https://realpython.com/documenting-python-code/#basics-of-commenting-code)
- [Blog - 파이썬 타입 어노테이션/힌트](https://www.daleseo.com/python-type-annotations/)
- [Blog - typing 모듈로 타입 표시하기](https://www.daleseo.com/python-typing/)
