System Resource Monitor is a real-time desktop application built in Java using the Swing GUI toolkit and the JFreeChart charting library. The application continuously tracks CPU utilization, RAM consumption, and disk usage, displaying live line-charts and numeric indicators on an intuitive dark-themed dashboard. When any metric crosses a user-defined threshold, the system fires a desktop-style toast notification that appears in the bottom-right corner of the screen and auto-dismisses after four seconds — alerting the user without interrupting their workflow.

Project Objectives

1.	Monitor CPU, memory, and disk usage in real time using Java system APIs.
2.	Display live line-chart trends using the JFreeChart library.
3.	Alert the user via desktop toast notifications when usage exceeds configured thresholds.
4.	Allow users to configure alert thresholds and refresh intervals through a settings panel.
5.	List running processes with their CPU and RAM consumption.
6.	Maintain a persistent event log for later review.
7.	Demonstrate proper OOP design: service classes, UI separation, utility services
.  Package & File Structure (SRC)


    

The source tree follows Java package naming conventions under com.systemmonitor:


com.systemmonitor
├── Main.java                  — Entry point; splash then DashboardUI
├── cpu/
│   └── CpuService.java        — CPU load via OperatingSystemMXBean
├── memory/
│   └── MemoryService.java     — Total / used / free RAM
├── disk/
│   └── DiskService.java       — Disk space via java.io.File
├── process/
│   ├── ProcessInfo.java       — Data class (PID, name, CPU%, RAM%)
│   └── ProcessService.java    — Running processes via ProcessHandle
├── ui/
│   ├── DashboardUI.java       — Main frame, sidebar, live update timer
│   ├── AlertsUI.java          — Alert list + toast notification engine
│   ├── ProcessManagerUI.java  — Process table panel
│   ├── WelcomeScreen.java     — Splash window shown for 3 seconds
│   ├── IconLoader.java        — Loads PNG icons; fallback if missing
│   ├── UIConstants.java       — Color palette and font constants
│   └── UIUtils.java           — Shared component factory methods
├── utils/
│   ├── SettingsService.java   — Reads/writes settings.properties
│   ├── LoggerService.java     — Appends events to system_logs.txt
│   └── SystemUtils.java       — Misc system helpers
└── resources/
    └── icons/                 — PNG icon files (18 total)
