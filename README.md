# random_walk

I was interested in this.   I learned about it in a course; but, here I was trying months later.   

I started with some ideas, eventually made a function and then a generator function so that it would be better able to handle memory issues associated with a very large walk.
I cannot remember if I was forced to make it more efficient like this or if I just wanted to try.  Oh yea, reading the comment, it seems like it was incapable of doing a walk greater than 1,000,000 steps until I made the function into a generator function. 
&nbsp;

random_walk_generator.py
&nbsp;

```python
import numpy
import random
import pylab

def random_walk(n):
   x = y = 0
   offsets = [ (0,1),(0,-1),(1,0),(-1,0)]  # ,(1,1),(-1,-1) ]
   for i in range(1, n):
      yield (x,y)
      dx,dy = random.choice(offsets)
      x,y   = x+dx, y+dy

# number of steps ( could not handle: 1000000)
n = int( input("How many steps in this random walk? ") )
x = numpy.zeros(n)
y = numpy.zeros(n)

for k,point in enumerate( random_walk(n) ):
   # print(point, end="\n")
   x[k],y[k] = point

# plotting stuff:
pylab.title("Random Walk ($n = " + str(n) + "$ steps)")
pylab.plot(x, y)
pylab.savefig("rand_walk_gen"+str(n)+".png",dpi=1000)  # bbox_inches="tight",dpi=600)
pylab.show()
```
