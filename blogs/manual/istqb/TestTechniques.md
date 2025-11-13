# 📘 Chapter 4: Test Techniques
Test techniques are structured methods used to design test cases. They help testers:
- Maximize coverage
- Reduce effort
- Improve defect detection

These techniques fall into three categories:
- Black-box
- White-box
- Experience-based

## 🔹 1. Black-box Test Techniques
<b>Focus:</b> Testing based on inputs and outputs, without knowing internal code.

### ✅ 1.1 Equivalence Partitioning (EP)
<b>What it is:</b> Divide input data into groups (partitions) that are expected to behave similarly. Test one value from each group.

<b>Example:</b> For an age field accepting 18–65:
<br/><b>Valid partition:</b> 18–65 → test with 30
<br/><b>Invalid partitions:</b> <18 and >65 → test with 17 and 70
<br/><b>Hint:</b> Reduces number of test cases while maintaining coverage.

#### Sample Question:

Q: What does Equivalence Partitioning help achieve? 
<br/>
A. Test all code paths 
<br/>B. Reduce redundant test cases 
<br/>C. Test performance 
<br/>D. Test user interface 
<br/>✅ Correct Answer: B

### ✅ 1.2 Boundary Value Analysis (BVA)

<b>What it is:</b> Test the edges of input ranges — where defects often occur.
<b>Example:</b> For age 18–65:
<b>Test:</b> 17, 18, 65, 66
<b>Hint:</b> Always test just below, at, and just above boundaries.

#### Sample Question:

Q: Which values are best for Boundary Value Analysis of 1–100? 
<br/>A. 0, 1, 100, 101 
<br/>B. 50, 75 
<br/>C. 1, 50, 100 
<br/>D. 10, 20, 30 
<br/>✅ Correct Answer: A

### ✅ 1.3 Decision Table Testing
<b>What it is:</b> Use a table to represent rules and actions. Helps test combinations of inputs.

<b>Example:</b>

| Promo Code | Payment Method | Discount Applied |
|------------|----------------|------------------|
| Yes        | Credit Card    | Yes              |
| No         | Credit Card    | No               |
| Yes        | Cash           | No               |

> 💡 **Hint:** Great for business logic and rule-based systems.

### Sample Question:

Q: What is the purpose of a decision table? 
<br/>A. To test UI layout 
<br/>B. To test combinations of conditions and actions 
<br/>C. To test performance 
<br/>D. To test boundary values 
<br/>✅ Correct Answer: B

### ✅ 1.4 State Transition Testing
<b>What it is:</b> Test how the system behaves when moving between states.

<b>Example:</b> Login → Browse → Add to Cart → Checkout → Logout 
<br/>Test valid and invalid transitions (e.g., Checkout without login).

💡 **Hint:** Useful for systems with workflow or status changes.

#### Sample Question:

Q: What does State Transition Testing focus on? 
<br/>A. Input values 
<br/>B. Code structure 
<br/>C. System states and transitions 
<br/>D. User roles ✅ Correct Answer: C

### ✅ 1.5 Use Case Testing
<b>What it is:</b> Design tests based on user interactions and goals.
<b>Example:</b> “User places an order and tracks delivery.” Test each step in that journey.
💡 **Hint:** Helps ensure real-world scenarios are covered.

#### Sample Question:

Q: What is the focus of Use Case Testing? 
<br/>A. Code branches 
<br/>B. User journeys and goals 
<br/>C. Input partitions 
<br/>D. Performance metrics 
<br/>✅ Correct Answer: B

## 🔹 2. White-box Test Techniques
<b>Focus:</b> Testing based on internal code structure.

### ✅ 2.1 Statement Testing
<b>What it is:</b> Ensure every line of code is executed at least once.
<br/><b>Example:</b> If a login function has 10 lines, test cases must trigger all 10.
💡 **Hint:** Measures statement coverage.

#### Sample Question:

Q: What does statement testing aim to achieve? <br/>A. Test all user inputs <br/>B. Execute every line of code <br/>C. Test UI layout <br/>D. Test performance <br/>✅ Correct Answer: B

### ✅ 2.2 Decision Testing
<b>What it is:</b> Ensure every decision (if/else) outcome is tested.

Example: If a payment function has:

```python
if card_valid:
    process_payment()
else:
    show_error()
```
Test both paths.

💡 **Hint:** Measures decision coverage — more thorough than statement testing.

#### Sample Question:

Q: What does decision testing focus on? <br/>A. Executing all statements <br/>B. Testing all decision outcomes <br/>C. Testing all user roles <br/>D. Testing all UI elements <br/>✅ Correct Answer: B

## 🔹 3. Experience-Based Test Techniques
Focus: Use tester’s intuition, experience, and creativity.

### ✅ 3.1 Error Guessing
<b>What it is:</b> Guess where bugs might be based on past experience.
<b>Example:</b> “Users often forget passwords — test reset flow thoroughly.”

💡 **Hint:** Works well when documentation is limited.

#### Sample Question:

Q: What does Error Guessing rely on? 
<br/>A. Formal rules 
<br/>B. Tester’s experience and intuition 
<br/>C. Code coverage tools 
<br/>D. User feedback 
<br/>✅ Correct Answer: B

### ✅ 3.2 Exploratory Testing
<b>What it is:</b> Testers explore the system freely while learning about it.
<b>Example:</b> Tester uses the app without a script — finds a bug in the cart when switching languages.
💡 **Hint:** Great for early-stage testing or when time is short.

#### Sample Question:

Q: What is a key feature of exploratory testing? 
<br/>A. Predefined test cases 
<br/>B. Scripted execution 
<br/>C. Simultaneous learning and testing 
<br/>D. Automated tools 
<br/>✅ Correct Answer: C

### ✅ Summary Table
| Technique Type     | Key Focus        | Example                          |
|--------------------|------------------|----------------------------------|
| Black-box          | Inputs/outputs   | Age field, promo codes           |
| White-box          | Code structure   | If-else paths, loops             |
| Experience-based   | Tester intuition | Password reset, UI quirks        |

