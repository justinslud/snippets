## outline of app
have main.py with sidebar options
if/elif/else for sidebar options with each option calling a function in another file

## writing
st.write(anything) # text, DataFrame, python dict, list etc

st.title(title of page)
st.subheader(text)

st.markdown()
st.latex()

## cache
@st.cache
def ... # not sure why not just use cache

## layout (columns)
left_column, right_column = st.beta_columns(num_cols)
right_column.selectbox(...)

### expander
expander = st.beta_expander('section title')
expander.write('mytext')

### place holder
holder = st.empty()
holder.text(text)

## componenets
st.sidebar.[other component]

### selection
st.selectbox(name, [option1, option2])
st.selectbox(name, df[col])

### text input
st.text_input('your text below!', 'default text')

### progress bar
latest_iteration = st.empty()
bar = st.progress(0)
for i in range(100):
	latest_iteration.text(f'Iteration {i+1}')
	bar.progress(i + 1)
	time.sleep(0.1)

### slider
slider = st.slider('name', min, max, default)

### button
btn = st.button('text')
if btn: ...

### code block
code = st.code('code here', language='python') # don't need langauge

### radio
rad = st.radio('these are radio buttons', ['option1', 'option2', ...])

### other
st.number_input()
st.text_area() # multiline
st.date_input()
st.file_uploader() 

## plotting

st.line_chart()
st.bar_chart()

### bokeh
from bokeh.plotting import figure
p = figure(...)
p.line(...)
st.bokeh_chart(p)

### matplotlib
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.line(...)
st.pyplot(fig)
