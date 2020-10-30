

## plot figure
p = figure(plot_width, plot_height, title)
show(p)

## glyphs
p.circle(xs, ys, size) # or radius
p.square(xs, ys, size)
p.line(xs, ys, width, line_dash=[int, int])
p.scatter(xs, ys, line_width)

color
line_color
line_alpha
fill_color
fill_alpha
hover_alpha

## anotations
from bokeh.models.annotations import BoxAnnotation, Label

label = Label(x, y, x_offset, y_offset, text, text_baseline)
p.add_layout(label)

# widgets
## slider
from bokeh.models import RangeSlider
rs = RangeSlider(start, end, step, value(startmin, startmax, title)

## input text
from bokeh.models import TextInput
text = TextInput(title, value)
text.on_change('value', function)


## panel
- have widgets in row, row in layout, layour in Panel 
from ... import Panel
panel = Panel(child, title)
## notebook

## run server
bokeh serve app.py

## save

## sample datasets
from bokeh.sampledata.automtg import autompg as df
from bokeh.sample.data.stocks import AAPL

# figure

## tools
from bokeh.models.tools import HoverTool
p.add_tools(HoverTool(tooltips=None, mode='hline'))
mode can be 

## toolbar
tools = 'reset,save'
p = figure(..., tools=tools)
p.toolbar.logo = None

## grid
p.grid.grid_line_color
p.xgrid.grid_line_color
p.yaxis.axis_label

# checklists

## .

# dashboard

## file structure
bokeh_app
|
+--- data
|   +--- info.csv
|   +--- info2.csv
|
+--- scripts
|   +--- plot.py
|   +--- plot2.py
|
+--- main.py

- keep one script per tab then call them all in main

## tabs
from bokeh.io import curdoc
from bokeh.models.widgets import Tabs

tabs = Tabs(tabs=[tab1, tab2])
curdoc().add_root(tabs)
