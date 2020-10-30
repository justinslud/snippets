
#  libraries
library()
require()
search() # gives installed packages

## list of libs
profviz (timing)
gapminder (data)
dplyr (for pipes %>%)


# save / export
save(x, "data.Rda")
saveRDS(object, 'object.Rds')
rm(x)

new <- readRDS('objet.Rds')
new_data <- load('x.Rda')


# ggplot

ggplot(df, aes(x, y, color, size)) + geom_something() + 
  xlab('xlabel') + geom_title(title) + theme()
geom_line()
geom_point()
geom_hist(),
geom_boxplot()

# go to url
browse_URL(url)

# range
start:end
seq(end_inclusive)
seq(start, end, by)

# math (built-in) and stats
sqrt()
sd() # standard deviation
round()
rep() # repeats


# python-like built-in useful
length()
nchar() # for strings
lapply(function, vector)
gsub(to_find, to_replace, string) # replaces
rev() # reverse
append(list, elem)

# for / while

# linear regression
lm(y ~ x, data=df)

# summary
summarize(new=fctn(feature))

group_by(feature) # then can %>% summarize(...)

# function
f <- function(a, b=1)
	a + b # can do return(a+b)

args(fctn) # lists params

# dataframe
df <- dataframe()
df <- as.data.frame(data)
df <- read.csv(file)

df.names # columns, same as attributes(df)

## can remove things you don't want
new_df <- df[-c(row1_unwanted, other:nums), -c(cols_unwanted)]

subset(df, cond, select=c('feature1', 'feature2'))
select(filter(df, cond), c(feature1, feature2))

# typecasting / coercing / types
as.integer()
typeof(var)
class(var)
is.vector()

# sorting
arrange(feature) # or arrange(desc(feature))

# mutate
mutate(new_feature = recode(
  old_feature, 'val1' = 'new_val1',
  default='def'))

# ifelse

number <- as.numeric(readline(prompt='Enter max number to check: '))
number <- ifelse(number %% 2 == 0, number-1, number)

if (number %% 2 == 0) {
  number <- number - 1
} else if (number %% 3 == 0) {
	break # or next
}

# io

name = readline(prompt="Name: ")
print(paste("My name is", name, "and what is your name?"))
view(df) # ?

stop(text) # raises error

# syntactic sugar / good examples
