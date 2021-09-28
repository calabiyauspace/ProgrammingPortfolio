## Инвариантная СР. Исследовать функционал модуля requests
Исследовать функционал одного модуля requests и создать фрагмент ЭОР с описанием и примерами его использования при работе в Jupyter Notebook (Typora, встроенный редактор Markdown сервиса GitHub) и в скриптовом виде.


```python
# import requests

# def get_module(srv_path:str='localhost:8000', module_name:str='cool_module'):
#     r = requests.get(srv_path + '/' + module_name)
#     print(r)

# get_module()

import re
import sys
from urllib.request import urlopen
from importlib.abc import PathEntryFinder
from importlib.util import spec_from_loader
from urllib.request import urlopen


# sys.path_hooks.append(url_hook)

class URLFinder(PathEntryFinder):
    def __init__(self, url, available):
        self.url = url
        self.available = available

    def find_spec(self, name, target=None):
        if name in self.available:
            origin = "{}/{}.py".format(self.url, name)
            loader = URLLoader()
            return spec_from_loader(name, loader, origin=origin)

        else:
            return None


class URLLoader:
    def create_module(self, target):
        return None

    def exec_module(self, module):
        with urlopen(module.__spec__.origin) as page:
            source = page.read()
        code = compile(source, module.__spec__.origin, mode="exec")
        exec(code, module.__dict__)


def url_hook(some_str):
    """ С помощью этой функции мы перехватываем ситуацию, в которой то,
    что мы собираемся импортировать является URL-адресом"""
    if not some_str.startswith(("http", "https")):
        raise ImportError
    with urlopen(some_str) as page:
        data = page.read().decode("utf-8")
    filenames = re.findall("[a-zA-Z_][a-zA-Z0-0_]*.py", data)
    modnames = {name[:-3] for name in filenames}
    return URLFinder(some_str, modnames)
```


```python

```
