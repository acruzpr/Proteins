import numpy as np 
import math

#Makes 2-d array of all conforms 
#Access conform 1, contact 0 by conform = getConforms conform[1][0]
def getConforms():
  with open("idLineAlltest_100.txt","r") as file:
    #conforms = [0] * 50000
    conforms = [0] * 100
    indexcount = 0 
    for line in file:
      shape = list(line)
      if '\n' in shape:
	shape.remove('\n')
      shape = [int(i) for i in shape]
      conforms[indexcount] = shape
      indexcount += 1
    return conforms

def get1Conform(conform):
  with open("idLineAlltest_100.txt","r") as file:
    i = 0 
    for line in file:
      if i == conform: 
	shape = list(line)
	if '\n' in shape:
	  shape.remove('\n')
	shape = [int(i) for i in shape]
        return shape
      i+=1

def getSums(i):
  return sum(get1Conform(i))


def getNij(i,j):
  conform1 = get1Conform(i)
  conform2 = get1Conform(j)
  counter = 0
  for i in range(len(conform1)):
    if conform1[i] == 1 and conform2[i] == 1:
	counter += 1
  return counter 
	
def getnegd(i,j):
  nij = getNij(i,j)
  ni = getSums(i)
  nj = getSums(j)
  num = float(nij)/(ni+nj)
  num *=2.0
  num = 1.0 - num 
  return num * -1

#START -->INPUT 
def makeW():
  conforms = getConforms()
  size = len(conforms)
  w = np.empty([size,size])
  for (i,j), value in np.ndenumerate(w):
      w[i][j] = np.exp(getnegd(i,j))
      w[j][i] = np.exp(getnegd(i,j))
  return w 



#with open("Nij1000.txt","a") as file:
  #for i in range(1000):
    #for j in range(i+1,1000):
      #file.write("%d\n"%getNij(i,j))

#with open("weights1000.txt","a") as file:
  #W = makeW()
  #for i in range (len(W)):
    #for j in range(i+1,len(W)):
      #file.write("%f\n"%W[i][j])
    #start += 1
#''''   
