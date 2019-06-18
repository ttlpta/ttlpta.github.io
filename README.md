## Goodbye, Object Oriented Programming

https://medium.com/@cscalfani/goodbye-object-oriented-programming-a59cda4c0e53

1, Kế thừa :
* Banana Monkey Jungle Problem 

<p align='center'>
<img src="https://raw.githubusercontent.com/ttlpta/ttlpta.github.io/master/imgs/1.png">
</p>


## Learn Enough React For The Interview

https://medium.com/bb-tutorials-and-thoughts/learn-enough-react-for-the-interview-f460a2fa3aeb

1, What is Declarative Programming
* Mô hình lập trình tập trung vào bạn làm ra cái gì hơn là bạn làm thế nào. 
VD : 

>
    const numbers = [1,2,3,4,5];

    // declarative programming
    const doubleWithDec = numbers.map(number => number * 2);

    console.log(doubleWithDec)

    // imperative programming
    const doubleWithImp = [];
    for(let i=0; i<numbers.length; i++) {
        const numberdouble = numbers[i] * 2;
        doubleWithImp.push(numberdouble)
    }

    console.log(doubleWithImp)

2, What is Functional Programming
* Functional Programming là một phần của lập trình declarative. Functions trong JS là những hàm bạn có thể save , truy xuất và pass các functions này trong application giống những các variable
* Một số nội dung đặc trưng cho functional đó là : Immutability, Pure Functions, Data Transformations, Higher-Order Functions, Recursion, Composition



