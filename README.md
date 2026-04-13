# 🚀 BlazeDemo Performance Testing 

## 📝 Project Overview
This repository contains a comprehensive Performance Testing suite for the [BlazeDemo](https://blazedemo.com/) web application. The testing focuses on the core user journey: Flight Reservation, Ticket Purchase, and Booking Confirmation.

## 🛠️ Tools & Technologies
* **Performance Testing Tool:** Apache JMeter
* **Test Execution:** Non-GUI (Command Line Interface)
* **Reporting:** JMeter HTML Dashboard Report
* **Version Control:** Git & GitHub

## ⚙️ Test Plan Architecture
The JMeter script is structured to simulate a realistic user flow using the following transactions:
1. **Reserve Request:** Navigating and selecting a flight.
2. **Purchase Request:** Filling in passenger details and submitting the payment form.
3. **Confirmation Request:** Verifying the booking success.

*Key JMeter Elements Used:* * `HTTP Request Defaults` & `HTTP Header Manager`
* `Constant Timer` to simulate realistic user think-time.
* `Check Status Code` & `Response Assertions` to validate successful transactions.

## 📊 Testing Scenarios & Execution
The application has an estimated capacity of **50 concurrent users**. Based on this baseline, three different testing strategies were executed:

| Test Strategy | Virtual Users (Threads) | Duration | Objective |
| :--- | :---: | :---: | :--- |
| **Load Testing** | 40 Users | Standard | Validate system behavior under expected peak load (below breaking point). |
| **Stress Testing**| 60 Users | Standard | Push the system beyond its capacity limit (50 VUs) to identify bottlenecks. |
| **Soak Testing** | 30 Users | 3 Minutes | Monitor system stability, resource utilization, and memory leaks over an extended period. |

### ⚡ Spike Testing (Ultimate Thread Group)
To simulate sudden surges in traffic while maintaining a normal base load, a Spike Test was configured using the **Ultimate Thread Group** plugin. The scenario includes two distinct traffic spikes:

| Schedule Record | Start Threads Count | Initial Delay (sec) | Startup Time (sec) | Hold Load For (sec) | Shutdown Time (sec) | Description |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **1. Base Load** | 10 | 0 | 5 | 180 | 5 | Continuous normal load running for the entire 3 minutes. |
| **2. Spike 1** | 40 | 30 | 1 | 10 | 1 | First surge starting after 30s (Total load reaches 50 VUs). |
| **3. Spike 2** | 60 | 100 | 1 | 15 | 1 | Heavier surge starting after 100s (Total load reaches 70 VUs). |

## 💻 CLI Execution Command
To ensure accurate metrics and avoid UI resource consumption, all tests were executed via the command line:

```bash
jmeter -n -t BlazeDemo_TestPlan.jmx -l result.csv
```
To generate HTML_Report
```bash
jmeter -n -t BlazeDemo_TestPlan.jmx -l results/test_results.jtl -e -o results
```
================================================================================

👨‍💻 Author
**Ahmed El-Sharkawi**  
*Junior Test Automation Engineer*

🔗 [LinkedIn Profile](https://www.linkedin.com/in/ahmed-el-sharkawi/)
🔗 [GitHub Profile](https://github.com/Ahmed2015-22)

