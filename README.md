# Counting-Inversion-alorithm-in-python

#counts between two splits
def merge(a,b):
    c = []
    value = {}
    counts = 0
    while len(a) != 0 and len(b) != 0:
        if int(a[0]) < int(b[0]):
            c.append(a[0])
            a.remove(a[0])
        else:
            c.append(b[0])
            b.remove(b[0])
            counts = counts + len(a)
    if len(a) == 0:
        c += b
    else:
        c += a
    value['c'] = c
    value['counts'] = counts 
    return value
#return merged sorted array and counts for inversions between two splits
    
    
#sort and counts the inversions
def mergesort(x):
    value = {}
    if len(x) == 0 or len(x) == 1:
        value['sortvalue'] = x
        value['countst'] = 0
    else:
        middle = int(round(len(x)/2,0))
        avalue = mergesort(x[:middle])
        bvalue = mergesort(x[middle:])
        a = avalue['sortvalue']
        b = bvalue['sortvalue']
        acounts = avalue['countst'] 
        bcounts = bvalue['countst']
        priorvalue = merge(a,b)
        sortvalue = priorvalue['c']
        countst = priorvalue['counts'] + acounts + bcounts
        value['sortvalue'] = sortvalue
        value['countst'] = countst
    return value  
 #return sort array and total counts for inversion
    
 
