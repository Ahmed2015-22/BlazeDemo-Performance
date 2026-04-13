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

## 💻 CLI Execution Command
To ensure accurate metrics and avoid UI resource consumption, all tests were executed via the command line:

```bash
jmeter -n -t BlazeDemo_TestPlan.jmx -l results/test_results.jtl -e -o results
