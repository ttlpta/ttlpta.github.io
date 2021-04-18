## Mục lục - Table of content
1, JS - Closure : [VI]  - https://ttlpta.github.io/closure-javascript.html \
2, Lập trình - Nên học gì tiếp? : [VI] - https://ttlpta.github.io/decide-what-to-learn.html \
3, Thư gửi con trai - sinh nhật 1 tuổi : [VI] - https://ttlpta.github.io/letter-to-my-son.html \
4, Nhật ký làm chồng : [VI] - https://ttlpta.github.io/hpbd-vo-tui.html \
5, JS - Quick Tip 1 : Tránh thực hiện nhiều request API liên tiếp nhau : [VI] - https://ttlpta.github.io/avoid-serial-request.html \
6, JS - Quick Tip 2 : 10 câu hỏi hay gặp khi phỏng vấn vị trí JS : [VI] - https://ttlpta.github.io/10-tips-interview-javascript.html 

============================ NOTE ======================================

## Goodbye, Object Oriented Programming

https://medium.com/@cscalfani/goodbye-object-oriented-programming-a59cda4c0e53

1, Kế thừa :
* Banana Monkey Jungle Problem 


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


## Improve Performance in React.js Using Hooks
1, useCallback (memoize function) : Khi gặp trường hợp render với vòng lặp : 
>
    handleClick = (id) => {
        alert(id);
    }

    {
        items.map((item, idx)) => {
            return (<p onClick={ () => handleClick(item.id) }>{idx}</p>)
        });
    }


Việc này sẽ dẫn đến những re-render không cần thiết. Ta có thể cải thiện bằng cách : 

>
    handleClick = (id) => {
        alert(id);
    }

    {
        items.map((item, idx)) => {
            return (<p onClick={ useCallback( () => handleClick(item.id), [item]) }>{idx}</p>)
        });
    }

2, useMemo (Expensive Computations) : Khi gặp những phép toán phức tạp trước khi render ra view. Việc sử dụng useMemo sẽ giúp cache lại kết quả của phép tính trc, tránh việc phải tự động tính toán lại. Sẽ tính toán lại khi items truyền vào thay đổi
>
    import React, { useMemo } from 'react';

    const Dropdown = ({ items, onClick }) => {
    const memoizedValue = useMemo(() => {
        // This code will only run on initial render
        // and when "items" changes
        return items
        .filter(item => item < 5)
        .map(item => item + 3);
    }, [items]);
    
    return (...); // Returns some JSX
    }

## How to reuse react hooks
https://blog.bitsrc.io/simple-code-reuse-with-react-hooks-432f390696bf
>
    import { useState } from "react";

    export const useRandomColor = (colors, initialColor) => {
    const lenColors = colors.length;
    const [color, setColor] = useState(initialColor);

    const changeColor = () => {
        const index = Math.floor(Math.random() * lenColors);
        const pickedColor = colors[index];
        setColor(pickedColor);
    };

    return [color, changeColor];
    };


    // REUSE changeColor

    import React from "react";
    import { useRandomColor } from "./useRandomColor";

    export const ColoredBanner = () => {
        const colors = ["red", "blue", "green", "black"];
        const [color, changeColor] = useRandomColor(colors, "red");

        return (
            <div style={{
                textAlign: "center",
                padding: "20px 0",
                backgroundColor: color
            }} >
                <h2 style={{ color: "#fff" }}>Click below button to change Color</h2>
                <br />
                <button onClick={changeColor}>Change</button>
            </div>
            );
    };


## Top animation React
https://blog.bitsrc.io/11-javascript-animation-libraries-for-2018-9d7ac93a2c59

## Top JS library
https://blog.bitsrc.io/11-javascript-utility-libraries-you-should-know-in-2018-3646fb31ade


## Call vs Apply

Call và apply đều là để 1 function được viết thực hiện được ở 1 opject khác. Args thứ 1 là object sẽ thực hiện method đó , còn args thứ 2 là params truyền vào function . Khác nhau giữa call và apply là truyền mảng và truyền từng tham số

Hàm call
>   
    var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
    var person2 = {firstName: 'Kelly', lastName: 'King'};

    function say(greeting1, greeting2) {
        console.log(greeting1 + ',' + greeting2 + ' ' + this.firstName + ' ' + this.lastName);
    }

    say.call(person1, 'Hello', 'Good morning'); // => Hello,Good morning Jon Kuperman
    say.call(person2, 'Hello', 'Good morning'); // => Hello,Good morning Kelly King


