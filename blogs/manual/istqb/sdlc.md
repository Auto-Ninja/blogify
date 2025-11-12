# 📘 Chapter 2: Testing Throughout the Software Development Lifecycle
## 🔹 2.1 Software Development Lifecycle Models
Testing activities vary depending on the development model used. Let’s explore the three most common models with a real-world example: building a food delivery app.

### 🧱 Waterfall Model
Sequential phases — each must finish before the next begins.

```Code
[Requirements] → [Design] → [Implementation] → [Testing] → [Deployment]
```
Example:

<br/><b>Requirements:</b> Define features like login, browse restaurants, place order.
<br/><b>Design:</b> Create UI and backend architecture.
<br/><b>Implementation:</b> Developers build the app.
<br/><b>Testing:</b> Happens only after development is complete.
<br/><b>Deployment:</b> App is released to users.

Hint: Testing is late-stage. Bugs found here are costly to fix.

### Sample Question:

Q: In which model is testing typically done after development is complete? 
<br/>A. Agile 
<br/>B. V-Model 
<br/>C. Waterfall 
<br/>D. Spiral 
<br/>✅ Correct Answer: C

### 🧩 V-Model

Testing is planned in parallel with development.  Each dev phase has a corresponding test phase.

```Code
Requirements → System Design → Architecture → Module Design → Coding
     ↓             ↓              ↓             ↓
Acceptance ← System ← Integration ← Unit Testing
```
Example:

<br/><b>Acceptance tests</b> are written during requirements.
<br/><b>System tests</b> are designed during system design.
<br/><b>Integration tests</b> align with architecture.
<br/><b>Unit tests</b> match module design.

Hint: Know the correspondence between dev and test phases.

### Sample Question:

Q: Which test level corresponds to the system design phase in the V-Model? 
<br/>A. Unit Testing 
<br/>B. Integration Testing 
<br/>C. System Testing 
<br/>D. Acceptance Testing 
<br/>✅ Correct Answer: C

### 🔁 Agile Model
Iterative and collaborative. Testing is continuous and integrated into each sprint.

```Code
[Plan] → [Design] → [Develop & Test] → [Review] → [Release]
             ↑         ↑
         Continuous Testing
```         
Example:
<br/>Sprint 1: Build and test login feature.
<br/>Sprint 2: Add restaurant filters.
<br/>Sprint 3: Implement payment gateway.

Hint: Testing is ongoing and adaptive.

### Sample Question:

Q: What is a key characteristic of testing in Agile? 
<br/>A. Performed only after development 
<br/>B. Conducted by a separate team 
<br/>C. Continuous and integrated into development <br/>D. Focused only on system testing 
<br/>✅ Correct Answer: C

## 🔹 2.2 Test Levels
Testing is performed at different levels to target different scopes.

| Test Level         | Description                             | Real-World Example                                      |
|--------------------|-----------------------------------------|----------------------------------------------------------|
| Component (Unit)   | Tests individual functions or modules   | Test login validation logic                              |
| Integration        | Tests interaction between components    | Login → Dashboard → Profile                              |
| System             | Tests the entire system as a whole      | Full order flow: login → browse → order → pay            |
| Acceptance         | Validates system against business needs | Client verifies order tracking works as expected         |

**Hint:** Know the goal and scope of each level.


### Sample Question:

Q: What is the main purpose of system testing? 
<br/>A. To test individual components 
<br/>B. To validate business requirements 
<br/>C. To test the complete integrated system 
<br/>D. To test user acceptance 
<br/>✅ Correct Answer: C

## 🔹 2.3 Test Types
Different types of testing target different risks.

| Test Type        | Focus                    | Real-World Example                                      |
|------------------|--------------------------|----------------------------------------------------------|
| Functional       | What the system does     | Does the “Place Order” button work?                      |
| Non-functional   | How the system behaves   | Can the app handle 10,000 users?                         |
| Structural       | Internal code structure  | Are all branches in the login logic tested?              |
| Change-related   | After changes            | Regression test after fixing payment bug                 |

**Hint:** Be able to match test types to scenarios.


### Sample Question:

Q: Which test type focuses on system performance under load? 
<br/>A. Functional 
<br/>B. Structural 
<br/>C. Non-functional 
<br/>D. Regression 
<br/>✅ Correct Answer: C

## 🔹 2.4 Maintenance Testing
Testing done after release to ensure continued quality.

| Type                | Purpose                          | Real-World Example                                         |
|---------------------|----------------------------------|------------------------------------------------------------|
| Regression Testing  | Ensure unchanged parts still work| After fixing a bug in checkout, test login and cart        |
| Confirmation Testing| Verify a specific fix            | Confirm that the payment bug is resolved                   |

**Hint:** Know the difference between regression and confirmation testing.


### Sample Question:

Q: What is the purpose of confirmation testing? 
<br/>A. To test new features 
<br/>B. To confirm a defect has been fixed 
<br/>C. To test system performance 
<br/>D. To test unrelated modules 
<br/>✅ Correct Answer: B

## ✅ Summary Table
| Topic               | Key Focus                          | Hint                                      |
|---------------------|------------------------------------|-------------------------------------------|
| Lifecycle Models    | How testing fits into development  | Know Waterfall, V-Model, Agile            |
| Test Levels         | Scope of testing                   | Match level to purpose                    |
| Test Types          | What is being tested               | Functional vs Non-functional vs Structural|
| Maintenance Testing | Post-release testing               | Regression vs Confirmation                |
