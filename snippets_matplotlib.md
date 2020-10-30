# importing
%matplotlib inline
import matplotlib as mpl
import matplotlib.pyplot as plt

# plotting matlab style
plt.subplot(nrows, ncols, index)
plt.plot()
plt.text()
plt.show()

# plotting object oriented style
fig, ax = plt.subplots(nrows, ncols)
ax[0].plot()
ax[0].set(xlim=(4,5))

# pie
wedges, texts, autotexts = ax1.pie(x, labels)

# bar
ax.bar(heights, x, bottom: variable, yerr: list) # also barh

# style
plt.style.use('seaborn')

mpl.rcParams['figure.dpi']= dpi # btw 150 and 300 recommended for downloading, 80 is inline default
larger dpi like magnifying class - makes lines thicker

# plot params
alpha: int: line thickness, .01=>really thin

# save
fig.savefig('figname.png', dpi: int, ...)

# filling
ax.fill_between(x_values, lower_y, upper_y, color, alpha)

# legend

## seaborn
sns.despine()

# lineplot 


# barplot
plot = sns.barplot(x, y, ax=ax, palette="rocket")
plot.set(xticks=[])

# scatterplot
sns.scatterplot(x='3', y='7', data=nums, color='r', alpha=.5) #'3' and '7' are features of nums df

sns.scatterplot(x='1', y='3', data=nums, hue='lab', legend='full', markers='O', units='mpg')

# heatmap
f, ax = plt.subplots(figsize=(9, 6))
sns.heatmap(nums.iloc[:10,:10], annot=True, fmt="d", linewidths=.5, ax=ax) # only need first param

# relplot (linear)
sns.relplot(x='1', y='2', data=nums, ax=ax1, kind='line', estimator=None) # default kind produces dots

# jointplot (replot with histogram distributions)
sns.jointplot(x='2', y='3', data=nums) # can have 

# pairplot
sns.pairplot(data) # relplot for each combo of 2 vars with diagonal histogram
