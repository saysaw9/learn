import requests
import lxml
import cssselect

response = requests.get('https://parivahan.gov.in/rcdlstatus/?pur_cd=101')
print(response.text)

import requests
import lxml.html

response = requests.get('https://parivahan.gov.in/rcdlstatus/?pur_cd=101')
tree = lxml.html.fromstring(response.text)
title_elem = tree.xpath('//title')[0]
title_elem = tree.cssselect('title')[0]  # equivalent to previous XPath
print("title tag:", title_elem.tag)
print("title text:", title_elem.text_content())
print("title html:", lxml.html.tostring(title_elem))
print("title tag:", title_elem.tag)
print("title's parent's tag:", title_elem.getparent().tag)
