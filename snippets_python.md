
#pickle

pickle.dump(open('primes_under_million.p', 'w'), data)

p = pickle.load(open('primes_under_million.p', 'rb'))

#sqlite3 

conn = sqlite3.connect('books.db')
cursor = conn.cursor()

cursor.execute(command)
cursor.commit()

#csv

csv_reader = csv.reader(csv_file, delimiter=',')


csv_writer = csv.writer(open(file, 'w'), delimiter=',')
writer.writerow([thing1, thing2])

# string / print / format
f" {e-s:.0f} seconds" prints value of e - s with 0 decimal places as a float (so really like int)
print('hello, %' % var)

from string import punctuation, 

#ipython
timing
%%timeit

save to .py
%save current_session.py 0/

shift+tab for params

?function for documentation

!... for shell command



#argparse

parser = argparse.ArgumentParser()

parser.add_argument('-d', '--deck', 
                    help='deck name',
                    action='store')

parser.add_argument('-a', '--action', 
                    help='what do you want to do?',
                    choices=['add','remove', 'changeVariables'])

parser.add_argument('-i', '--info',
                    help='get info on deck(s)',
                    action='append')

args = parser.parse_args()

# datetime

import datetime as dt
dt.datetime.strptime('30MAR1990', '%d%b%Y')

%d = day num
%b = month abb
%B = month full
%m = month num
%y = year mod 100
%Y = year
%H = 24 hr
%M = minute
%S = second

# os

import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))


os.chdir(path)
os.exec(command)
os.listdir()
os.path.join('hi', 'there') # produce 'hi\\there'