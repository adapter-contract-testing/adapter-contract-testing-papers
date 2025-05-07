🧪 Adapter Contract Testing & Simulators
====

➡️ For more reliable, simpler application testing, without fragile mocks.

----

### 🐛 A bug in production despite your tests?  

You've tested everything... but an unexpected behavior occurs in production. 
The cause? Often, **a mock** that does not faithfully simulate the service or database.<br>
What if you changed your approach?  

### 🎭 Simulators instead of mocks  

Rather than blindly mocking with a framework, we can **manually code a simulator**.<br>
A simple component, maintained within the project, that simulates **just what the application needs**.  

**💡 Why is it better?**  

 - The simulator behaves like a real service, with real business rules.  
 - It is more expressive than a mock: we can simulate specific errors, exchange sequences, and internal states.  
 - It makes business tests easier to write and much more reliable, as the testing environment is close to reality.  

**🛠️ Examples:**

 - For a third-party service: the simulator can generate realistic responses, precise errors, or simulate a typical production request sequence.  
 - For a database: we implement an in-memory version, capable of handling insertions, queries, and filtering rules.  

A well-designed simulator becomes a valuable tool in all application tests. And above all: **it replaces all mocks** for that dependency.

--- 

### 🔁 Adapter Contract Testing: the link between the real and the simulated  

But how do we ensure that this simulator behaves **like the real service**?<br>
➡️ This is where **Adapter Contract Testing** comes in.  

The idea:  
1. We write an integration test **against the real external service** (or a real database, or any uncontrolled dependency).  
2. This test becomes the expected **behavior contract**.  
3. We use the same test to validate our simulator.  

🎯 Result: a single test guarantees both:  

 - Integration with the external service works, without surprises  
 - The simulator faithfully reproduces this behavior.  
 - Consistency over time between reality and simulation

This is powerful, as it avoids drift between what we test and what happens in production. It also detects regressions due to partner changes.



### 🧩 Simplifying the interface = simplifying the test  

But to make this approach successful, the interface between the application and its dependency must be **clear and stable**.  


| It's not because the dependency does all this                      | that we want more than this.                         |
|--------------------------------------------------------------------|------------------------------------------------------------------|
| <img src="../swiss-knife-complex.png" alt="complex" height="220"/> | <img src="../swiss-knife-simple.png" alt="simple" height="220"/> |


👉 The less we expose the technical details of the dependency, the easier it is to:
 - write a simple contract,
 - develop a faithful simulator,
 - and maintain the whole over time.  
 
📐 **Domain Driven Design** and **hexagonal architecture** are two excellent sources of inspiration here:<br>
  They encourage designing business interfaces **centered on the actual use** of the dependency, not on its internal complexity.  
  
In other words: **by mastering the dependency**, we make testing much simpler and more robust.

---

###  ✅ In summary

<br> 🧩 We simplify the interface to our dependencies.  
<br> 🧪 We write an integration test that defines a behavior contract.  
<br> 🎭 We develop a simulator that adheres to this contract.  
<br> 🔁 This simulator replaces all mocks in our application tests.  
<br> ⚙️ Tests become simpler, more reliable, and closer to reality.

📚 For concrete examples:  
 - [Slides](https://adapter-contract-testing.github.io/presentation)
 - [Kata](https://github.com/adapter-contract-testing/snail-race-kata)

## See also  
### The 5 benefits
<br> ✅ More refactorability (of business and adapters)
<br> ✅ Integration without surprises  
<br> ☑️ More confidence in our tests at all levels (much fewer green tests with bugs in production)  
<br> ✅ Easy migration of dependencies  
<br> ☑️ Isolation of external complexity