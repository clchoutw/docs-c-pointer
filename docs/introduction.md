---
layout: post
title: Introduction
subtitle: make pointers less confusing
tags:
  - draft
comments: false
published: false
---


# Goal of the Docs


The pointer in C is powerful but confusing. We can understand pointer better if we
think it logically and use it concisely. This document is trying to
bridge the gap between logic thinking and concise usage.


# Target of a Pointer

The target of a pointer could be NULL, a normal variable, a pointer variable, a function, an array, a structure, or a string.
The target must be defined first, assign its address to a pointer,
then use the pointer to indirectly access the target.


# Dimensional Analysis

Pointers are used to store memory address. 
Dereferencing pointers can access memory content including data, address, and code.


### Description

#### Memory Address and Content

```
int v; // v is an integer variable
int a[5]; // a[] is an array with 5 integer variables a[0], a[1], ..., a[4]
int *p; // p is an integer pointer
int f(); // f() is a function which returns an integer
```


* Memory Address 

    + constant address `&v`: address of variable `v`
    + constant address `&p`: address of pointer `p`
    + constant address `a`: address of an array `a[]` (`&` is NOT needed for an array)
    + constant address `f`: address of a function `f()` (`&` is NOT needed for a function)
  
    
* Memory Content
    + variable `v`: memory content as data
    + pointer `p`: memory content as address
    + function `f()`: memory content as code

#### Assign a memory address to a pointer.

* pointer assignment `p = memory address` ... `DA OK`
* pointer assignment `p = data` ... `DA NG`


#### Dereference a pointer to access data.

* dereferencing pointer `*p = data` ... `DA OK`
* dereferencing pointer `*p = address` ... `DA NG`
* dereferencing pointer `data = *p` ... `DA OK`

### Examples

#### 1. Pointer to Data

```
data_type v, *pv;
pv = &v; // v is a variable, &v is its address

data_type a[5], *pa;
pa = &a[0] // think logically: a[0] is a variable, &a[0] is its address
pa = a // use concisely: a is array name and a = &a[0] 

```


* v: a normal variable
* pv: a pointer to a variable v
* a[]: an array of variables
* a: array name
* pa: a pointer to an array



##### address

* constant address (assigned by compiler): `&v`, `&pv`, `a`, `&a[0]`, `&a[1]`, ... 

* changeable address variable (changeable during runtime): `pv`, `pa`

##### data

* direct access: `v`, `a[0]`, `a[1]`, ..., `f()`
* indirect access: `*pv`, `*pa`, `pa[0]`, `*(pa+1)`, `pa[1]`, ..., `(*pf)()`


#### 2. Pointer to Function

```
data_type fd(), (*pfd)();
pfd = &fd; // thinking
pfd = fd; // usage

data_type *fa(), *(*pfa)();
pfa = &fa;
pfa = fa;
```

* fd(): a function that returns data
* fd: function name
* pfd: a pointer to a funciton fd()
* fa(): a function that returns address
* fa: function name
* pfa: a pointer to a function fa()


##### address

* constant address: `&fd`, `fd`, `&fa`, `fa`
* changeable address variable: `pfd`, `pfa`
* address returned by fa(): `fa()`, `(*pfa)()`

##### data

* data returned by fd(): `fd()`, `(*pfd)()`

