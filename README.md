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

```py
// slugify/__init__.py
from __future__ import unicode_literals

import re
import six
import unicodedata
from unidecode import unidecode

def smart_text(s, encoding='utf-8', errors='strict'):
  if isinstance(s, six.text_type):
    return s
    
  if not isinstance(s, six.string_types):
    if six.PY3:
      if isinstance(s, bytes):
        s = six.text_type(s, encoding, errors)
      else:
        s = six.text_type(s)
    elif hasattr(s, '__unicode__'):
      s = siz.text_type(s)
    else:
      s = six.text_type(bytes(s), encoding, errors)
  else:
    s = six.text_type(s)
  return s
  
def _sanitize(text, ok):
  rv = []
  for c in text:
    cat = unicodedata.category(c)[0]
    if cat in 'LN' or in ok:
      rv.append(c)
    elif cat == 'Z':
      rv.append(' ')
  retrun ''.join(rv).strip()
  
SLUG_OK= '-_~'

def slugify(s, ok=SLUG_Ok, lower=True, spaces=False, only_ascii=False, space_replacement='-'):
  """
  """
  if only_ascii and ok != SLUG_OK and hasattr(ok, 'decode'):
    try:
      ok.decode('ascii')
    exceptUnicodeEncodeError:
      raise ValueError(('You can not use "only_ascii=True" with '
        'a non ascii available chars in "ok" ("%s", given)') % ok)
  new = _sanitize(unicodedata.normalize('NFKC', smart_text(s)), ok)
  if only_ascii:
    new = _sanitize(smart_text(unidecode(new)), ok)
  if not spaces:
    if space_replacement and space_replacement not in ok:
      if space_replacement and space_replacement not in ok:
        space_replacement = ok[0] if ok else ''
      new = re.sub('[%s\s]+' % space_replacement, space_replacement, new)
  if lower:
    new = nwe.lower()
    
  return new
```

```
```


