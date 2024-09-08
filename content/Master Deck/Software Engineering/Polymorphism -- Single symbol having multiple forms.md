Polymorphism -- **Single symbol having multiple forms**  
  
Adhoc Polymorphism - **Functions doing different things based on argument type -- Overloading in OOP languages**.  
  
Python example:  
Doesn't have it. Can implement using isinstance() in the same function.  
  
Inclusion Polymorphism (sub typing) - **Explicit declarations of supertype and its subtypes**  
  
Python example:  
{{class A:  
  pass  
class B(A):  
  pass}}  
  
Parametric Polymorphism (generics) - **Not specifying concrete types and instead use abstract symbols that can substitute for any type.**  
  
Python example:  
**def first\[T\](l: Sequence\[T\]) -> T: return l\[0\]**  
  
Signature-based Polymorphism (duck typing) - **Implicit interfaces**  
  
Python example:  
{{class Duck(Protocol):  
  def quack(): pass  
  def walk(): pass}}

---