Hàm Apply 
> 
    var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
    var person2 = {firstName: 'Kelly', lastName: 'King'};

    function say(greeting0, greeting1) {
        console.log(greeting0 + ',' + greeting1 + ' ' + this.firstName + ' ' + this.lastName);
    }

    say.apply(person1, ['Hello', 'Good moring']); // => Hello,Good moring Jon Kuperman
    say.apply(person2, ['Hello', 'Good moring']); // => Hello,Good moring Kelly King


Hàm Bind
>  
    var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
    var person2 = {firstName: 'Kelly', lastName: 'King'};

    function say(greeting0, greeting1) {
        console.log(greeting0 + ',' + greeting1 + ' ' + this.firstName + ' ' + this.lastName);
    }

    var sayHelloJon = say.bind(person1, 'Hello', 'Good morning');
    var sayHelloKelly = say.bind(person2, 'Hello', 'Good morning');

    sayHelloJon(); // => Hello,Good morning Jon Kuperman
    sayHelloKelly(); // => Hello,Good morning Kelly King

## Using the DOM like a Pro
To select a single element using any valid CSS selector use:
>
    document.querySelector('.foo')            // class selector
    document.querySelector('#foo')            // id selector
    document.querySelector('div')             // tag selector
    document.querySelector('[name="foo"]')    // attribute selector
    document.querySelector('div + p > span')  // you go girl!

Multiple elements
>
    document.querySelectorAll('p')  

Tips for making selector like Jquery
>
    const $ = document.querySelector.bind(document);
    $('#container');
    const $$ = document.querySelectorAll.bind(document);
    $$('p');

Going up the DOM tree
>
    document.querySelector('p').closest('div').closest('.content');

Adding elements
>
    const link = document.createElement('a');
    a.setAttribute('href', '/home');
    a.className = 'active';
    a.textContent = 'Home';
    document.body.appendChild(link);
Moving elements
>
    <!-- beforebegin -->
    <p>
    <!-- afterbegin -->
    foo
    <!-- beforeend -->
    </p>
    <!-- afterend -->
>
    <div class="first">
        <h1>Title</h1>
    </div>
    <div class="second">
        <h2>Subtitle</h2>
    </div>

and the h2 is inserted after the h1:
>
    const h1 = document.querySelector('h1');
    const h2 = document.querySelector('h2');
    h1.insertAdjacentElement('afterend', h2)

MutationObserver : Watch element when its attributes change

https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver
>
    // Select the node that will be observed for mutations
    const targetNode = document.getElementById('some-id');

    // Options for the observer (which mutations to observe)
    const config = { attributes: true, childList: true, subtree: true };

    // Callback function to execute when mutations are observed
    const callback = function(mutationsList, observer) {
        for(let mutation of mutationsList) {
            if (mutation.type === 'childList') {
                console.log('A child node has been added or removed.');
            }
            else if (mutation.type === 'attributes') {
                console.log('The ' + mutation.attributeName + ' attribute was modified.');
            }
        }
    };

    // Create an observer instance linked to the callback function
    const observer = new MutationObserver(callback);

    // Start observing the target node for configured mutations
    observer.observe(targetNode, config);

    // Later, you can stop observing
    observer.disconnect();
    
## Use reduce to increase performance in loop

>   
    // Navi way
    const counter = {
		next: 0,
		step() {
		  return ++this.next;
		},
		reset() {
		  this.next = 0;
		}
	};

	const getNum = () => counter.step(); 
	
	const halve = x => x / 2;
	const isInt = x => Math.floor(x) === x;
	console.time('time-solution1');
	const bigArray = new Array(10000000).fill(0);
	
	const newArray = bigArray
        .map(getNum) // Function để tạo ra dãy số tự động tăng
        .map(halve)
        .filter(isInt);
        
        console.log('===>', newArray);
        console.timeEnd('time-solution1'); // time-solution1: 2593.798095703125ms

    // Reduce way 

	const newArray = bigArray.reduce(newArr => {
		const x = getNum();
		const hlv = halve(x);
		if (isInt(hlv)) {
		  newArr.push(hlv);
		}
		return newArr;
	}, []);
    
    console.log('===>', newArray);
    console.timeEnd('time-solution2'); // time-solution2: 1438.924072265625ms

## Function curry how to write add(2)(3)(4)

