## Lab 13 – Windows Server Monitoring & Event Log Troubleshooting 

## Objectives
- Monitor Windows Server health.
- Use Event Viewer to investigate errors and warnings.
- Use Performance Monitor to monitor CPU, memory, disk, and network usage.
- Monitor critical Windows services.

## Documentation

1. Investigate Event Viewer

This is where we Learn where Windows records problems.

On DC01, open Server Manager → Tools → Event Viewer. , expand windows , then expand system
Expand Windows Logs.
Open System.
Look for:
Critical
Error
Warning
Lets Click one of the recent events.
<img width="1910" height="1624" alt="2" src="https://github.com/user-attachments/assets/03350425-44e7-41ae-8ada-ff359088fc49" />

2.  Create a Custom Troubleshooting View

Makes it easier for an administrator to find important problems.

Open Event Viewer.
Right-click Custom Views.
Select Create Custom View.
<img width="1898" height="1624" alt="3" src="https://github.com/user-attachments/assets/cf0dd2f6-e1e9-4a1e-9ebd-76e9f9152191" />

3. Check:
Critical
Error
Warning
Select Windows Logs.
<img width="1914" height="1572" alt="4" src="https://github.com/user-attachments/assets/11ce1674-f73c-4546-890f-92ceb009f2f6" />

4. Name it:
IT Support - Critical Events
<img width="1900" height="1614" alt="5" src="https://github.com/user-attachments/assets/e030ec3a-1eea-489c-a39d-e02d1eb4f2c5" />

5. Now we can see the custom critical events
<img width="1916" height="1688" alt="6" src="https://github.com/user-attachments/assets/e46451ee-0f1d-435e-8f62-3fcc435de553" />

6. Monitor Performance
Monitor DC01's system resources using the professional Windows monitoring tool.
Press Windows + R.
Enter:
perfmon
<img width="1722" height="1652" alt="7" src="https://github.com/user-attachments/assets/02b0adfb-c123-4a29-8d78-0d9b103d9510" />

7.  Select Performance Monitor.
Click the green + button to add counters
<img width="1716" height="1696" alt="8" src="https://github.com/user-attachments/assets/b9ad4ad0-ac66-40f0-9136-c067222a86c2" />

8. Add counters for:

Processor → % Processor Time and click ok
<img width="1720" height="1656" alt="9" src="https://github.com/user-attachments/assets/4403e407-5cdf-4f09-ac12-0773f4bc20f8" />

9. Screenshot shows CPU Performance Monitoring: Used Windows Performance Monitor (PerfMon) to monitor DC01 processor utilization in real time. The server averaged approximately 25% CPU utilization, with temporary spikes reaching approximately 71%, demonstrating how performance counters can be used to identify abnormal resource usage and potential server performance issues.
<img width="1726" height="1658" alt="10" src="https://github.com/user-attachments/assets/9c279ee6-a8ec-45ca-988d-377fd93ab364" />

10.  Added counters for memory 
shows Page Faults/sec — how often Windows needs memory pages that aren't immediately available in the working set.
Available Bytes — available physical memory.
Committed Bytes — memory Windows has committed for use.
Commit Limit — maximum amount of committed virtual memory available.
Write Copies/sec, Transition Faults/sec, and Cache Faults/sec — additional memory-management activity.
<img width="1722" height="1692" alt="11" src="https://github.com/user-attachments/assets/a3787675-96d0-469f-9630-bf9e1936e077" />
