---
layout: page
title: Polymorphism(virtual methods and class) and Casting
description: Overview of construction of a website with GitHub Pages
date: 2020-10-12 02:27 -0400
---

* You can assign child class handle to parent class(up-casting), vice-versa is not allowed.
* Using $cast is a safer way to do the up-casting.
* After up-casting(parent=child), if you call parent non-virtual function the function call is resolved based on the object type(which is parent's function).
* After up-casting(parent=child), if you call parent virtual function the function call is resolved based on the handle type(which is child's function).

```systemverilog
class base_class;  
  int addr;
  string base="base class";
  
  function void display();
    $display("In %0s because non-virtual function is called Addr = %0d",base, addr);
  endfunction
  
  virtual function void vdisplay();
    $display("In %0s because virtual function is called Addr = %0d",base, addr);
  endfunction  
endclass : base_class
 
class child_class extends base_class;

  string child="child class";
  
  function void display();
    $display("In %0s because non-virtual function is called Addr = %0d",child, addr);
  endfunction
  
  virtual function void vdisplay();
    $display("In %0s because virtual function is called Addr = %0d",child, addr);
  endfunction   
endclass : child_class
 
module inheritence;
  initial begin
    base_class base=new();
    child_class child1=new();
    child_class child2;
    
    child1.addr = 5;
    base.addr = 10;
    
    $display("--------Before Assignment/Up-Casting----------");
    child1.vdisplay();
    base.vdisplay();
	
    //Below both statements are prohobited 
    //child1=base; 		 //Prohibited: assigning parent class handle to child class handle 
    //$cast(child1,base);//Prohibited: Downcasting 
    
    //Below both statements are same and allowed 
    //base = child1;      //Allowed: assigning child class handle to parent class handle
    $cast(base, child1); //Allowed: Upcasting 
    
    $display("---------After Assignment/Up-Casting---------");
    child1.display();
    base.display();
    
    child1.vdisplay();
    base.vdisplay();
    
    $display("------------Up-Casting------------");
    //child2=base; //Prohibited: assigning parent class handle(although it points to child1) to child class handle
    $cast(child2,base);
    child2.display();
    child2.vdisplay();
  end
endmodule
```