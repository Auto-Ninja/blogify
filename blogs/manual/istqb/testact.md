# 📘 Managing Test Activities
## 🧭 Overview of Key Activities
```Code
Managing Test Activities
├── Test Planning
├── Test Monitoring and Control
├── Risk Management
├── Configuration Management
└── Defect Management
```
### 🔹 5.1 Test Planning

<b>Purpose:</b> Define the scope, objectives, strategy, resources, and schedule for testing.
<b>Activities:</b>
- Identify test objectives and scope
- Define entry and exit criteria
- Assign roles and responsibilities
- Select tools and environments

<b>Real-World Example:</b> For a food delivery app:
<b>Entry:</b> All features implemented
<b>Exit:</b> 95% test coverage, no critical bugs
<b>Strategy:</b> Functional and regression testing

### Tools:
| Tool         | Type | Notes                                         |
|--------------|------|-----------------------------------------------|
| Azure DevOps | Paid | Integrated planning, pipelines, test cases    |
| TestRail     | Paid | Widely used for test planning and tracking    |
| TestLink     | Free | Open-source, basic planning features          |


### 🔹 5.2 Test Monitoring and Control
<b>Purpose:</b> Track progress and adjust plans as needed.

<b>Activities:</b>
- Monitor test execution and defect trends
- Compare actual vs planned metrics
- Take corrective actions (e.g., reallocate testers)

<b>Real-World Example:</b> If only 40% of tests are executed by mid-sprint, the test lead may shift resources or reduce scope.

<b>Tools:</b>

| Tool         | Type | Notes                                              |
|--------------|------|----------------------------------------------------|
| Jira + Xray  | Paid | Real-time dashboards, integrates with Agile boards |
| qTest        | Paid | Advanced analytics and reporting                   |
| Zephyr       | Paid | Popular Jira plugin for test tracking              |

### 🔹 5.3 Risk Management
<b>Purpose:</b> Identify and prioritize risks to guide testing effort.

<b>Activities:</b>
- Identify product and project risks
- Assess likelihood and impact
- Prioritize test cases accordingly

<b>Real-World Example:</b> If the payment module is complex and critical, it gets more test coverage than the user profile page.

<b>Tools:</b>

| Tool              | Type | Notes                                      |
|-------------------|------|--------------------------------------------|
| SpiraTest         | Paid | Built-in risk-based testing                |
| TestFLO           | Paid | Jira plugin with risk tracking             |
| Excel/Confluence  | Free | Manual risk registers and matrices         |

### 🔹 5.4 Configuration Management

<b>Purpose:</b> Control versions of test artifacts and environments.

<b>Activities:</b>
- Version control for test cases, data, and environments
- Track changes and dependencies
- Ensure consistency across releases

<b>Real-World Example:</b> Ensure test cases for version 2.1 aren’t mistakenly used on version 2.0.

<b>Tools:<b>

| Tool         | Type | Notes                                         |
|--------------|------|-----------------------------------------------|
| Git          | Free | Version control for test scripts and data     |
| Azure DevOps | Paid | Tracks builds, environments, and test artifacts |
| TestLink     | Free | Supports versioning of test cases             |

### 🔹 5.5 Defect Management

<b>Purpose:</b> Log, track, and resolve defects efficiently.
<b>Defect Lifecycle:</b>
- Detection – Tester finds a bug
- Logging – Bug is recorded in a tool
- Triage – Severity and priority assigned
- Fix – Developer resolves the issue
- Retest – Tester verifies the fix
- Closure – Bug is marked as closed

<b>Real-World Example:</b> A bug in the checkout flow is logged in Jira, fixed by a developer, and retested before closure.

#### Tools:

| Tool         | Type | Notes                                      |
|--------------|------|--------------------------------------------|
| Jira         | Paid | Most widely used for defect tracking       |
| Azure DevOps | Paid | Integrated bug tracking with pipelines     |
| Bugzilla     | Free | Open-source, customizable                  |
| MantisBT     | Free | Lightweight and easy to use                |

## 🔄 Sequence Diagram: Defect Management Lifecycle

```Code
User → Tester: Reports issue
Tester → Jira/Azure: Logs defect
Tool → Developer: Assigns defect
Developer → Tool: Updates status
Tester → Tool: Retests fix
Tool → Tester: Confirms resolution
Tester → Tool: Closes defect
```
## 🧠 Mind Map: Managing Test Activities
```Code
Managing Test Activities
├── Test Planning
│   ├── Objectives
│   ├── Entry/Exit Criteria
│   └── Resources
├── Monitoring & Control
│   ├── Metrics
│   └── Adjustments
├── Risk Management
│   ├── Identification
│   ├── Assessment
│   └── Prioritization
├── Configuration Management
│   ├── Versioning
│   └── Environment Tracking
└── Defect Management
    ├── Logging
    ├── Assignment
    ├── Retesting
    └── Closure
```

#### ✅ Sample Questions
Q1: What is the purpose of test planning? 
<br/>A. To execute tests 
<br/>B. To define strategy and schedule 
<br/>C. To log defects 
<br/>D. To monitor progress 
<br/>✅ Correct Answer: B

Q2: Which tool is most commonly used for defect tracking? 
<br/>A. Git 
<br/>B. Jira 
<br/>C. TestRail 
<br/>D. Zephyr 
<br/>✅ Correct 
<br/>Answer: B

Q3: What does configuration management help with? 
<br/>A. Writing test cases 
<br/>B. Controlling versions of test artifacts 
<br/>C. Designing test strategies 
<br/>D. Executing tests 
<br/>✅ Correct Answer: B

Q4: What is the goal of risk-based testing? 
<br/>A. To test all features equally 
<br/>B. To prioritize testing based on risk 
<br/>C. To reduce test coverage 
<br/>D. To avoid regression testing 
<br/>✅ Correct Answer: B

Q5: What is the first step in defect management? 
<br/>A. Fixing the defect 
<br/>B. Logging the defect 
<br/>C. Retesting the defect 
<br/>D. Closing the defect 
<br/>✅ Correct Answer: B