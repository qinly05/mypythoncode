# mypythoncode

import itertools


n = 10
op = ['', '+', '-']
lst = [None]*(n*2-1)

for e in range(n*2-1):
    if (e+2) % 2 == 0:
        lst[e] = str((e+2)//2)

def cats(lst):
    s = ''
    for e in lst:
        s += e
        s = s.replace(' ','')
    return s

for x in itertools.product(' +-', repeat=n-1):
    for i in range(len(x)):
        lst[i*2+1] = x[i]
    if eval(cats(lst)) == 100 :
        print(cats(lst),'=',100)
