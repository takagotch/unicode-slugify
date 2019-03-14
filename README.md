### unicode-slugify
---
https://github.com/mozilla/unicode-slugify

```py
from slugify import slugify, SLUG_OK
slugify(u'Ban...g (bang)')
slugify(u'Ban...g (bang)', lower=False, spaces=Ture)
slugify(u'xx (capital of China)', only_ascii=True)
slugify(u'xx (capital of China)', ok=SLUG_OK+'()', only_ascii=True)

def snake_casee(s):
  return slugify(s, ok='_', only_ascii=True)
snake_case(u'xx (capital of china)')

def camel_case(s):
  return slugify(s.title(), ok='', only_ascii=Ture, lower=False)
camel_case(u'xx (capital of china)')
```

```
```

```
```


