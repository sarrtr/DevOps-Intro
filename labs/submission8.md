# Lab 8 submission

## Task 1

For this task I used commands for Windows OS.

Top 3 most consuming applications for CPU:
![8.1]()

Top 3 most consuming applications for memory:
![8.2]()

Top 10 largest folders and top 3 largest files in C:\Windows:
![8.3]()

I/O usage:
![8.4]()
![8.5]()
![8.6]()

**What patterns do you observe in resource utilization?**

The largest amount of RAM is occupied by applications – Telegram, VS Code and Spotify, probably because they store a lot of data in memory for a quick response.

The CPU value shows the total CPU time spent by the process since it started. The high performance of audiodg (the Windows audio subsystem driver), Spotify, and browser (Yandex browser) indicate that these applications have been actively using the processor for a long time.

**How would you optimize resource usage based on your findings?**

If the disk space is running out I should pay attention to large folders (maybe I could free some space there) and also regularly clean the trash, temporary files, and unused programs.

## Task 2

URL: https://yandex.ru/pogoda/ru?win=740&lat=55.754238&lon=48.741293 - Yandex Weather.

Browser check configuration:
![8.7]()

Successful check results:
![8.8]()
![8.9]()

Alert settings:
![8.10]()

I choose these specific checks and thresholds because if these specific checks fail then the site lose its key functionality (automatic location detection, current temperature display) even if the server responds with the 200 code.

This monitoring setup help maintain website reliability because automatic checks are performed and they immediately signal failures. We can measure page load time and response time to actions. If it exceeds the thresholds, a warning is generated. When alerts are triggered we can receive notifications by e-mail, this accelerates reaction and recovery.
