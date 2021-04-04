from functools import reduce
from timeit import timeit


def even_fib_simple(f=10):
    """Функция принимает аргумент - количество четных чисел Фибоначчи 
    и возвращает генератор этих чисел.

    Вызывается исключение если аргумент меньше единицы.

    Parameters
    ----------
    x1, x2 : int
        первые два числа последовательнсти Фибоначчи
    i : int
        счетчик увеличивается до заданного f

    """
    
    if f <= 0:
        raise ValueError(f'The argument f must be greater than zero, it is {f}')
    else:
        x1, x2, i = -1, 1, 0
        while i != f:
            if (x1 + x2) % 2 == 0:
                yield x1+x2
                i += 1
            x1, x2 = x2, x1+x2


#рекурсия
def fib(f):
    """Функция принимает аргумент - номер числа последовательности Фибоначчи 
    и возвращает это число.

    Parameters
    ----------
    x1, x2 : int
        первые два числа последовательнсоит Фибоначчи
    
    """
    x1, x2 = 0, 1
    if f == 1:
        return x1
    elif f == 2:
        return x2
    else:
        return fib(f-2) + fib(f-1)

def even_fib_rec(f=10):
    """Функция принимает аргумент - количество четных чисел Фибоначчи 
    и возвращает генератор этих чисел.

    Вызывается исключение если аргумент меньше единицы.

    Parameters
    ----------
    i : int
        счетчик найденных четных чисел
    inf : int
        количество найденных чисел Фибоначчи   
    temp : int
        вспомогательная переменная хранения промежуточного результата 
    """
    
    if f <= 0:
        raise ValueError(f'The argument f must be greater than zero, it is {f}')
    else:
        i, inf = 0, 1
        while i != f:
            temp = fib(inf)
            inf += 1
            if temp % 2 == 0:
                yield temp
                i += 1
    

#ооп
class even_fib_oop:
    """Функция принимает аргумент - количество четных чисел Фибоначчи 
    и возвращает генератор этих чисел.

    Вызывается исключение если аргумент меньше единицы.

    Объект класса можно вызвать как функцию и передать в него аргументы

    Attributes
    ----------
    x1, x2 : int
        первые два числа последовательнсоит Фибоначчи
    i : int
        счетчик увеличивается до заданного f

    Methods
    -------
    __call__()
        Принимает аргумент f как размер итогового списка
        Генерирует последовательность Фибоначчи
        и возвращает результат в виде списка только четных чисел
    """
    x1, x2, i = -1, 1, 0

    def __call__(self, f=10):

        if f <= 0:
            raise ValueError(f'The argument f must be greater than zero, it is {f}')
        else:
            while self.i != f:
                if (self.x1 + self.x2) % 2 == 0:
                    yield self.x1 + self.x2
                    self.i += 1
                self.x1, self.x2 = self.x2, self.x1 + self.x2

#кратчайшая
def even_fib_tri(f=10):
    """Функция принимает аргумент - количество четных чисел Фибоначчи 
    и возвращает генератор этих чисел.

    Каждое третье число последовательности Фибоначчи
    четное, оно и выводится.

    Вызывается исключение если аргумент меньше единицы.

    Parameters
    ----------
    x1, x2 : int
        первые два числа последовательнсти Фибоначчи
    """

    if f <= 0:
        raise ValueError(f'The argument f must be greater than zero, it is {f}')
    else:
        x1, x2 = 0, 1
        for _ in range(f):
            yield x1
            x1, x2 = 2*x2 + x1, 3*x2+2*x1


#функциональщина

#one line - one love
#even_fib = lambda f, x1 = 0, x2 = 1: [x1, x2 = x2, x1+x2 for i in range(f) if x1 % 2 == 0]
#even_fib = lambda f, x1 = 0, x2 = 1: x1, x2 = x2, x1+x2 if (x1+x2) % 2 == 0  
#even_fib0 = lambda f, x1 = 0, x2 = 1: [x1, x2 = x2, x1+x2 for i in [x1+x2 for ] if x1 % 2 == 0]
#even_fib0 = lambda f, x1=0, x2=1, x3=1: x1 += x2#[(lambda x1, x2: x1 += x2, x1)[1] for i in range(f)]
#even_fib1 = lambda f: [i for i in map(lambda x,f=lambda x,f:(x<=1) or (f(x-1,f)+f(x-2,f)): f(x,f), range(f))]
#lambda n: reduce(lambda x,y:(x[0]+x[1],x[0]),[(1,1)]*(n-2))
even_fib_func = lambda f=10: [i for i in [(lambda n:reduce(lambda x,n:[x[1],x[0]+x[1]], range(n),[0,1])[0])(n) for n in range(f*3)] if i % 2 == 0]

#print(reduce(lambda x,t:(x[0]+x[1],x[0]),[(1,1)]*(2)))
#print((lambda z: z.append(1))([1]))

#print(sum(map(lambda x: x*2, [i for i in range(4)])))

#even_fib_lamb = lambda n=10,x=(-1,1):[x := (x[1], sum(x)) for i in range(n+1)][0::3]

#самый короткий однострочник
even_fib_lamb = lambda n, f=(2,-1): list(zip(*[f := (f[0] + f[1]*2, 2*f[0]+3*f[1]) for _ in range(n)]))[0]
print(*even_fib_lamb(5))




print('ввести количество элементов:', end='')
Fi = int(input())
even_fib_oop = even_fib_oop()

print(*even_fib_lamb(Fi), end='')
print(f"  самый крутой однострочник эвер  время выполнения: {timeit(f'even_fib_lamb({Fi})', setup='from __main__ import even_fib_lamb', number=10)}")

print(*even_fib_tri(Fi), end='')
print(f"  каждый третий                   время выполнения: {timeit(f'even_fib_tri({Fi})', setup='from __main__ import even_fib_tri', number=10)}")

print(*even_fib_simple(Fi), end='')
print(f"  простая                         время выполнения: {timeit(f'even_fib_simple({Fi})', setup='from __main__ import even_fib_simple', number=10)}")

print(*even_fib_oop(Fi), end='')
print(f"  ооп                             время выполнения: {timeit(f'even_fib_oop({Fi})', setup='from __main__ import even_fib_oop', number=10)}")

print(*even_fib_func(Fi), end='')
print(f"  функциональная                  время выполнения: {timeit(f'even_fib_func({Fi})', setup='from __main__ import even_fib_func', number=10)}")

print(*even_fib_rec(Fi), end='')
print(f"  рекурсивная                     время выполнения: {timeit(f'even_fib_rec({Fi})', setup='from __main__ import even_fib_rec', number=10)}")