>    
    function fixCurry(fn, totalArgs){
        totalArgs = totalArgs ||fn.length
            return function recursor(){
                return arguments.length<totalArgs?recursor.bind(this, ...arguments): fn.call(this, ...arguments);
            }
    }

    var add = fixCurry((a,b,c)=>a+b+c); //fn = summation function
    > console.log(add(1,2, 3))  // output: 6
    > console.log(add(1)(2,3)) // output: 6
    > console.log(add(1)(3)(2)) // output: 6
    > console.log(add(1,2)(3)) // output: 6

## No for/while
>
    const getElements = (selector) => {
        return Array.from(document.querySelectorAll(selector));
    };

    const getRemover = (el) => {
        return (className) => {
            el.classList.remove(className);
            return el;
        };
    };

    const els = getElements('.box')
        .map(getRemover)
        .map(removeClass => removeClass('hide'));

    console.log(els);

## Function Composition : Compose

>   
    const compose = (...fns) => {
        return fns.reduce((f, g) => (x) => f(g(x)));
    };
    const quăng_cho_tao_cái_thớt = compose(móc, chà, khoan, bào, sấy, cưa); // móc, chà, khoan, bào .. là function
    const thớt = quăng_cho_tao_cái_thớt('khúc gỗ');
    console.log(thớt); 

## Function Composition : Pipe ( Ngược chiều với compose )

> 
    const pipe = (...fns) => {
        return fns.reduce((f, g) => (x) => g(f(x)));
    };

## Elegant patterns in modern JavaScript: Ice Factory

>
    // Prevent this
    
    export default class ShoppingCart {
        constructor({db}) {
            this.db = db
        }
        
        addProduct (product) {
            this.db.push(product)
        }
        
        empty () {
            this.db = []
        }
        get products () {
            return Object
            .freeze([...this.db])
        }
        removeProduct (id) {
            // remove a product 
        }
        // other methods
    }
    // someOtherModule.js
    const db = [] 
    const cart = new ShoppingCart({db})
    cart.addProduct({ 
    name: 'foo', 
    price: 9.99
    })

    // Instead by this : Ice Factory
    
    export default function makeShoppingCart({
        db
    }) {
        return Object.freeze({
            addProduct,
            empty,
            getProducts,
            removeProduct,
            // others
        })
        function addProduct (product) {
            db.push(product)
        }
        
        function empty () {
            db = []
        }
        function getProducts () {
            return Object
            .freeze([...db])
        }
        function removeProduct (id) {
            // remove a product
        }
        // other functions
        }
    // someOtherModule.js
    const db = []
    const cart = makeShoppingCart({ db })
    cart.addProduct({ 
        name: 'foo', 
        price: 9.99
    })

    // cart.getProducts();

    // How to inheritance : Right now use object composition instead of inheritance to reuse.

    function makeProductList({ productDb }) {
        return Object.freeze({
            addProduct,
            empty,
            getProducts,
            removeProduct,
            // others
        )}
        
        // definitions for 
        // addProduct, etc…
    }

    function makeShoppingCart(productList) {
        return Object.freeze({
            items: productList,
            someCartSpecificMethod,
            // …
        )}

        function someCartSpecificMethod () {
            // code 
            }
        }
    }

    const productDb = []
    const productList = makeProductList({ productDb })
    const cart = makeShoppingCart(productList)

## How to do this console.log(obj.a, obj.a, obj.a) => "1", "2", "3"?

>
    Solution 1: 

    const obj = {
        get a(){
            console.log('trigger get a');
        }
        set a(value) {
            console.log('trigger set a: ', value);
        }
    }

    obj.a // trigger get a;
    obj.a = 1 // trigger set a: 1

    // ===== 

    const obj = {
        _initValue: 0,
        get a() {
            _initValue++;
            return this._initValue;
        }
    }

    console.log(obj.a, obj.a, obj.a) // "1", "2", "3"

    // ===== 

    Solution 2: 

    let obj = {}
    Object.defineProperty(obj, 'a', {
        get: (
            function(){
                let initValue = 0;
                return function(){
                    initValue++;
                    return initValue
                }
            })()
        }
    )
    console.log(obj.a, obj.a, obj.a)

    Solution 3: 

    let initValue = 0;
    let obj = new Proxy({}, {
    get: function(item, property, itemProxy){
        if(property === 'a'){
        initValue++;
        return initValue
        }
        return item[property]
    }
    })
    console.log(obj.a, obj.a, obj.a)





