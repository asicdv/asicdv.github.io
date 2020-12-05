---
layout: page
title: Static vs Automatic
description: Exploring static and automatic 
---

In short what is static and automatic in system verilog.

|           | Static                     | Automatic                  |
|-----------|----------------------------|----------------------------|
| Memory    | Permanant(BSS, DATA).      | Temporary(Stack).          |
| Life-time | Throughout the simulation. | Until the method finishes. |
| Variables | Module & Program           | Class                      |
| Methods   | Module                     | Class                      |

## STATIC
* By default all <ins>function/variable</ins> inside a module is **static**, unless declared **automatic**. 
* If a <ins>function</ins> as **automatic**, all the <ins>variables</ins> inside the function will be **automatic**, unless a specific <ins>variable</ins> is declared as **static**.
* Although by default <ins>functions</ins> are **static**, you can specifically declare it as **static** and required <ins>variables</ins> as **automatic**.

## AUTOMATIC
* By default all <ins>function/variable</ins> inside a class is **automatic**, unless declared **static**. 
* If a function as **static**, all the <ins>variables</ins> inside the function will be **static**, unless a specific <ins>variable</ins> is declared as **automatic**.
