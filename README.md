# Table of contents
1. [HOW TO TABEL OF CONTENT](#HOWTOTABELOFCONTENT)
2. [Print a float with thousands separators](#Printafloatwiththousandsseparators)
3. [Clickable pandas dataframe](#Clickablepandasdataframe)
4. [Interactive labeling of images in jupyter notebook](#interactivelabeling)


<br/>

## HOW TO TABEL OF CONTENT <a name="HOWTOTABELOFCONTENT"></a> [(link)](https://stackoverflow.com/questions/11948245/markdown-to-create-pages-and-table-of-contents/33433098#33433098)


___
1. [Template Text](#tempLink1)

## Template Text <a name="tempLink1"></a>
Text Paragraph "Template Text"
___

<br/>


# Table of contents
1. [Introduction](#introduction)
2. [Some paragraph](#paragraph1)
    1. [Sub paragraph](#subparagraph1)
3. [Another paragraph](#paragraph2)

## This is the introduction <a name="introduction"></a>
Some introduction text, formatted in heading 2 style

## Some paragraph <a name="paragraph1"></a>
The first paragraph text

### Sub paragraph <a name="subparagraph1"></a>
This is a sub paragraph, formatted in heading 3 style

## Another paragraph <a name="paragraph2"></a>
The second paragraph text
___
<br/>

# Print a float with thousands separators <a name="Printafloatwiththousandsseparators"></a> [(link)](https://stackoverflow.com/questions/13082620/how-can-i-print-a-float-with-thousands-separators)

```python
import re
def sep(s, thou=",", dec=".", roundTo=None):
    if roundTo == None:
        integer, decimal = str(s).split(".")
        integer = re.sub(r"\B(?=(?:\d{3})+$)", thou, integer)
        return integer + dec + decimal
    else:
        newS = str(round(s,roundTo))
        integer, decimal = newS.split(".")
        integer = re.sub(r"\B(?=(?:\d{3})+$)", thou, integer)
        return integer + dec + decimal
```

```s = float("5255918.87898331")
sep(s, roundTo=2)
```
___
<br/>

# Clickable pandas dataframe <a name="Clickablepandasdataframe"></a> [(link)](https://stackoverflow.com/questions/43832898/use-jupyter-widgets-to-save-clicks-on-a-pandas-dataframe)

```python
import pandas as pd
from IPython.display import display, HTML
from ipywidgets import Button, HBox, VBox,widgets
import ipywidgets


df = pd.DataFrame([[1,'car'],[2,'bus'],[3,'train']])

click_list = []

button = widgets.Button(description='click')
def obc(b):
    click_list.append((pd.to_datetime('now'),1)) 
button.on_click(obc)

button2 = widgets.Button(description='click')
def obc2(b):
    click_list.append((pd.to_datetime('now'),2))
button2.on_click(obc2)

button3 = widgets.Button(description='click')
def obc3(b):
    click_list.append((pd.to_datetime('now'),3)) 
button3.on_click(obc3)
```

```python
display(HBox([VBox([widgets.Button(description=''),button,button2,button3]),ipywidgets.
                    HTML(df.style.set_table_attributes('class="table"').render())]))
```
___
<br/>

# Interactive labeling of images in jupyter notebook <a name="interactivelabeling"></a> [(link)](https://stackoverflow.com/questions/54921711/interactive-labeling-of-images-in-jupyter-notebook)

```python
COLS = 4
ROWS = 2
IMAGES = ...
IMG_WIDTH = 200
IMG_HEIGHT = 200

def on_click(index):
    print('Image %d clicked' % index)

import ipywidgets as widgets
import functools

rows = []

for row in range(ROWS):
    cols = []
    for col in range(COLS):
        index = row * COLS + col
        image = widgets.Image(
            value=IMAGES[index], width=IMG_WIDTH, height=IMG_HEIGHT
        )
        button = widgets.Button(description='Image %d' % index)
        # Bind the click event to the on_click function, with our index as argument
        button.on_click(functools.partial(on_click, index))

        # Create a vertical layout box, image above the button
        box = widgets.VBox([image, button])
        cols.append(box)

    # Create a horizontal layout box, grouping all the columns together
    rows.append(widgets.HBox(cols))

# Create a vertical layout box, grouping all the rows together
result = widgets.VBox(rows)
```

