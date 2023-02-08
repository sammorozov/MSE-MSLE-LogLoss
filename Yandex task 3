import math
n, k = map(int, input().split())
a = []
b = []
for i in range(1, n+1):
    line = input().split()
    a.append(line[-2])
    b.append(line[-1])


t = []
for i in range(len(a)):
    t.append(float(a[i])/float(b[i]))
# print('t = ', t)
w = []
for i in range(len(a)):
    w.append(float(b[i]))


def mse(p):
    summ1 = 0
    summ2 = 0
    for i in range(n):
        summ1 += w[i] * ((t[i]) - p)**2
        summ2 += w[i]
    return summ1/summ2


def dmse(p):
    summ1 = 0
    summ2 = 0
    for i in range(n):
        summ1 += w[i] * -2 * (t[i] - p)
        summ2 += w[i]
    return summ1/summ2


def dmsle(p):
    summ1 = 0
    summ2 = 0
    for i in range(n):
        summ1 += w[i] * -2 * (math.log(1 + t[i]) - math.log(1 + p)) / (1 + p)
        summ2 += w[i]
    return summ1/summ2


c = max(t)


def dlogloss(p):
    summ1 = 0
    summ2 = 0
    for i in range(n):
        summ1 += - w[i] * ((t[i] / p) - (1 - t[i] / c) * (1 / (1 - p / c)))
        summ2 += w[i]
    return summ1 / summ2


N = 300
lmd = 0.1
p1 = 0
p2 = 0
p3 = 0.1
for j in range(N):
    p1 = p1 - lmd * dmse(p1)
    p2 = p2 - lmd * dmsle(p2)
    p3 = p3 - lmd * dlogloss(p3)


p1 = (round(p1, 6))
p2 = (round(p2, 6))
p3 = (round(p3, 6))

print(p1, p2, p3)
